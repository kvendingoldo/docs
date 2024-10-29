---
editable: false
sourcePath: en/_cli-ref/cli-ref/managed-services/compute/disk/relocate.md
---

# yc compute disk relocate

Relocate the specified disk to the zone

#### Command Usage

Syntax: 

`yc compute disk relocate <DISK-NAME>|<DISK-ID> [Flags...] [Global Flags...]`

#### Flags

| Flag | Description |
|----|----|
|`--id`|<b>`string`</b><br/>Disk id.|
|`--name`|<b>`string`</b><br/>Disk name.|
|`--async`|Display information about the operation in progress, without waiting for the operation to complete.|
|`--destination-zone-id`|<b>`string`</b><br/>The zone to relocate to.|
|`--disk-placement-group-id`|<b>`string`</b><br/>Placement group to move the disk to.|
|`--disk-placement-group-name`|<b>`string`</b><br/>Placement group to move the disk to.|
|`--disk-placement-group-partition`|<b>`int`</b><br/>Placement group partition. Used when a placement group is created with the partition strategy.|

#### Global Flags

| Flag | Description |
|----|----|
|`--profile`|<b>`string`</b><br/>Set the custom configuration file.|
|`--debug`|Debug logging.|
|`--debug-grpc`|Debug gRPC logging. Very verbose, used for debugging connection problems.|
|`--no-user-output`|Disable printing user intended output to stderr.|
|`--retry`|<b>`int`</b><br/>Enable gRPC retries. By default, retries are enabled with maximum 5 attempts.<br/>Pass 0 to disable retries. Pass any negative value for infinite retries.<br/>Even infinite retries are capped with 2 minutes timeout.|
|`--cloud-id`|<b>`string`</b><br/>Set the ID of the cloud to use.|
|`--folder-id`|<b>`string`</b><br/>Set the ID of the folder to use.|
|`--folder-name`|<b>`string`</b><br/>Set the name of the folder to use (will be resolved to id).|
|`--endpoint`|<b>`string`</b><br/>Set the Cloud API endpoint (host:port).|
|`--token`|<b>`string`</b><br/>Set the OAuth token to use.|
|`--impersonate-service-account-id`|<b>`string`</b><br/>Set the ID of the service account to impersonate.|
|`--no-browser`|Disable opening browser for authentication.|
|`--format`|<b>`string`</b><br/>Set the output format: text (default), yaml, json, json-rest.|
|`--jq`|<b>`string`</b><br/>Query to select values from the response using jq syntax|
|`-h`,`--help`|Display help for the command.|
