---
editable: false
sourcePath: en/_api-ref-grpc/iot/devices/v1/api-ref/grpc/Device/listPasswords.md
---

# IoT Core Service, gRPC: DeviceService.ListPasswords {#ListPasswords}

Retrieves the list of passwords for the specified device.

## gRPC request

**rpc ListPasswords ([ListDevicePasswordsRequest](#yandex.cloud.iot.devices.v1.ListDevicePasswordsRequest)) returns ([ListDevicePasswordsResponse](#yandex.cloud.iot.devices.v1.ListDevicePasswordsResponse))**

## ListDevicePasswordsRequest {#yandex.cloud.iot.devices.v1.ListDevicePasswordsRequest}

```json
{
  "deviceId": "string"
}
```

#|
||Field | Description ||
|| deviceId | **string**

Required field. ID of the registry to list passwords in.

To get a registry ID make a [RegistryService.List](/docs/iot-core/api-ref/grpc/Registry/list#List) request. ||
|#

## ListDevicePasswordsResponse {#yandex.cloud.iot.devices.v1.ListDevicePasswordsResponse}

```json
{
  "passwords": [
    {
      "deviceId": "string",
      "id": "string",
      "createdAt": "google.protobuf.Timestamp"
    }
  ]
}
```

#|
||Field | Description ||
|| passwords[] | **[DevicePassword](#yandex.cloud.iot.devices.v1.DevicePassword)**

List of passwords for the specified device. ||
|#

## DevicePassword {#yandex.cloud.iot.devices.v1.DevicePassword}

A device password.

#|
||Field | Description ||
|| deviceId | **string**

ID of the device that the password belongs to. ||
|| id | **string**

ID of the password. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|#