---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='mailto:jake@bestow.co'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Bestow Quote API.  Users of the API can get price quotes for Bestow life insurance products by passing in a few customer parameters. 

# Authentication

> To authorize, use this code:

```shell

curl -X POST \
  https://api.hellobestow.com/v2/quote \
  -H 'Authorization: 82zZIHeBqUlBtICMX5li' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
	"birth_date": "1980-01-01", 
	"gender": "male", 
	"height_feet": 6, 
	"height_inches": 0, 
	"state": "TX", 
	"weight": 180
}
'
```


> Make sure to replace `82zZIHeBqUlBtICMX5li` with your API key.

Bestow uses API keys to allow access to the API. You can register a new Bestow API key by sending an [email to us](mailto:jake@bestow.co). 

Bestow expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: 82zZIHeBqUlBtICMX5li`

<aside class="notice">
You must replace <code>82zZIHeBqUlBtICMX5li</code> with your personal API key.
</aside>

# Quote

## Creating a Quote


> The above command returns JSON structured like this:

```json
{
  "product_rates": {
    "BT0201": {
      "100000": "8.33", 
      "150000": "12.50", 
      "200000": "16.67", 
      "250000": "18.54", 
      "300000": "22.25", 
      "350000": "25.96", 
      "400000": "29.67", 
      "450000": "33.38", 
      "50000": "4.63", 
      "500000": "37.08"
    }, 
    "BT1002": {
      "100000": "11.25", 
      "1000000": "55.83", 
      "150000": "14.38", 
      "200000": "17.50", 
      "250000": "16.66", 
      "300000": "19.33", 
      "350000": "22.00", 
      "400000": "24.66", 
      "450000": "27.33", 
      "50000": "11.38", 
      "500000": "29.58", 
      "550000": "32.21", 
      "600000": "34.83", 
      "650000": "37.46", 
      "700000": "40.08", 
      "750000": "42.71", 
      "800000": "45.33", 
      "850000": "47.96", 
      "900000": "50.58", 
      "950000": "53.21"
    }, 
    "BT2002": {
      "100000": "12.75", 
      "1000000": "69.16", 
      "150000": "16.63", 
      "200000": "20.50", 
      "250000": "21.04", 
      "300000": "24.58", 
      "350000": "28.12", 
      "400000": "31.66", 
      "450000": "35.21", 
      "50000": "10.58", 
      "500000": "36.25", 
      "550000": "39.54", 
      "600000": "42.83", 
      "650000": "46.12", 
      "700000": "49.41", 
      "750000": "52.71", 
      "800000": "56.00", 
      "850000": "59.29", 
      "900000": "62.58", 
      "950000": "65.87"
    }
  }, 
  "quote_id": "a3b4d9e4-567d-4d77-95da-4761b7985320"
}
```

This endpoint retrieves a quote.

### HTTP Request

`POST https://api.hellobestow.com/v2/quote`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
birth_date | required | Birth date in format YYYY-MM-DD
gender | true | "male" or "female"
height_feet | true | Feet part of height
height_inches | true | Inches part of height
state | true | The 2-character abbreviation of the US state
weight | true | Weight in lbs

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

