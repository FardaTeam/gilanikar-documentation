# Retrieve jobs` modules and its details

```URL
/public/api/settings/modules
```

## Request Specification
<table>
<tr>
<th>Method</th>
<td>GET</td>
</tr>
</table>

## Request Body
parameters Key | Format | Description
---|---|---
keys | string | comma separated job module`s keys

### Keys Example
this key used to restrict result and it return only defined keys detail 
``` query String
keys=retailing_store,wholesaler_store,retail_and_wholesaler_store
```
## Response


Http Code| Meaning|Response body
---|---|---
200|Ok|array of job modules

**Response Content Type:** 
application/json

## Response Body
Array of job modules contains following property:

- key
- title
- description
- image


## Example
Example of using this api in vue component

```javascript
function getModulesInfo() {
      const keys = ['retailing_store', 'wholesaler_store', 'retail_and_wholesaler_store'].join(',');
      xhr(`public/api/settings/modules?keys=${keys}`).then(r => {
        this.modules = r;
      })
    }
```

