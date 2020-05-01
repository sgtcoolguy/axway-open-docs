{"title":"Upsert a User","weight":"110"}

{{% alert title="❗️ API Builder 3.x is deprecated" color="danger" %}}Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

To configure an upsert (update or insert) a user flow:

1. Click the **Create Flow** icon associated with updating or inserting a simple user.
    The API Orchestration user interface is displayed.

2. Select and pull the simpleusers flow-node onto the flow editor from the Models list. Note that the Start flow-node is automatically connected to the input of the simpleusers flow-node.

3. Name the flow-node: Upsert a user

4. Select the upsert method.

5. Select **Parameters**.

6. Configure the **value** parameter. If **selector** is selected from the _selector_ drop-down menu, as you begin typing in the **value** parameter field, a drop-down menu of valid or previously used selector options is displayed. You may optionally choose a selector from the list, or continue typing to manually configure the parameter. For additional selector autocomplete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). For additional information on the Model flow-node and General flow-node configuration parameters, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

7. Select **Outputs**.

8. Configure the **update** output. As you begin typing in the **update** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

9. Configure the **upsert** output. As you begin typing in the **upsert** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

10. Select and pull a Set Context flow-node onto the flow editor from the Core list.

11. Name the flow-node: Set location

12. Select **Parameters**.

13. For the **value** parameter, select **selector** and select $.model.id from the selector options drop-down menu or continue typing to manually complete the selector configuration. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

14. Connect the insert output of the Upsert a user flow-node to the input of the Set location flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

15. Select and pull an HTTP flow-node onto the flow editor from the Core list.

16. Name the flow-node: Upsert succeeded

17. Select **Parameters**.

18. For the **status** parameter, select **number** and enter 204 in the field.

19. Leave the **body** and **headers** parameters disabled.

20. Connect the update output of the Upsert a user flow-node to the input of the Upsert succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

21. Select and pull an HTTP flow-node onto the flow editor from the Core list.

22. Name the flow-node: Insert succeeded

23. Select **Parameters**.

24. For the **status** parameter, select **number** and enter 404 in the field.

25. Leave the **body** parameter disabled.

26. Enable the **headers** parameter, select **selector**, and select $.headers from the selector options drop-down menu or continue typing to manually complete the selector configuration. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

27. Connect the insert output of the Upsert a user flow-node to the input of the Insert succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

28. Connect the next output of the Set location flow-node to the input of the Insert succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). The completed flow is displayed.

    ![Upsert](/Images/appc/download/attachments/52298583/Upsert.png)
29. Click **Save**.

30. On the next screen, click **Proceed**. The server will be restarted and the Upsert a user flow will be saved and enabled.
