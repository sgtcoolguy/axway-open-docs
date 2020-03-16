{"title":"Find and Modify Users","weight":"70"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

To configure a find and modify users flow:

1. Click the **Create Flow** icon associated with finding and modifying simple users.
    The API Orchestration user interface is displayed.

2. Select and pull a Set Context flow-node onto the flow editor from the Core list. Note that the Start flow-node is automatically connected to the input of the Set Context flow-node.

3. Name the flow-node: Build args parameter (new)

4. Select **Parameters**.

5. For the **value** parameter, select **selector** and select $.params.new from the selector options drop-down menu or continue typing to manually complete the selector configuration. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

6. Select **Outputs**.

7. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

8. Select and pull a Set Context flow-node onto the flow editor from the Core list.

9. Name the flow-node: Build args parameter (upsert)

10. Select **Parameters**.

11. For the **value** parameter, select **selector** and select $.params.upsert from the selector options drop-down menu or continue typing to manually complete the selector configuration. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

12. Select **Outputs**.

13. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

14. Connect the next output of the Build args parameter (new) flow-node to the input of the Build args parameter (upsert) flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

15. Select and pull the simpleusers flow-node onto the flow editor from the Models list.

16. Name the flow-node: Find and modify users

17. Select the findAndModify method.

18. Select **Parameters**.

19. Configure the **data** parameter. If **selector** is selected from the _selector_ drop-down menu, as you begin typing in the **data** parameter field, a drop-down menu of valid or previously used selector options is displayed. You may optionally choose a selector from the list, or continue typing to manually configure the parameter. For additional selector auto-complete information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). For additional information on the Model flow-node and General flow-node configuration parameters, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

20. Enable the additional parameters and configure them according to the findAndModify parameters listed in [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

21. Select **Outputs**.

22. Configure the **next** output. As you begin typing in the **next** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

23. Configure the **notfound** output. As you begin typing in the **notfound** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter.

24. Connect the next output of the Build args parameter (upsert) to the input of the Find and modify users flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

25. Select and pull an HTTP flow-node onto the flow editor from the Core list.

26. Name the flow-node: Find and modify succeeded

27. Select **Parameters**.

28. For the **status** parameter, select **number** and enter 204 in the field.

29. Leave the **body** and **headers** parameters disabled.

30. Connect the next output of the Find and modify users flow-node to the input of the Find and modify succeeded flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

31. Select and pull an HTTP flow-node onto the flow editor from the Core list.

32. Name the flow-node: Users not found

33. Select **Parameters**.

34. For the **status** parameter, select **number** and enter 404 in the field.

35. Leave the **body** and **headers** parameters disabled.

36. Connect the notfound output of the Find and modify users flow-node to the input of the Users not found flow-node. For additional information on connecting flow-nodes in a flow, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/). The completed flow is displayed.

    ![Find_and_modify](/Images/appc/download/attachments/52298572/Find_and_modify.png)
37. Click **Save**.

38. On the next screen, click **Proceed**. The server will be restarted and the Find and modify users flow will be saved and enabled.
