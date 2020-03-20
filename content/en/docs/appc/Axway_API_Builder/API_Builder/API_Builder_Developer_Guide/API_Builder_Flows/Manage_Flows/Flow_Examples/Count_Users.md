{"title":"Count Users","weight":"10"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

To configure a count users flow:

1. Click the **Create Flow** icon associated with counting simple users.
    The API Orchestration user interface is displayed.

2. Select and pull the simpleusers flow-node onto the flow editor from the Models list. Note that the Start flow-node is automatically connected to the input of the simpleusers flow-node.

3. Name the flow-node: Count users

4. Select the count method.

5. Select **Parameters**.

6. Enable all parameters and begin typing in the parameter fields for each parameter. If **selector** is selected from the _selector_ drop-down menu, as you begin typing in the **parameter** field, a drop-down menu of valid or previously used selector options is displayed. You may optionally choose a selector from the list, or continue typing to manually configure the parameter. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). For additional information on the Model flow-node and General flow-node configuration parameters, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

7. Select **Outputs**.

8. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

9. Select and pull an HTTP flow-node onto the flow editor from the Core list.

10. Name the flow-node: Count succeeded

11. Select **Parameters**.

12. For the **status** parameter, select **number** and enter 200 in the field.

13. Enable the **body** parameter, select **selector** and enter $.count in the field.

14. Leave the **headers** parameter disabled.

15. Connect the next output of the Count users flow-node to the input of the Count succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). The completed flow is displayed.

    ![Count_01](/Images/appc/download/attachments/52298548/Count_01.png)
16. Click **Save**.

17. On the next screen, click **Proceed**. The server will be restarted and the Count users flow will be saved and enabled.
