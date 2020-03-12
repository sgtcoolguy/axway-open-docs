{"title":"Find All Users","weight":"60"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

To configure a find all users flow:

1. Click the **Create Flow** icon associated with finding all simple users.
  The API Orchestration user interface is displayed.

2. Select and pull the simpleusers flow-node onto the flow editor from the Models list. Note that the Start flow-node is automatically connected to the input of the simpleusers flow-node.

3. Name the flow-node: Find all users

4. Select the findAll method.

5. Select **Outputs**.

6. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

7. Select and pull an HTTP flow-node onto the flow editor from the Core list.

8. Name the flow-node: Find succeeded

9. Select **Parameters**.

10. For the **status** parameter, select **number** and enter 200 in the field.

11. Enable the **body** parameter, select **selector**, and select $.models from the selector options drop-down menu or continue typing to manually complete the selector configuration. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

12. Leave the **headers** parameter disabled.

13. Connect the next output of the Find all users flow-node to the input of the Find succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). The completed flow is displayed.

  ![Find_all](/Images/appc/download/attachments/52298568/Find_all.png)
14. Click **Save**.

15. On the next screen, click **Proceed**. The server will be restarted and the Find all users flow will be saved and enabled.
