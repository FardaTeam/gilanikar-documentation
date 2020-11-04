# Retrieve jobs` modules and its details

```URL
/public/api/settings/module/plan/{key}
```

## Url Params
parameter|Description
---|---
key| key of module

## Request Specification
<table>
<tr>
<th>Method</th>
<td>GET</td>
</tr>
</table>


### Url Example
this key used to restrict result and it return only defined keys detail 
``` query String
/public/api/settings/module/plan/retailing_store
```
## Response


Http Code| Meaning|Response body
---|---|---
200|Ok|array of job modules` plans

**Response Content Type:** 
application/json

## Response Body
Array of job modules contains following property:

- plan_id
- key
- title
- description
- days
- price
- payment_type


## Example
Example of using this api in vue component

```javascript
function getModulesPlans(key) {
               if (!Array.isArray(this.modulePlans[key])) {
                 this.modulePlans[key] = 'loading';
                 xhr(`public/api/settings/module/plan/${key}`).then(r => {
                   this.modulePlans[key] = r;
                   this.$forceUpdate();
                 }).catch(() => {
                   this.modulePlans[key] = undefined
                 });
               }
             }
```

