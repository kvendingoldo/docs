---
editable: false
sourcePath: en/_api-ref-grpc/compute/v1/api-ref/grpc/Disk/create.md
---

# Compute Cloud API, gRPC: DiskService.Create {#Create}

Creates a disk in the specified folder.

You can create an empty disk or restore it from a snapshot or an image.
Method starts an asynchronous operation that can be cancelled while it is in progress.

## gRPC request

**rpc Create ([CreateDiskRequest](#yandex.cloud.compute.v1.CreateDiskRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## CreateDiskRequest {#yandex.cloud.compute.v1.CreateDiskRequest}

```json
{
  "folderId": "string",
  "name": "string",
  "description": "string",
  "labels": "string",
  "typeId": "string",
  "zoneId": "string",
  "size": "int64",
  // Includes only one of the fields `imageId`, `snapshotId`
  "imageId": "string",
  "snapshotId": "string",
  // end of the list of possible fields
  "blockSize": "int64",
  "diskPlacementPolicy": {
    "placementGroupId": "string",
    "placementGroupPartition": "int64"
  },
  "snapshotScheduleIds": [
    "string"
  ],
  "hardwareGeneration": {
    // Includes only one of the fields `legacyFeatures`, `generation2Features`
    "legacyFeatures": {
      "pciTopology": "PCITopology"
    },
    "generation2Features": "Generation2HardwareFeatures"
    // end of the list of possible fields
  },
  "kmsKeyId": "string"
}
```

#|
||Field | Description ||
|| folderId | **string**

Required field. ID of the folder to create a disk in.
To get the folder ID use a [yandex.cloud.resourcemanager.v1.FolderService.List](/docs/resource-manager/api-ref/grpc/Folder/list#List) request. ||
|| name | **string**

Name of the disk. ||
|| description | **string**

Description of the disk. ||
|| labels | **string**

Resource labels as `key:value` pairs. ||
|| typeId | **string**

ID of the disk type.
To get a list of available disk types use the [yandex.cloud.compute.v1.DiskTypeService.List](/docs/compute/api-ref/grpc/DiskType/list#List) request. ||
|| zoneId | **string**

Required field. ID of the availability zone where the disk resides.
To get a list of available zones use the [yandex.cloud.compute.v1.ZoneService.List](/docs/compute/api-ref/grpc/Zone/list#List) request. ||
|| size | **int64**

Required field. Size of the disk, specified in bytes.
If the disk was created from a image, this value should be more than the
[yandex.cloud.compute.v1.Image.minDiskSize](/docs/compute/api-ref/grpc/Image/get#yandex.cloud.compute.v1.Image) value. ||
|| imageId | **string**

ID of the image to create the disk from.

Includes only one of the fields `imageId`, `snapshotId`. ||
|| snapshotId | **string**

ID of the snapshot to restore the disk from.

Includes only one of the fields `imageId`, `snapshotId`. ||
|| blockSize | **int64**

Block size used for disk, specified in bytes. The default is 4096. ||
|| diskPlacementPolicy | **[DiskPlacementPolicy](#yandex.cloud.compute.v1.DiskPlacementPolicy)**

Placement policy configuration. ||
|| snapshotScheduleIds[] | **string**

List of IDs of the snapshot schedules to attach the disk to. ||
|| hardwareGeneration | **[HardwareGeneration](#yandex.cloud.compute.v1.HardwareGeneration)**

Specify the overrides to hardware_generation of a source disk, image or snapshot,
or to the default values if the source does not define it. ||
|| kmsKeyId | **string**

ID of KMS key for disk encryption. ||
|#

## DiskPlacementPolicy {#yandex.cloud.compute.v1.DiskPlacementPolicy}

#|
||Field | Description ||
|| placementGroupId | **string**

Placement group ID. ||
|| placementGroupPartition | **int64** ||
|#

## HardwareGeneration {#yandex.cloud.compute.v1.HardwareGeneration}

A set of features, specific to a particular Compute hardware generation.
They are not necessary supported by every host OS or distro, thus they are fixed to an image
and are applied to all instances created with it as their boot disk image.
These features significantly determine how the instance is created, thus cannot be changed after the fact.

#|
||Field | Description ||
|| legacyFeatures | **[LegacyHardwareFeatures](#yandex.cloud.compute.v1.LegacyHardwareFeatures)**

Includes only one of the fields `legacyFeatures`, `generation2Features`. ||
|| generation2Features | **[Generation2HardwareFeatures](#yandex.cloud.compute.v1.Generation2HardwareFeatures)**

Includes only one of the fields `legacyFeatures`, `generation2Features`. ||
|#

## LegacyHardwareFeatures {#yandex.cloud.compute.v1.LegacyHardwareFeatures}

A first hardware generation, by default compatible with all legacy images.
Allows switching to PCI_TOPOLOGY_V2 and back.

#|
||Field | Description ||
|| pciTopology | enum **PCITopology**

- `PCI_TOPOLOGY_UNSPECIFIED`
- `PCI_TOPOLOGY_V1`
- `PCI_TOPOLOGY_V2` ||
|#

## Generation2HardwareFeatures {#yandex.cloud.compute.v1.Generation2HardwareFeatures}

A second hardware generation, which by default assumes PCI_TOPOLOGY_V2
and UEFI boot (with UEFI related features).

#|
||Field | Description ||
|| Empty | > ||
|#

## operation.Operation {#yandex.cloud.operation.Operation}

```json
{
  "id": "string",
  "description": "string",
  "createdAt": "google.protobuf.Timestamp",
  "createdBy": "string",
  "modifiedAt": "google.protobuf.Timestamp",
  "done": "bool",
  "metadata": {
    "diskId": "string"
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "id": "string",
    "folderId": "string",
    "createdAt": "google.protobuf.Timestamp",
    "name": "string",
    "description": "string",
    "labels": "string",
    "typeId": "string",
    "zoneId": "string",
    "size": "int64",
    "blockSize": "int64",
    "productIds": [
      "string"
    ],
    "status": "Status",
    // Includes only one of the fields `sourceImageId`, `sourceSnapshotId`
    "sourceImageId": "string",
    "sourceSnapshotId": "string",
    // end of the list of possible fields
    "instanceIds": [
      "string"
    ],
    "diskPlacementPolicy": {
      "placementGroupId": "string",
      "placementGroupPartition": "int64"
    },
    "hardwareGeneration": {
      // Includes only one of the fields `legacyFeatures`, `generation2Features`
      "legacyFeatures": {
        "pciTopology": "PCITopology"
      },
      "generation2Features": "Generation2HardwareFeatures"
      // end of the list of possible fields
    },
    "kmsKey": {
      "keyId": "string",
      "versionId": "string"
    }
  }
  // end of the list of possible fields
}
```

An Operation resource. For more information, see [Operation](/docs/api-design-guide/concepts/operation).

#|
||Field | Description ||
|| id | **string**

ID of the operation. ||
|| description | **string**

Description of the operation. 0-256 characters long. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| createdBy | **string**

ID of the user or service account who initiated the operation. ||
|| modifiedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[CreateDiskMetadata](#yandex.cloud.compute.v1.CreateDiskMetadata)**

Service-specific metadata associated with the operation.
It typically contains the ID of the target resource that the operation is performed on.
Any method that returns a long-running operation should document the metadata type, if any. ||
|| error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**

The error result of the operation in case of failure or cancellation.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|| response | **[Disk](#yandex.cloud.compute.v1.Disk)**

The normal response of the operation in case of success.
If the original method returns no data on success, such as Delete,
the response is [google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty).
If the original method is the standard Create/Update,
the response should be the target resource of the operation.
Any method that returns a long-running operation should document the response type, if any.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|#

## CreateDiskMetadata {#yandex.cloud.compute.v1.CreateDiskMetadata}

#|
||Field | Description ||
|| diskId | **string**

ID of the disk that is being created. ||
|#

## Disk {#yandex.cloud.compute.v1.Disk}

A Disk resource. For more information, see [Disks](/docs/compute/concepts/disk).

#|
||Field | Description ||
|| id | **string**

ID of the disk. ||
|| folderId | **string**

ID of the folder that the disk belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)** ||
|| name | **string**

Name of the disk. 1-63 characters long. ||
|| description | **string**

Description of the disk. 0-256 characters long. ||
|| labels | **string**

Resource labels as `key:value` pairs. Maximum of 64 per resource. ||
|| typeId | **string**

ID of the disk type. ||
|| zoneId | **string**

ID of the availability zone where the disk resides. ||
|| size | **int64**

Size of the disk, specified in bytes. ||
|| blockSize | **int64**

Block size of the disk, specified in bytes. ||
|| productIds[] | **string**

License IDs that indicate which licenses are attached to this resource.
License IDs are used to calculate additional charges for the use of the virtual machine.

The correct license ID is generated by the platform. IDs are inherited by new resources created from this resource.

If you know the license IDs, specify them when you create the image.
For example, if you create a disk image using a third-party utility and load it into Object Storage, the license IDs will be lost.
You can specify them in the [yandex.cloud.compute.v1.ImageService.Create](/docs/compute/api-ref/grpc/Image/create#Create) request. ||
|| status | enum **Status**

Current status of the disk.

- `STATUS_UNSPECIFIED`
- `CREATING`: Disk is being created.
- `READY`: Disk is ready to use.
- `ERROR`: Disk encountered a problem and cannot operate.
- `DELETING`: Disk is being deleted. ||
|| sourceImageId | **string**

ID of the image that was used for disk creation.

Includes only one of the fields `sourceImageId`, `sourceSnapshotId`. ||
|| sourceSnapshotId | **string**

ID of the snapshot that was used for disk creation.

Includes only one of the fields `sourceImageId`, `sourceSnapshotId`. ||
|| instanceIds[] | **string**

Array of instances to which the disk is attached. ||
|| diskPlacementPolicy | **[DiskPlacementPolicy](#yandex.cloud.compute.v1.DiskPlacementPolicy2)**

Placement policy configuration. ||
|| hardwareGeneration | **[HardwareGeneration](#yandex.cloud.compute.v1.HardwareGeneration2)**

If specified, forces the same HardwareGeneration features to be applied to the instance
created using this disk as a boot one. Otherwise the current default will be used. ||
|| kmsKey | **[KMSKey](#yandex.cloud.compute.v1.KMSKey)**

Key encryption key info. ||
|#

## DiskPlacementPolicy {#yandex.cloud.compute.v1.DiskPlacementPolicy2}

#|
||Field | Description ||
|| placementGroupId | **string**

Placement group ID. ||
|| placementGroupPartition | **int64** ||
|#

## HardwareGeneration {#yandex.cloud.compute.v1.HardwareGeneration2}

A set of features, specific to a particular Compute hardware generation.
They are not necessary supported by every host OS or distro, thus they are fixed to an image
and are applied to all instances created with it as their boot disk image.
These features significantly determine how the instance is created, thus cannot be changed after the fact.

#|
||Field | Description ||
|| legacyFeatures | **[LegacyHardwareFeatures](#yandex.cloud.compute.v1.LegacyHardwareFeatures2)**

Includes only one of the fields `legacyFeatures`, `generation2Features`. ||
|| generation2Features | **[Generation2HardwareFeatures](#yandex.cloud.compute.v1.Generation2HardwareFeatures2)**

Includes only one of the fields `legacyFeatures`, `generation2Features`. ||
|#

## LegacyHardwareFeatures {#yandex.cloud.compute.v1.LegacyHardwareFeatures2}

A first hardware generation, by default compatible with all legacy images.
Allows switching to PCI_TOPOLOGY_V2 and back.

#|
||Field | Description ||
|| pciTopology | enum **PCITopology**

- `PCI_TOPOLOGY_UNSPECIFIED`
- `PCI_TOPOLOGY_V1`
- `PCI_TOPOLOGY_V2` ||
|#

## Generation2HardwareFeatures {#yandex.cloud.compute.v1.Generation2HardwareFeatures2}

A second hardware generation, which by default assumes PCI_TOPOLOGY_V2
and UEFI boot (with UEFI related features).

#|
||Field | Description ||
|| Empty | > ||
|#

## KMSKey {#yandex.cloud.compute.v1.KMSKey}

#|
||Field | Description ||
|| keyId | **string**

ID of KMS symmetric key ||
|| versionId | **string**

Version of KMS symmetric key ||
|#