# MCP Workshop — Assignment Answers

### Question 1: What changed in the number of tools after adding `predict_both`? Did the original client need to change?

Initially, the MCP server provided 8 tools. After adding the `predict_both` function with the `@server.tool()` decorator, the server provided 9 tools.

The original client did not need to be modified to discover the new tool because MCP supports dynamic tool discovery. The client can retrieve the updated list of available tools from the server.

### Question 2: How many test patients had different predictions? Which model was correct?

The models disagreed on 8 out of 114 test patients.

The disagreement occurred at patient indices 3, 25, 48, 53, 76, 80, 99, and 102.

Logistic Regression was correct for patients 3, 25, 48, 76, 80, 99, and 102. KNN was correct for patient 53.

Therefore, Logistic Regression was correct in 7 of the 8 disagreements, while KNN was correct in 1.

### Question 3: Which model performed better, and why?

Logistic Regression performed better on the test dataset.

- Logistic Regression accuracy: 96.49%
- KNN accuracy: 91.23%
- Logistic Regression malignant recall: 92.86%
- KNN malignant recall: 90.48%

Logistic Regression achieved higher accuracy, precision, and recall. It also made the correct prediction in 7 of the 8 cases where the models disagreed.

Based on these results, Logistic Regression is the better-performing model for this test dataset.

### Question 4: Why is the triple-quoted docstring important for an MCP tool?

The triple-quoted docstring describes what the tool does. MCP clients and AI agents can use this description to understand the tool's purpose and decide when to call it.

For example, the `predict_both` docstring explains that the tool runs predictions using both models and reports whether they agree.

A clear docstring makes the tool easier to discover and use correctly.

### Question 5: Why is the audit log useful?

The audit log records information about MCP tool calls, including request IDs, tool names, and execution status.

It helps developers track which tools were called, verify successful execution, troubleshoot errors, and review the system's behavior.

In this workshop, the audit log confirmed that `get_sample_input` and `predict_both` completed successfully for the tested patients.