{"title":"Create a User","weight":"20"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

To configure a create a user flow:

1. Click the **Create Flow** icon associated with creating a simple user.
    The API Orchestration user interface is displayed.

2. Select and pull the simpleusers flow-node onto the flow editor from the Models list. Note that the Start flow-node is automatically connected to the input of the simpleusers flow-node.

3. Name the flow-node: Create user

4. Select the create method.

5. Select **Parameters**.

6. Configure the **data** parameter. If **selector** is selected from the _selector_ drop-down menu, as you begin typing in the **data** parameter field, a drop-down menu of valid or previously used selector options is displayed. You may optionally choose a selector from the list, or continue typing to manually configure the parameter. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). For additional information on the Model flow-node and General flow-node configuration parameters, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

7. Select **Outputs**.

8. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

9. Select and pull a Set Context flow-node onto the flow editor from the Core list.

10. Name the flow-node: Set header location

11. Select **Parameters**.

12. Configure the **value** parameter. If **selector** is selected from the _selector_ drop-down menu, as you begin typing in the **value** parameter field, a drop-down menu of valid or previously used selector options is displayed. You may optionally choose a selector from the list, or continue typing to manually configure the parameter. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). For additional information on the Model flow-node and General flow-node configuration parameters, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

13. Select **Outputs**.

14. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

15. Connect the next output of the Create user flow-node to the input of the Set header location flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

16. Select and pull an HTTP flow-node onto the flow editor from the Core list.

17. Name the flow-node: Create succeeded

18. Select **Parameters**.

19. For the **status** parameter, select **number** and enter 201 in the field.

20. Leave the **body** parameter disabled.

21. Enable and configure the **headers** parameter. If **selector** is selected from the _selector_ drop-down menu, as you begin typing in the **headers** parameter field, a drop-down menu of valid or previously used selector options is displayed. You may optionally choose a selector from the list, or continue typing to manually configure the parameter. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). For additional information on the Model flow-node and General flow-node configuration parameters, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

22. Connect the next output of the Create user flow-node to the input of the Create succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

23. Connect the next output of the Set header location flow-node to the input of the Create succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). The completed flow is displayed.

    ![Create_01](/Images/appc/download/attachments/52298551/Create_01.png)
24. Click **Save**.

25. On the next screen, click **Proceed**. The server will be restarted and the Create a user flow will be saved and enabled.
