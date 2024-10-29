---
editable: false
sourcePath: en/_api-ref-grpc/k8s/v1/managed-kubernetes/api-ref/grpc/Cluster/listNodes.md
---

# Managed Services for Kubernetes API, gRPC: ClusterService.ListNodes {#ListNodes}

Lists cluster's nodes.

## gRPC request

**rpc ListNodes ([ListClusterNodesRequest](#yandex.cloud.k8s.v1.ListClusterNodesRequest)) returns ([ListClusterNodesResponse](#yandex.cloud.k8s.v1.ListClusterNodesResponse))**

## ListClusterNodesRequest {#yandex.cloud.k8s.v1.ListClusterNodesRequest}

```json
{
  "clusterId": "string",
  "pageSize": "int64",
  "pageToken": "string"
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the Kubernetes cluster to list nodes in.
To get the Kubernetes cluster ID use a [ClusterService.List](/docs/managed-kubernetes/managed-kubernetes/api-ref/grpc/Cluster/list#List) request. ||
|| pageSize | **int64**

The maximum number of results per page to return. If the number of available
results is larger than `pageSize`,
the service returns a [ListClusterNodesResponse.nextPageToken](#yandex.cloud.k8s.v1.ListClusterNodesResponse)
that can be used to get the next page of results in subsequent list requests.
Default value: 100. ||
|| pageToken | **string**

Page token. To get the next page of results, set `page_token` to the
[ListClusterNodeGroupsResponse.nextPageToken](/docs/managed-kubernetes/managed-kubernetes/api-ref/grpc/Cluster/listNodeGroups#yandex.cloud.k8s.v1.ListClusterNodeGroupsResponse) returned by a previous list request. ||
|#

## ListClusterNodesResponse {#yandex.cloud.k8s.v1.ListClusterNodesResponse}

```json
{
  "nodes": [
    {
      "status": "Status",
      "spec": {
        "resources": {
          "memory": "int64",
          "cores": "int64",
          "coreFraction": "int64",
          "gpus": "int64"
        },
        "disk": {
          "diskTypeId": "string",
          "diskSize": "int64"
        }
      },
      "cloudStatus": {
        "id": "string",
        "status": "string",
        "statusMessage": "string"
      },
      "kubernetesStatus": {
        "id": "string",
        "conditions": [
          {
            "type": "string",
            "status": "string",
            "message": "string",
            "lastHeartbeatTime": "google.protobuf.Timestamp",
            "lastTransitionTime": "google.protobuf.Timestamp"
          }
        ],
        "taints": [
          {
            "key": "string",
            "value": "string",
            "effect": "Effect"
          }
        ],
        "attachedVolumes": [
          {
            "driverName": "string",
            "volumeHandle": "string"
          }
        ]
      }
    }
  ],
  "nextPageToken": "string"
}
```

#|
||Field | Description ||
|| nodes[] | **[Node](#yandex.cloud.k8s.v1.Node)**

List of nodes for the specified Kubernetes cluster. ||
|| nextPageToken | **string**

This token allows you to get the next page of results for list requests. If the number of results
is larger than [ListClusterNodesRequest.pageSize](#yandex.cloud.k8s.v1.ListClusterNodesRequest), use
the `next_page_token` as the value
for the [ListClusterNodesRequest.pageToken](#yandex.cloud.k8s.v1.ListClusterNodesRequest) query parameter
in the next list request. Each subsequent list request will have its own
`next_page_token` to continue paging through the results. ||
|#

## Node {#yandex.cloud.k8s.v1.Node}

#|
||Field | Description ||
|| status | enum **Status**

Computed node status.

- `STATUS_UNSPECIFIED`
- `PROVISIONING`: Node instance is not yet created (e.g. in progress).
- `NOT_CONNECTED`: Node instance is created but not registered
(e.g. is still initializing).
- `NOT_READY`: Node has connected but is not ready for
workload (see conditions for details).
- `READY`: Node has connected and ready for workload.
- `MISSING`: Node is still registered but its instance
is deleted (this is our bug).
- `STOPPED`: Node is stopped
- `UNKNOWN`: Backend request to kubernetes api was unsuccessful. ||
|| spec | **[Spec](#yandex.cloud.k8s.v1.Node.Spec)**

Node specificaion. ||
|| cloudStatus | **[CloudStatus](#yandex.cloud.k8s.v1.Node.CloudStatus)**

Cloud instance status.
Not available in `MISSING` status. ||
|| kubernetesStatus | **[KubernetesStatus](#yandex.cloud.k8s.v1.Node.KubernetesStatus)**

Kubernetes node status.
Not available in `PROVISIONING` and `NOT_CONNECTED` states. ||
|#

## Spec {#yandex.cloud.k8s.v1.Node.Spec}

Node specification.

#|
||Field | Description ||
|| resources | **[ResourcesSpec](#yandex.cloud.k8s.v1.ResourcesSpec)**

Node group specified resources. ||
|| disk | **[DiskSpec](#yandex.cloud.k8s.v1.DiskSpec)**

Node group specified disk. ||
|#

## ResourcesSpec {#yandex.cloud.k8s.v1.ResourcesSpec}

#|
||Field | Description ||
|| memory | **int64**

Amount of memory available to the node, specified in bytes. ||
|| cores | **int64**

Number of cores available to the node. ||
|| coreFraction | **int64**

Baseline level of CPU performance with the possibility to burst performance above that baseline level.
This field sets baseline performance for each core. ||
|| gpus | **int64**

Number of GPUs available to the node. ||
|#

## DiskSpec {#yandex.cloud.k8s.v1.DiskSpec}

#|
||Field | Description ||
|| diskTypeId | **string**

ID of the disk type. ||
|| diskSize | **int64**

Size of the disk, specified in bytes. ||
|#

## CloudStatus {#yandex.cloud.k8s.v1.Node.CloudStatus}

Cloud instance info

#|
||Field | Description ||
|| id | **string**

Compute instance id ||
|| status | **string**

IG instance status ||
|| statusMessage | **string**

IG instance status message ||
|#

## KubernetesStatus {#yandex.cloud.k8s.v1.Node.KubernetesStatus}

Kubernetes node info

#|
||Field | Description ||
|| id | **string**

Node id (and instance name) ||
|| conditions[] | **[Condition](#yandex.cloud.k8s.v1.Condition)**

Conditions is an array of current observed node conditions.
More info: https://kubernetes.io/docs/concepts/nodes/node/#condition ||
|| taints[] | **[Taint](#yandex.cloud.k8s.v1.Taint)**

If specified, the node's taints. ||
|| attachedVolumes[] | **[AttachedVolume](#yandex.cloud.k8s.v1.AttachedVolume)**

List of volumes that are attached to the node. ||
|#

## Condition {#yandex.cloud.k8s.v1.Condition}

#|
||Field | Description ||
|| type | **string**

Type of node condition. ||
|| status | **string**

Status is the status of the condition. ||
|| message | **string**

Human-readable message indicating details about last transition. ||
|| lastHeartbeatTime | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Last time we got an update on a given condition. ||
|| lastTransitionTime | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Last time the condition transit from one status to another. ||
|#

## Taint {#yandex.cloud.k8s.v1.Taint}

#|
||Field | Description ||
|| key | **string**

The taint key to be applied to a node. ||
|| value | **string**

The taint value corresponding to the taint key. ||
|| effect | enum **Effect**

The effect of the taint on pods that do not tolerate the taint.

- `EFFECT_UNSPECIFIED`
- `NO_SCHEDULE`: Do not allow new pods to schedule onto the node unless they tolerate the taint,
but allow all pods submitted to Kubelet without going through the scheduler
to start, and allow all already-running pods to continue running.
- `PREFER_NO_SCHEDULE`: Like NO_SCHEDULE, but the scheduler tries not to schedule
new pods onto the node, rather than prohibiting new pods from scheduling
onto the node entirely. Enforced by the scheduler.
- `NO_EXECUTE`: Evict any already-running pods that do not tolerate the taint. ||
|#

## AttachedVolume {#yandex.cloud.k8s.v1.AttachedVolume}

AttachedVolume describes a volume attached to a node

#|
||Field | Description ||
|| driverName | **string**

Name of the driver which has attached the volume ||
|| volumeHandle | **string**

Volume handle (cloud disk id) ||
|#