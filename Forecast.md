## API Token
進行查詢前，先取得通行證，每次取到的 Token 可使用 12 小時。


### 取得 Token

```http
GET /api/AccessToken/{apiKey}
```

| Parameter | Type | Description |
| :--- | :---: | :--- |
| `apikey` | `string` | **Required**. Your API key |

API key將另外提供。


### Responses
> _HTTP Status Code：_ **200**
```json
{
  "status": "success",
  "message": "string",
  "data": {
    "token": "string"
  }
}
```

> _HTTP Status Code：_ **404**
```json
{
  "status": "error",
  "message": "string",
  "data": null
}
```

---
## Forecast


### 查詢可用量

```http
GET /api/DealerForecast/
```

| Header Parameter | Type | Description |
| :--- | :---: | :--- |
| `token` | `string` | 從 _accesstoken_ 取到的字串 |

### Responses
> _HTTP Status Code：_ **200**
```json
{
  "status": "success",
  "message": "",
  "data": [
    {
      "ItemNo": "string",
      "StockQty": "int",
      "UsefulQty": "int"
    }
  ]
}
```

| 欄位 | 型別 | 說明 |
| :--- | :---: | :--- |
| ItemNo | `string` | 寶工品號 |
| StockQty | `int` | 寶工可用量 |
| UsefulQty | `int` | 廠商可用量 |


> _HTTP Status Code：_ **404**
```json
{
  "status": "error",
  "message": "查無資料",
  "data": null
}
```

> _HTTP Status Code：_ **403**
```json
{
  "status": "error",
  "message": "token已失效, 請重新取得",
  "data": null
}
```

---
### 上傳預估資料

```http
POST /api/DealerForecast/
```

| Header Parameter | Type | Description |
| :--- | :---: | :--- |
| `token` | `string` | 從 _accesstoken_ 取到的字串 |


> POST body：application/json
```javascript
[
  {
    "PKItemNo": "1PK-036S",
    "PredictQty": 10
  },
  {
    "PKItemNo": "MT-8100",
    "PredictQty": 20
  }
]
```
| 欄位 | 型別 | 說明 |
| :--- | :---: | :--- |
| PKItemNo | `string` | 寶工品號 |
| PredictQty | `int` | 預估數量 |


### Responses
> _HTTP Status Code：_ **200**
```json
{
  "status": "success",
  "message": null,
  "data": {
    "traceID": "string",
    "inputTime": "2022-05-20T11:31:29Z"
  }
}
```