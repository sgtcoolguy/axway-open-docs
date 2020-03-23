{"title":"Delete All Users","weight":"30"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

To configure a delete all users flow:

1. Click the **Create Flow** icon associated with deleting all simple users.
    The API Orchestration user interface is displayed.

2. Select and pull the simpleusers flow-node onto the flow editor from the Models list. Note that the Start flow-node is automatically connected to the input of the simpleusers flow-node.

3. Name the flow-node: Delete all users

4. Select the deleteAll method.

5. Select **Outputs**.

6. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

7. Select and pull an HTTP flow-node onto the flow editor from the Core list.

8. Name the flow-node: Delete succeeded

9. Select **Parameters**.

10. For the **status** parameter, select **number** and enter 204 in the field.

11. Leave the **body** and **headers** parameters disabled.

12. Connect the next output of the Delete all users flow-node to the input of the Delete succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). The completed flow is displayed.

    ![Delete_all](/Images/appc/download/attachments/52298561/Delete_all.png)
13. Click **Save**.

14. On the next screen, click **Proceed**. The server will be restarted and the Delete all users flow will be saved and enabled.
