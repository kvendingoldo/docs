---
editable: false
sourcePath: en/_api-ref/video/v1/api-ref/Thumbnail/generateUploadURL.md
---

# Video API, REST: Thumbnail.GenerateUploadURL {#GenerateUploadURL}

Generate url for upload image.

## HTTP request

```
POST https://video.{{ api-host }}/video/v1/thumbnails/{thumbnailId}:generateUploadURL
```

## Path parameters

#|
||Field | Description ||
|| thumbnailId | **string**

Required field. ID of the thumbnail. ||
|#

## Response {#yandex.cloud.video.v1.GenerateThumbnailUploadURLResponse}

**HTTP Code: 200 - OK**

```json
{
  "uploadUrl": "string"
}
```

#|
||Field | Description ||
|| uploadUrl | **string**

Upload url. ||
|#