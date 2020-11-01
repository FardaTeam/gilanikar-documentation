# Upload Image for specified job

[**Authentication Required**](link-to-authentication)

```URL
/members/api/job/delete-images/{job_id}
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
images | string[] | array of selected image url


## Response


Http Code| Meaning|Response body
---|---|---
200|Ok|array of job images
404|Job not find, job_id is incorrect|
400|Request not correct, image url dont declared

**Response Content Type:** 
application/json

## Response Body
Json Object with following structure 

**images** : array of job images url (relative)

**default_image** : url of deleted image. it change if user remove default image


## Example
Example of using this api in vue component

```javascript
function deleteImage(image) {
               xhr(`members/api/job/delete-images/${this.job.job_id}`, 'POST', {images: [image]}).then(r => {
                 this.job.images = r.images;
                 this.job.default_image = r.default_image;
               }).catch(r => console.log(r));
             }
```

