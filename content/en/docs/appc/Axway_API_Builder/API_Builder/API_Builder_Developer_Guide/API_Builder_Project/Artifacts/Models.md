{"title":"Models","weight":"10"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Introduction](#introduction)

* [Create a new model](#create-a-new-model)

* [Edit a model](#edit-a-model)

* [Composing a new model](#composing-a-new-model)

* [Generate endpoints](#generate-endpoints)

## Introduction

This guide covers the basics for creating Models. Models are a way of accessing data stored in either server memory or a backend service, such as [Mobile Backend Services](/docs/appc/Mobile_Backend_Services/) or a MySQL database, using a Connector. Models are accessed like standard REST objects using predefined endpoints that API Builder automatically generates. You can either create a model by defining your own schema, use an existing model defined by a connector, modify an existing model, or create a composite model by joining two or more models together.

To programmatically create Models, see the [API Builder.Model API reference](#!/api/Arrow.Model).

In the **Models** tab, you will see a list of models (by name), connector names, descriptions, and any joins to other models. This page allows you to also create new models, edit an existing model, and compose the model into a new model.

## Create a new model

Models can be created in many different ways but with the GUI, you don't necessarily need to get your hands dirty with writing out code.

To create a new model using the GUI:

1. Click the **\+ Model** button.

2. In the model window.

    ![new_model_%281%29](/Images/appc/download/attachments/49153275/new_model_%281%29.png)

    1. Enter the **Model name** (required).

    2. Select a **Connector** (required).

    3. Enter a **description** for the new model. While this is an optional field, we encourage you to provide a clear and concise description of what the model does.

    4. Click **Next** to start the process of creating a new model.

3. In the New Model page, you will see the name of the model you just created with an option to edit that name and the Connector you selected for it to use.

4. To add a new field, click the **\+ Field** button. In the model window,

    1. Enter the **Field** name (required).

    2. Select the **Type** for this new field.

    3. Enter a **Default** **value** (optional).

    4. Enter a **Description**.

    5. Check off the **Read-only** and/or the **Required** boxes.

    6. Click **Add field to model** to complete the addition of this new field.

5. Repeat step 4 as needed to add as many fields as necessary.

6. At this point, you can edit any field you created by clicking the **pencil icon** at the end of the field row.

7. If the field isn't needed, you can remove it by clicking on the trashcan icon at the end of the field row.

    There is no warning for deleting a field. Once you delete the field, you will not be prompted for a confirmation of the action.

8. Click the **Next >** button.

9. Optional: on the endpoint generation page, select the methods that will be automatically generated for the API endpoints. When you click **Next**, you are brought to the API generation page where you can optionally generate an API definition for your new model, and choose the method(s) that you wish to generate. To generate API endpoints:

    1. Select the methods that will be automatically generated for the API endpoints.

    2. You can change the singular and plural values for this new model. These values are used in the API documentation (e.g. "Create a user", or "Count users"), but these values are also used in the body of the API responses.

    3. If you are satisfied with your new field(s), click the **Save** button.

10. Also on this page, you can change the singular and plural values for this new model.

11. If you are satisfied with your new field(s), click the **Save** button.

    ![model_page](/Images/appc/download/attachments/49153275/model_page.png)

## Edit a model

To edit an existing model using the GUI:

1. Navigate to the **Models** tab.

2. Locate the model you wish to edit and click the **Tool** icon at the end of the row. A dialogue box will open.

    ![edit-compose-generate_model](/Images/appc/download/thumbnails/49153275/edit-compose-generate_model.png)
3. Click **Edit this model**. A dialogue window will open up and allow you to make changes to your selected model.

4. You can edit the model name by clicking the **Pencil** icon next to the model name.

5. Locate the field you wish to edit and click the **Pencil** icon at the end of its row.

6. Modify the **Field** name, **Type**, **Default** value, and/or **Description** fields as necessary. You can also toggle the Read-only and Required check boxes.

7. Once you are done modifying this field, click the Update field button.

8. Repeat steps 6-7 as necessary.

9. Click the **Next** button.

10. Modify any of the **API endpoints** and/or the **Singular** and **Plural** fields.

11. Click the **Save** button if you are satisfied with your changes.

## Composing a new model

To compose a new model using the GUI:

1. Click on the **Cog** icon at the end of the row for the model you wish to compose and select **Compose into new**.

2. Enter a model name (required) and a description.

    ![compose_model](/Images/appc/download/attachments/49153275/compose_model.png)
3. In the Composite Model page, you can edit the name of the composite and modify the fields (as needed). If you want to rename the composite, click the **Pencil** icon and fill in the fields of the Composite Model model window as necessary. Click Update when you have finished.

4. If you wish to modify the fields of this new composite, click the **Pencil** icon at the end of the row for the field in question.

5. Fill in the various fields and check the Read-only or Required check boxes as necessary. Click Update Field once you have finished.

6. When you are done making any modifications, click the Next button.

7. Enable or disable any auto-generated API endpoints as you see fit.

8. Modify the Singular and Plural fields as necessary.

9. Click Save to commit your new composite model.

## Generate endpoints

To generate endpoints, refer to [Manage Endpoints](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Endpoints/).
