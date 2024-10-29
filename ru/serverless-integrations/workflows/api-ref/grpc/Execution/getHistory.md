---
editable: false
sourcePath: en/_api-ref-grpc/serverless/workflows/v1/workflows/api-ref/grpc/Execution/getHistory.md
---

# Workflows Service, gRPC: ExecutionService.GetHistory {#GetHistory}

Retrieves detailed history of specified Workflow execution.

## gRPC request

**rpc GetHistory ([GetExecutionHistoryRequest](#yandex.cloud.serverless.workflows.v1.GetExecutionHistoryRequest)) returns ([GetExecutionHistoryResponse](#yandex.cloud.serverless.workflows.v1.GetExecutionHistoryResponse))**

## GetExecutionHistoryRequest {#yandex.cloud.serverless.workflows.v1.GetExecutionHistoryRequest}

```json
{
  "executionId": "string"
}
```

#|
||Field | Description ||
|| executionId | **string**

Required field. ID of the Workflow execution. ||
|#

## GetExecutionHistoryResponse {#yandex.cloud.serverless.workflows.v1.GetExecutionHistoryResponse}

```json
{
  "execution": {
    "id": "string",
    "workflowId": "string",
    "status": "Status",
    "startedAt": "google.protobuf.Timestamp",
    "duration": "google.protobuf.Duration"
  },
  "entries": [
    {
      "id": "string",
      "title": "string",
      "description": "string",
      "startedAt": "google.protobuf.Timestamp",
      "duration": "google.protobuf.Duration",
      "input": {
        // Includes only one of the fields `inputJson`
        "inputJson": "string"
        // end of the list of possible fields
      },
      "output": {
        // Includes only one of the fields `outputJson`
        "outputJson": "string"
        // end of the list of possible fields
      },
      "error": {
        "message": "string",
        "errorCode": "string"
      },
      "status": "Status",
      "type": "string",
      "attempts": "int64",
      "lastError": {
        "message": "string",
        "errorCode": "string"
      }
    }
  ]
}
```

#|
||Field | Description ||
|| execution | **[ExecutionPreview](#yandex.cloud.serverless.workflows.v1.ExecutionPreview)**

Workflow execution details. ||
|| entries[] | **[HistoryEntry](#yandex.cloud.serverless.workflows.v1.HistoryEntry)**

Workflow execution detailed history items. ||
|#

## ExecutionPreview {#yandex.cloud.serverless.workflows.v1.ExecutionPreview}

#|
||Field | Description ||
|| id | **string**

ID of the Workflow execution. Generated at creation time. ||
|| workflowId | **string**

ID of the Workflow. ||
|| status | enum **Status**

Status of the Workflow execution

- `STATUS_UNSPECIFIED`
- `QUEUED`: Workflow execution is being queued.
- `RUNNING`: Workflow execution is running.
- `PAUSED`: Workflow execution is being paused.
- `STOPPED`: Workflow execution is stopped.
- `FAILED`: Workflow execution is failed.
- `FINISHED`: Workflow execution is finished. ||
|| startedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Start timestamp for the Workflow execution. ||
|| duration | **[google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration)**

Duration of the Workflow execution. ||
|#

## HistoryEntry {#yandex.cloud.serverless.workflows.v1.HistoryEntry}

#|
||Field | Description ||
|| id | **string**

ID of the Workflow step. ||
|| title | **string**

Title of the Workflow step. ||
|| description | **string**

Description of the Workflow step. ||
|| startedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Start timestamp for the Workflow step. ||
|| duration | **[google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration)**

Duration of the Workflow step. ||
|| input | **[HistoryEntryInput](#yandex.cloud.serverless.workflows.v1.HistoryEntryInput)**

Input data for the Workflow step. ||
|| output | **[HistoryEntryOutput](#yandex.cloud.serverless.workflows.v1.HistoryEntryOutput)**

Result of the Workflow step. ||
|| error | **[HistoryEntryError](#yandex.cloud.serverless.workflows.v1.HistoryEntryError)**

Error details, in case Workflow step failed. ||
|| status | enum **Status**

Status of the Workflow step.

- `STATUS_UNSPECIFIED`
- `SCHEDULED`: Step execution is being scheduled.
- `STARTED`: Step execution is started.
- `COMPLETED`: Step execution is completed.
- `FAILED`: Step execution is failed.
- `CANCEL_REQUESTED`: Step execution is requested to be cancelled.
- `CANCELLED`: Step execution is canceled. ||
|| type | **string**

Type of the Workflow step (for example, FunctionCall or HttpCall). ||
|| attempts | **int64**

Number of attempts (including all retries of unsuccessful attempts). Value "1" means there were no retries. ||
|| lastError | **[HistoryEntryError](#yandex.cloud.serverless.workflows.v1.HistoryEntryError)**

Last received error details in case of retries. ||
|#

## HistoryEntryInput {#yandex.cloud.serverless.workflows.v1.HistoryEntryInput}

#|
||Field | Description ||
|| inputJson | **string**

JSON input data for the Workflow step.

Includes only one of the fields `inputJson`. ||
|#

## HistoryEntryOutput {#yandex.cloud.serverless.workflows.v1.HistoryEntryOutput}

#|
||Field | Description ||
|| outputJson | **string**

JSON result for the Workflow step.

Includes only one of the fields `outputJson`. ||
|#

## HistoryEntryError {#yandex.cloud.serverless.workflows.v1.HistoryEntryError}

#|
||Field | Description ||
|| message | **string**

Error message of the Workflow step. ||
|| errorCode | **string**

Error code of the Workflow step. ||
|#