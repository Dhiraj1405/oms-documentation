# Check Inventory API

Get the stock details of the product on the specific locations. To get the stock details, you will need to call the `/checkInventory` endpoint with the POST method. 

## Request

### End Point
`https://<host>/api/checkInventory`

Example: https://demo-oms.hotwax.io/api/checkInventory

### Header
Content-Type: application/json


### Body
```
{
  "fieldsToSelect": "<fields>",
  "viewSize": "<view size>",
  "viewIndex": "<view index>",
  "filters": {
    "sku": "<sku1>", "<sku2>", "<sku>",
    "sku_op": "in",
    "facilityId": ["<facilityId1>", "<facilityId2>"],
    "facilityId_op": "in"
  }
}
```

| Parameter Name | Description | Required (Y/N) |
| --- | --- | --- |
| `sku` | The SKU of the product | N |
| `sku_op` | The operator | N |
| `fieldsToSelect` | The fields that you want to select or retrieve in your query results. | N |
| `viewSize` |  The size of items to be displayed in a single view  | N |
| `viewIndex` | The index of the current view | N |
| `productId` | HotWax Commerce internal product Id | N |
| `productId_op` | The operator | N |
| `facilityId` | The HotWax Commerce facility Id where product inventory is located | N |

Note: 
<li>It is required to pass either `sku` or `productId`. </li>
<li>Search limit = 100 items </li>


## Response

### Status Code
HTTP/1.1 200 OK

### Headers
Content-Type: application/json


### Body
  
```
{
  "count": "1",
  "docs": [
    {
      "productId": "<product ID>",
      "facilityId": "<faciltiy ID>",
      "atp": "<atp>"
    }
  ]
}
```

| Parameter Name | Description |
| --- | --- |
| `count`| Results count |
| `docs` | The array of results found |
| `facilityId` | The Id of the facility in HotWax |
| `atp` | The available to promise inventory of the product |
