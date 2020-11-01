# Upload Image for specified job

[**Authentication Required**](link-to-authentication)

```URL
/members/api/job/upload-image/{job_id}
```

## Url Params
parameter|Description
---|---
job_id| Identifier of specified job

## Request Specification
<table>
<tr>
<th>Method</th>
<td>POST</td>
</tr>
<tr>
<th>Content-Type</th>
<td>multipart/form-data</td>
</tr>
</table>

## Request Body
parameters Key | Format | Description
---|---|---
image | blob | file

## Response


|Http Code| Meaning|Response body|
|---|---|---|
|200|Ok|array of job images
|404|Job not find, job_id is incorrect||

**Response Content Type:** 
application/json

## Response body on success (200 HTTP Code)
Array of string contain relative url of job images 

## Example
Example of using this api in vue component

```javascript
function uploadJobImage(e){
      e.preventDefault();
      this.uploading = true;

      if (!this.image.blob)
        return false;

      const fd = new FormData();
      fd.append('image', this.image.blob, 'image.png');

      xhr(`members/api/job/upload-image/${this.job.job_id}`, 'POST', fd, true).then(r => {
        this.job.images = r;
        this.image = null;
        message('تصویر با موفقیت بارگذاری شد');
      }).finally(() => {
        this.uploading = false;
      });
    }
```

