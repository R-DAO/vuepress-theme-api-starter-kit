<Block>

# Transactions

</Block>

<Block>

## User Transaction

You can use this API to request for transactions, corresponding to user address.

### Endpoint

```bash
GET /v2/users/transactions
```

### Query Parameters

|   Name   |  Type  | Description |      Required      |
| :------: | :----: | :---------: | :----------------: |
| module | string |  module   | :heavy_check_mark: |
|  address   | string |    public key address    | :heavy_check_mark: |
| endblock | number |  Block limit   | :heavy_check_mark: |
|  limit   | number |    Number of transactions   | :heavy_minus_sign: |
|  page   | number |    Pagination Number   | :heavy_minus_sign: |
|  sort   | string |    Sort Order  | :heavy_minus_sign: |


### Response

```json
Status: 200

{ 
  "status": "success",
  "transactions": [
    {
      ...
    },
  ]
}
```

### Error Code

```json
Status: 400

{
  "status": "failed",
  "error": {
    "message": "Invalid Request"
  }
}
```

<Example>

<CURL>
```bash
curl --location -g --request GET '{{BASE_URI_ZKSYNC}}/v2/users/transactions?module=account&address=0xc679HDJH9HHJI098a3CC98sjskjjks&startblock=0&endblock=100000&limit=1&page=5&sort=desc'
```
</CURL>

Javascript - Fetch

```
var url = new URL("{{BASE_URI_ZKSYNC}}/v2/users/transactions"),
    params = {
      module="account",
      address="0xc679HDJH9HHJI098a3CC98sjskjjks&startblock=0",
      endblock=100000,
      limit=1,
      page=5,
      sort="desc"
    }
Object.keys(params).forEach(key => url.searchParams.append(key, params[key]))

fetch(url, {
  method: 'GET',
  redirect: 'follow'
})
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

</Example>

</Block>
