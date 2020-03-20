{"title":"Models - Composite","weight":"20"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Create a composite model](#create-a-composite-model)

    * [Join object definition](#join-object-definition)

    * [Left join example](#left-join-example)

    * [Inner join example](#inner-join-example)

Composite models require the **appc.composite connector** to be installed. This comes by default with all API Builder Projects. If you are missing this connector you can learn how to install it [here](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Connectors/Add_a_Connector/).

## Create a composite model

Composite models allow you to create a single model that is composed of two or more models based on the same or different connectors. Composite models can be joined together via a common set of properties, such as primary keys or foreign keys, or they can have no properties in common at all. The power of composite models is that you can represent multiple data sources and entities as a single API endpoint, which is ideal for many mobile use cases.

To create a composite model, follow the same procedure when creating a regular model except the connector property must be set to appc.composite, each field in the definition object must specify the model property to indicate which model the field originates from, and the metadata property must define the join operation to combine the models or leave it undefined to perform no join operations.

The composite connector can either perform a left join or inner join:

* left join: all records from the main model are returned regardless if it found a match in the secondary models

* inner join: only records that match both models are returned

The composite connector can also perform either a one-to-one join or one-to-many join:

* one-to-one: only one record from the secondary model matches a record in the main model

* one-to-many: multiple records from the secondary model can match a record in the main model

To define the join operation, set the metadata property to either the left\_join key or inner\_join key, either of which takes an array of objects defining the join. Each object in the left\_join or inner\_join property defines the model to join (model property), a key to join (join\_properties property), and optionally if the join is one-to-one or one-to-many (multiple property).

### Join object definition

| Key | Type | Value |
| --- | --- | --- |
| model | String | Name of the model. For left joins, this is the secondary model you want to join with the main model. |
| join\_properties | Object | Collection of key-value pairs that determine the keys in each model to perform the join operation. The key is the property of the model defined in this object and the value is the property to join in another model (or the main model for left joins). |
| multiple | Boolean | Determines if the match is one-to-one (false) or one-to-many (true). The default value is false. |

### Left join example

The example below combines the employee and managers models to create the employee\_manager model. The models are joined based on a match between the managers model's employee\_id and the employee model's auto-generated id.

*models/employee\_manager.js*

```javascript
var Arrow = require('arrow');

var employee_manager = Arrow.createModel('employee_manager',{
    fields: {
        fname: {type:String, description:'First name', model:'employee'},
        manager: {type:String, description:'manager of employee',model:'managers'}
    },
    connector: 'appc.composite',
    metadata: {
        left_join: {
            model: 'managers',
            join_properties: {
                employee_id: 'id'
            }
        }
    }
});

module.exports = employee_manager;
```

*models/employee.js*

```javascript
var Arrow = require('arrow');

var employee = Arrow.Model.reduce('appc.mysql/employee','employee',{
    fields: {
        fname: {type:String, description:'First name', name:'first_name'}
    },
    connector: 'appc.mysql'
});

module.exports = employee;
```

*models/managers.js*

```javascript
var Arrow = require('arrow');

var managers = Arrow.Model.reduce('appc.mysql/employee_manager','managers',{
    fields: {
        employee_id: { type: Number, description: 'Employee ID' },
        manager: {type:String, name:'manager_name', description:'manager name'}
    },
    connector: 'appc.mysql'
});

module.exports = managers;
```

### Inner join example

The example below performs an inner join on the employee, employee\_manager, and employee\_habit models. Both the employee\_manager and employee\_habit properties will try to match the employee\_id property.

```javascript
var Arrow = require('arrow');

// create a model from a mysql table
var employee_composite = Arrow.createModel('employee_composite',{
    fields: {
        fname: {type: String, description: 'First name', model: 'employee'},
        manager: {type: String, description: 'Manager of employee', model: 'employee_manager'},
        habit: {type: String, description: 'Habit of employee', model: 'employee_habit'}
    },
    connector: 'appc.composite',
    metadata: {
        inner_join: [
            {
                model: 'employee_manager',
                join_properties: {
                    employee_id: 'id'
                }
            },
            {
                model:'employee_habit',
                multiple:true,
                join_properties:{
                    employee_id:'id'
                }
            }
        ]
    }
});

module.exports = employee_composite;
```
