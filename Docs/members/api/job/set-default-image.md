# Upload Image for specified job

[**Authentication Required**](link-to-authentication)

```URL
/members/api/job/set-default-image/{job_id}
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
<td>application/json</td>
</tr>
</table>

## Request Body
parameters Key | Format | Description
---|---|---
image | string | url of selected image


## Response


Http Code| Meaning|Response body
---|---|---
200|Ok|array of job images
404|Job not find, job_id is incorrect|
400|Request not correct, image url dont declared

**Response Content Type:** 
application/json

## Response Body
Selected Image url (relative)


## Example
Example of using this api in vue component

```javascript
function setAsDefault(image) {
      xhr(`members/api/job/set-default-image/${this.job.job_id}`, 'POST', {image}).then(r => {
        this.job.default_image = r;
      }).catch(r => console.log(r));
    }
```

