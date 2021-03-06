

The document presents API specification of Ontology Explorer.

## explorer API

#### Mainnet explorer API 
[https://explorer.ont.io](https://explorer.ont.io)

#### Testnet explorer API 
[https://polarisexplorer.ont.io](https://polarisexplorer.ont.io)

## Specification

#### Parameter specification

Request and response parameters are in `SNAKE_CASE`  style, such as：`block_height`，`tx_hash`

#### URL specification

URLs follow the Restful style, define interfaces by resource, such as：`/v2/blocks`, `/v2/transactions/{tx_hash}`

#### URL request parameter specification

Multiple words are connected using underscores, such as：`/v2/blocks?page_size=10&page_number=1`

- **Page parameter**

  - page_size: number of records per page`(The page size is limited between 1 and 20)`.
  - page_number: number of pages.`(At least 1 or greater)`.

- **Time parameter**

  The maximum time range is **one week**.

  - start_time: start time, UNIX time.
  - end_time: end time, UNIX time.

#### Response

**HTTP Status Codes**
The API uses standard HTTP status codes to indicate the success or failure of an API call.

- **200 (Normal Request)** :Successful response.
- **400 (Bad Request)** :The server could not process the request, likely due to an invalid argument.
- **500 (Internal Server Error)** :An unexpected server issue was encountered.

**Response DTO**
A Status object is always included in the JSON response payload for both successful calls and failures when possible. During error scenarios you may reference the ```code``` and ```msg``` properties of the Status object.

```
{
  "code": 0,
  "msg": "SUCCESS",
  "result": {}
}
```

```code=0``` means successful calls ,```code!=0```means failures calls.