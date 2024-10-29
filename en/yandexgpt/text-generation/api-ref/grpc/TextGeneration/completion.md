---
editable: false
sourcePath: en/_api-ref-grpc/ai/foundation_models/v1/text_generation/text-generation/api-ref/grpc/TextGeneration/completion.md
---

# Foundation Models Text Generation API, gRPC: TextGenerationService.Completion {#Completion}

A method for generating text completions in [synchronous mode](/docs/foundation-models/concepts/#working-mode).

## gRPC request

**rpc Completion ([CompletionRequest](#yandex.cloud.ai.foundation_models.v1.CompletionRequest)) returns (stream [CompletionResponse](#yandex.cloud.ai.foundation_models.v1.CompletionResponse))**

## CompletionRequest {#yandex.cloud.ai.foundation_models.v1.CompletionRequest}

```json
{
  "modelUri": "string",
  "completionOptions": {
    "stream": "bool",
    "temperature": "google.protobuf.DoubleValue",
    "maxTokens": "google.protobuf.Int64Value"
  },
  "messages": [
    {
      "role": "string",
      // Includes only one of the fields `text`, `toolCallList`, `toolResultList`
      "text": "string",
      "toolCallList": {
        "toolCalls": [
          {
            // Includes only one of the fields `functionCall`
            "functionCall": {
              "name": "string",
              "arguments": "google.protobuf.Struct"
            }
            // end of the list of possible fields
          }
        ]
      },
      "toolResultList": {
        "toolResults": [
          {
            // Includes only one of the fields `functionResult`
            "functionResult": {
              "name": "string",
              // Includes only one of the fields `content`
              "content": "string"
              // end of the list of possible fields
            }
            // end of the list of possible fields
          }
        ]
      }
      // end of the list of possible fields
    }
  ],
  "tools": [
    {
      // Includes only one of the fields `function`
      "function": {
        "name": "string",
        "description": "string",
        "parameters": "google.protobuf.Struct"
      }
      // end of the list of possible fields
    }
  ]
}
```

Request for the service to generate text completion.

#|
||Field | Description ||
|| modelUri | **string**

The [ID of the model](/docs/foundation-models/concepts/yandexgpt/models) to be used for completion generation. ||
|| completionOptions | **[CompletionOptions](#yandex.cloud.ai.foundation_models.v1.CompletionOptions)**

Configuration options for completion generation. ||
|| messages[] | **[Message](#yandex.cloud.ai.foundation_models.v1.Message)**

A list of messages representing the context for the completion model. ||
|| tools[] | **[Tool](#yandex.cloud.ai.foundation_models.v1.Tool)**

List of tools that are available for the model to invoke during the completion generation.
Note: This parameter is not yet supported and will be ignored if provided. ||
|#

## CompletionOptions {#yandex.cloud.ai.foundation_models.v1.CompletionOptions}

Defines the options for completion generation.

#|
||Field | Description ||
|| stream | **bool**

Enables streaming of partially generated text. ||
|| temperature | **[google.protobuf.DoubleValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/double-value)**

Affects creativity and randomness of responses. Should be a double number between 0 (inclusive) and 1 (inclusive).
Lower values produce more straightforward responses while higher values lead to increased creativity and randomness.
Default temperature: 0.3 ||
|| maxTokens | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The limit on the number of tokens used for single completion generation.
Must be greater than zero. This maximum allowed parameter value may depend on the model being used. ||
|#

## Message {#yandex.cloud.ai.foundation_models.v1.Message}

A message object representing a wrapper over the inputs and outputs of the completion model.

#|
||Field | Description ||
|| role | **string**

The ID of the message sender. Supported roles:
* `system`: Special role used to define the behaviour of the completion model.
* `assistant`: A role used by the model to generate responses.
* `user`: A role used by the user to describe requests to the model. ||
|| text | **string**

Textual content of the message.

Includes only one of the fields `text`, `toolCallList`, `toolResultList`.

Message content. ||
|| toolCallList | **[ToolCallList](#yandex.cloud.ai.foundation_models.v1.ToolCallList)**

List of tool calls made by the model as part of the response generation.

Includes only one of the fields `text`, `toolCallList`, `toolResultList`.

Message content. ||
|| toolResultList | **[ToolResultList](#yandex.cloud.ai.foundation_models.v1.ToolResultList)**

List of tool results returned from external tools that were invoked by the model.

Includes only one of the fields `text`, `toolCallList`, `toolResultList`.

Message content. ||
|#

## ToolCallList {#yandex.cloud.ai.foundation_models.v1.ToolCallList}

Represents a list of tool calls.

#|
||Field | Description ||
|| toolCalls[] | **[ToolCall](#yandex.cloud.ai.foundation_models.v1.ToolCall)**

A list of tool calls to be executed. ||
|#

## ToolCall {#yandex.cloud.ai.foundation_models.v1.ToolCall}

Represents a call to a tool.

#|
||Field | Description ||
|| functionCall | **[FunctionCall](#yandex.cloud.ai.foundation_models.v1.FunctionCall)**

Represents a call to a function.

Includes only one of the fields `functionCall`. ||
|#

## FunctionCall {#yandex.cloud.ai.foundation_models.v1.FunctionCall}

Represents the invocation of a function with specific arguments.

#|
||Field | Description ||
|| name | **string**

The name of the function being called. ||
|| arguments | **[google.protobuf.Struct](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/struct)**

The structured arguments passed to the function.
These arguments must adhere to the JSON Schema defined in the corresponding function's parameters. ||
|#

## ToolResultList {#yandex.cloud.ai.foundation_models.v1.ToolResultList}

Represents a list of tool results.

#|
||Field | Description ||
|| toolResults[] | **[ToolResult](#yandex.cloud.ai.foundation_models.v1.ToolResult)**

A list of tool results. ||
|#

## ToolResult {#yandex.cloud.ai.foundation_models.v1.ToolResult}

Represents the result of a tool call.

#|
||Field | Description ||
|| functionResult | **[FunctionResult](#yandex.cloud.ai.foundation_models.v1.FunctionResult)**

Represents the result of a function call.

Includes only one of the fields `functionResult`. ||
|#

## FunctionResult {#yandex.cloud.ai.foundation_models.v1.FunctionResult}

Represents the result of a function call.

#|
||Field | Description ||
|| name | **string**

The name of the function that was executed. ||
|| content | **string**

The result of the function call, represented as a string.
This field can be used to store the output of the function.

Includes only one of the fields `content`. ||
|#

## Tool {#yandex.cloud.ai.foundation_models.v1.Tool}

Represents a tool that can be invoked during completion generation.

#|
||Field | Description ||
|| function | **[FunctionTool](#yandex.cloud.ai.foundation_models.v1.FunctionTool)**

Represents a function that can be called.

Includes only one of the fields `function`. ||
|#

## FunctionTool {#yandex.cloud.ai.foundation_models.v1.FunctionTool}

Represents a function tool that can be invoked during completion generation.

#|
||Field | Description ||
|| name | **string**

The name of the function. ||
|| description | **string**

A description of the function's purpose or behavior. ||
|| parameters | **[google.protobuf.Struct](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/struct)**

A JSON Schema that defines the expected parameters for the function.
The schema should describe the required fields, their types, and any constraints or default values. ||
|#

## CompletionResponse {#yandex.cloud.ai.foundation_models.v1.CompletionResponse}

```json
{
  "alternatives": [
    {
      "message": {
        "role": "string",
        // Includes only one of the fields `text`, `toolCallList`, `toolResultList`
        "text": "string",
        "toolCallList": {
          "toolCalls": [
            {
              // Includes only one of the fields `functionCall`
              "functionCall": {
                "name": "string",
                "arguments": "google.protobuf.Struct"
              }
              // end of the list of possible fields
            }
          ]
        },
        "toolResultList": {
          "toolResults": [
            {
              // Includes only one of the fields `functionResult`
              "functionResult": {
                "name": "string",
                // Includes only one of the fields `content`
                "content": "string"
                // end of the list of possible fields
              }
              // end of the list of possible fields
            }
          ]
        }
        // end of the list of possible fields
      },
      "status": "AlternativeStatus"
    }
  ],
  "usage": {
    "inputTextTokens": "int64",
    "completionTokens": "int64",
    "totalTokens": "int64"
  },
  "modelVersion": "string"
}
```

Response containing generated text completions.

#|
||Field | Description ||
|| alternatives[] | **[Alternative](#yandex.cloud.ai.foundation_models.v1.Alternative)**

A list of generated completion alternatives. ||
|| usage | **[ContentUsage](#yandex.cloud.ai.foundation_models.v1.ContentUsage)**

A set of statistics describing the number of content tokens used by the completion model. ||
|| modelVersion | **string**

The model version changes with each new releases. ||
|#

## Alternative {#yandex.cloud.ai.foundation_models.v1.Alternative}

Represents a generated completion alternative, including its content and generation status.

#|
||Field | Description ||
|| message | **[Message](#yandex.cloud.ai.foundation_models.v1.Message2)**

A message containing the content of the alternative. ||
|| status | enum **AlternativeStatus**

The generation status of the alternative

- `ALTERNATIVE_STATUS_UNSPECIFIED`: Unspecified generation status.
- `ALTERNATIVE_STATUS_PARTIAL`: Partially generated alternative.
- `ALTERNATIVE_STATUS_TRUNCATED_FINAL`: Incomplete final alternative resulting from reaching the maximum allowed number of tokens.
- `ALTERNATIVE_STATUS_FINAL`: Final alternative generated without running into any limits.
- `ALTERNATIVE_STATUS_CONTENT_FILTER`: Generation was stopped due to the discovery of potentially sensitive content in the prompt or generated response.
To fix, modify the prompt and restart generation.
- `ALTERNATIVE_STATUS_TOOL_CALLS`: Tools were invoked during the completion generation. ||
|#

## Message {#yandex.cloud.ai.foundation_models.v1.Message2}

A message object representing a wrapper over the inputs and outputs of the completion model.

#|
||Field | Description ||
|| role | **string**

The ID of the message sender. Supported roles:
* `system`: Special role used to define the behaviour of the completion model.
* `assistant`: A role used by the model to generate responses.
* `user`: A role used by the user to describe requests to the model. ||
|| text | **string**

Textual content of the message.

Includes only one of the fields `text`, `toolCallList`, `toolResultList`.

Message content. ||
|| toolCallList | **[ToolCallList](#yandex.cloud.ai.foundation_models.v1.ToolCallList2)**

List of tool calls made by the model as part of the response generation.

Includes only one of the fields `text`, `toolCallList`, `toolResultList`.

Message content. ||
|| toolResultList | **[ToolResultList](#yandex.cloud.ai.foundation_models.v1.ToolResultList2)**

List of tool results returned from external tools that were invoked by the model.

Includes only one of the fields `text`, `toolCallList`, `toolResultList`.

Message content. ||
|#

## ToolCallList {#yandex.cloud.ai.foundation_models.v1.ToolCallList2}

Represents a list of tool calls.

#|
||Field | Description ||
|| toolCalls[] | **[ToolCall](#yandex.cloud.ai.foundation_models.v1.ToolCall2)**

A list of tool calls to be executed. ||
|#

## ToolCall {#yandex.cloud.ai.foundation_models.v1.ToolCall2}

Represents a call to a tool.

#|
||Field | Description ||
|| functionCall | **[FunctionCall](#yandex.cloud.ai.foundation_models.v1.FunctionCall2)**

Represents a call to a function.

Includes only one of the fields `functionCall`. ||
|#

## FunctionCall {#yandex.cloud.ai.foundation_models.v1.FunctionCall2}

Represents the invocation of a function with specific arguments.

#|
||Field | Description ||
|| name | **string**

The name of the function being called. ||
|| arguments | **[google.protobuf.Struct](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/struct)**

The structured arguments passed to the function.
These arguments must adhere to the JSON Schema defined in the corresponding function's parameters. ||
|#

## ToolResultList {#yandex.cloud.ai.foundation_models.v1.ToolResultList2}

Represents a list of tool results.

#|
||Field | Description ||
|| toolResults[] | **[ToolResult](#yandex.cloud.ai.foundation_models.v1.ToolResult2)**

A list of tool results. ||
|#

## ToolResult {#yandex.cloud.ai.foundation_models.v1.ToolResult2}

Represents the result of a tool call.

#|
||Field | Description ||
|| functionResult | **[FunctionResult](#yandex.cloud.ai.foundation_models.v1.FunctionResult2)**

Represents the result of a function call.

Includes only one of the fields `functionResult`. ||
|#

## FunctionResult {#yandex.cloud.ai.foundation_models.v1.FunctionResult2}

Represents the result of a function call.

#|
||Field | Description ||
|| name | **string**

The name of the function that was executed. ||
|| content | **string**

The result of the function call, represented as a string.
This field can be used to store the output of the function.

Includes only one of the fields `content`. ||
|#

## ContentUsage {#yandex.cloud.ai.foundation_models.v1.ContentUsage}

An object representing the number of content [tokens](/docs/foundation-models/concepts/yandexgpt/tokens) used by the completion model.

#|
||Field | Description ||
|| inputTextTokens | **int64**

The number of tokens in the textual part of the model input. ||
|| completionTokens | **int64**

The total number of tokens in the generated completions. ||
|| totalTokens | **int64**

The total number of tokens, including all input tokens and all generated tokens. ||
|#