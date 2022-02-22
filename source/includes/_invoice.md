# Invoice

## Get All Invoices

```shell
curl "http://api.iworq.net/api/v1/invoices/1/1100" -H "Authorization: 123456"
```

```ruby
require "uri"
require "net/http"

url = URI("https://api.iworq.net/v1/invoices/1/1100")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Get.new(url)
request["Authorization"] = "123456"

response = https.request(request)
puts response.read_body
```

```python
import requests

response = requests.get("https://api.iworq.net/v1/invoices/1/1100", headers={"Authorization": "123456"})
print(response)
```

```javascript
var request = require("request");
var options = {
    "method": "GET",
    "url": "https://api.iworq.net/v1/invoices/1/1100",
    "headers": {
        "Authorization": "123456"
    }
};
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.iworq.net/v1/invoices/1/1100',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: 123456'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "invoiceNumber": "123456",
    "invoiceDate": "02/22/2022",
    "invoiceDueDate": "02/23/2022",
    "amount": 100.00,
    "amountPaid": 0.00
  },
  {
    "id": 2,
    "invoiceNumber": "654321",
    "invoiceDate": "02/12/2022",
    "invoiceDueDate": "02/13/2022",
    "amount": 80.00,
    "amountPaid": 0.00
  }
]
```

This endpoint retrieves all invoices for an application.

### HTTP Request

`GET https://api.iworq.net/v1/invoices/<AccountId>/<ApplicationId>`

### Query Parameters

Parameter |  Description
--------- |  -----------
AccountId | Unique identifier for your iWorQ account
ApplicationId | Unique identifier for your desired application

<!--<aside class="success">
Remember — a happy invoice is an authenticated invoice!
</aside>-->

## Get a Specific Invoice

```ruby
require "uri"
require "net/http"

url = URI("https://api.iworq.net/v1/invoice/123456?includes=entityinfo")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Get.new(url)
request["Authorization"] = "123456"

response = https.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.iworq.net/v1/invoice/123456?includes=entityinfo"

payload={}
headers = {
  'Authorization': '123456'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request GET 'https://api.iworq.net/v1/invoice/123456?includes=entityinfo' --header 'Authorization: 123456'
```

```javascript
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.iworq.net/v1/invoice/123456?includes=entityinfo',
  'headers': {
    'Authorization': '123456'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.iworq.net/v1/invoice/123456?includes=entityinfo',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: 123456'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
    "id": 1,
    "invoiceNumber": "123456",
    "invoiceDate": "02/22/2022",
    "invoiceDueDate": "02/23/2022",
    "amount": 100.00,
    "amountPaid": 0.00,
    "entityInfo": {
        "id": 2468,
        "number": 20220202,
        "text1": "Globe Trotters Contracting, Co.",
        "text2": "123 Main St.",
        "text3": "Logan",
        "text4": "UT"
    }
}
```

This endpoint retrieves a specific invoice by its id

<!--<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>-->

### HTTP Request

`GET https://api.iworq.net/v1/invoice/<ID>?includes=`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the invoice
includes | Optional parameter to include additional information (ie entity,property)

## Delete a Specific Invoice

```ruby
require "uri"
require "net/http"

url = URI("https://api.iworq.net/v1/invoice/123456")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Delete.new(url)
request["Authorization"] = "123456"

response = https.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.iworq.net/v1/invoice/123456"

payload={}
headers = {
  'Authorization': '123456'
}

response = requests.request("DELETE", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request DELETE 'https://api.iworq.net/v1/invoice/123456' --header 'Authorization: 123456'
```

```javascript
var request = require('request');
var options = {
  'method': 'DELETE',
  'url': 'https://api.iworq.net/v1/invoice/123456',
  'headers': {
    'Authorization': '123456'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.iworq.net/v1/invoice/123456',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'DELETE',
  CURLOPT_HTTPHEADER => array(
    'Authorization: 123456'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "id": 123456,
  "deleted" : ":("
}
```

This endpoint deletes a specific invoice.

### HTTP Request

`DELETE https://api.iworq.net/v1/invoice/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the invoice to delete

