---
editable: false
sourcePath: en/_api-ref-grpc/video/v1/api-ref/grpc/Video/get.md
---

# Video API, gRPC: VideoService.Get {#Get}

Returns the specific video.

## gRPC request

**rpc Get ([GetVideoRequest](#yandex.cloud.video.v1.GetVideoRequest)) returns ([Video](#yandex.cloud.video.v1.Video))**

## GetVideoRequest {#yandex.cloud.video.v1.GetVideoRequest}

```json
{
  "videoId": "string"
}
```

#|
||Field | Description ||
|| videoId | **string**

ID of the video. ||
|#

## Video {#yandex.cloud.video.v1.Video}

```json
{
  "id": "string",
  "channelId": "string",
  "title": "string",
  "description": "string",
  "thumbnailId": "string",
  "status": "VideoStatus",
  "duration": "google.protobuf.Duration",
  "visibilityStatus": "VisibilityStatus",
  // Includes only one of the fields `tusd`
  "tusd": {
    "url": "string"
  },
  // end of the list of possible fields
  // Includes only one of the fields `publicAccess`, `authSystemAccess`
  "publicAccess": "VideoPublicAccessRights",
  "authSystemAccess": "VideoAuthSystemAccessRights",
  // end of the list of possible fields
  "createdAt": "google.protobuf.Timestamp",
  "updatedAt": "google.protobuf.Timestamp",
  "labels": "string"
}
```

#|
||Field | Description ||
|| id | **string**

ID of the video. ||
|| channelId | **string**

ID of the channel where the video was created. ||
|| title | **string**

Video title. ||
|| description | **string**

Video description. ||
|| thumbnailId | **string**

ID of the thumbnail. ||
|| status | enum **VideoStatus**

Video status.

- `VIDEO_STATUS_UNSPECIFIED`: Video status unspecified.
- `WAIT_UPLOADING`: Waiting for the whole number of bytes to be loaded.
- `PROCESSING`: Video processing.
- `READY`: Video is ready, processing is completed.
- `ERROR`: An error occurred during video processing. ||
|| duration | **[google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration)**

Video duration. Optional, may be empty until the transcoding result is ready. ||
|| visibilityStatus | enum **VisibilityStatus**

Video visibility status.

- `VISIBILITY_STATUS_UNSPECIFIED`: Visibility status unspecified.
- `PUBLISHED`: Video is published and available for viewing.
- `UNPUBLISHED`: Video is unpublished, only admin can watch. ||
|| tusd | **[VideoTUSDSource](#yandex.cloud.video.v1.VideoTUSDSource)**

Upload video using the tus protocol.

Includes only one of the fields `tusd`.

Source type. ||
|| publicAccess | **[VideoPublicAccessRights](#yandex.cloud.video.v1.VideoPublicAccessRights)**

Video is available to everyone.

Includes only one of the fields `publicAccess`, `authSystemAccess`.

Video access rights. ||
|| authSystemAccess | **[VideoAuthSystemAccessRights](#yandex.cloud.video.v1.VideoAuthSystemAccessRights)**

Checking access rights using the authorization system.

Includes only one of the fields `publicAccess`, `authSystemAccess`.

Video access rights. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time when video was created. ||
|| updatedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time of last video update. ||
|| labels | **string**

Custom labels as `` key:value `` pairs. Maximum 64 per resource. ||
|#

## VideoTUSDSource {#yandex.cloud.video.v1.VideoTUSDSource}

#|
||Field | Description ||
|| url | **string**

URL for uploading video via the tus protocol. ||
|#

## VideoPublicAccessRights {#yandex.cloud.video.v1.VideoPublicAccessRights}

#|
||Field | Description ||
|| Empty | > ||
|#

## VideoAuthSystemAccessRights {#yandex.cloud.video.v1.VideoAuthSystemAccessRights}

#|
||Field | Description ||
|| Empty | > ||
|#