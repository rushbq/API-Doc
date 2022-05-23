## Pro'sKit API


### 取得查詢Token

```http
GET /api/AccessToken/{apiKey}
```

| Parameter | Type | Description |
| :--- | :---: | :--- |
| `apikey` | `string` | **Required**. Your API key |


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
