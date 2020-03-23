{"title":"Find a User by ID","weight":"80"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

To configure a find a user by ID flow:

1. Click the **Create Flow** icon associated with finding a simple user using their ID.
    The API Orchestration user interface is displayed.

2. Select and pull the simpleusers flow-node onto the flow editor from the Models list. Note that the Start flow-node is automatically connected to the input of the simpleusers flow-node.

3. Name the flow-node: Find a user by ID

4. Select the findByID method.

5. Select **Parameters**.

6. Configure the **id** parameter. If **selector** is selected from the _selector_ drop-down menu, as you begin typing in the **id** parameter field, a drop-down menu of valid or previously used selector options is displayed. You may optionally choose a selector from the list, or continue typing to manually configure the parameter. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). For additional information on the Model flow-node and General flow-node configuration parameters, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

7. Select **Outputs**.

8. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

9. Configure the **notfound** output. As you begin typing in the **notfound** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

10. Select and pull an HTTP flow-node onto the flow editor from the Core list.

11. Name the flow-node: Find succeeded

12. Select **Parameters**.

13. For the **status** parameter, select **number** and enter 200 in the field.

14. Enable the **body** parameter, select **selector**, and select $.model from the selector options drop-down menu or continue typing to manually complete the selector configuration. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

15. Leave the **headers** parameter disabled.

16. Connect the next output of the Find a user by ID flow-node to the input of the Find succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

17. Select and pull an HTTP flow-node onto the flow editor from the Core list.

18. Name the flow-node: User not found

19. Select **Parameters**.

20. For the **status** parameter, select **number** and enter 404 in the field.

21. Leave the **body** and **headers** parameters disabled.

22. Connect the notfound output of the Find a user by ID flow-node to the input of the User not found flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). The completed flow is displayed.

    ![Find_by_ID](/Images/appc/download/attachments/52298576/Find_by_ID.png)
23. Click **Save**.

24. On the next screen, click **Proceed**. The server will be restarted and the Find a user by ID flow will be saved and enabled.
