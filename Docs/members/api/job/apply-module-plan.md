# Apply a module with specified plan

[**Authentication Required**](link-to-authentication)

```URL
/members/api/job/apply-module-plan
```

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
job_id | bigInt | job identifier
module | string | key of module
plain_id | string | UUID of plan, unique identifier

***all params are required**

## Response


Http Code| Meaning|Response body
---|---|---
200|Ok|return job_module_key to track up request
400|structure error|params aren't send
404|source not found| where job or module plan not found
409|validation error| JSON object (key value pair) validation errors
500|Server Internal Error|

**Response Content Type:** 
application/json




## Example
Example of using this api in vue component

```javascript
function applyPlan() {
               this.errors = [];
         
               if (!this.selectedJob || !this.selectedJob.job_id || !this.module || !this.selectedPlan || !this.selectedPlan.plan_id) {
                 this.errors.push('لطفا فرم را تکمیل فرمایید')
                 return 0;
               }
               xhr('members/api/job/apply-module-plan', 'post', {
                 'job_id': this.selectedJob.job_id,
                 'module': this.module,
                 'plan_id': this.selectedPlan.plan_id
               }).then(r => {
                 if (r) {
                   message(`درخواست شما با موفقیت ثبت شد، کد پیگیری شما \n\n ${r}`);
                   this.$router.push('/businesses/management');
                 }
               }).catch(r => {
                 this.errors = r.responseJSON;
               });
             }
```

