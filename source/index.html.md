---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='mailto:jake@bestow.co'>Sign Up for a Developer Key</a>

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

> To get a quote, use this code:
 
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

Parameter | Required | Description
--------- | ------- | -----------
birth_date | true | Birth date in format YYYY-MM-DD
gender | true | "male" or "female"
height_feet | true | Feet part of height
height_inches | true | Inches part of height
state | true | The 2-character abbreviation of the US state
weight | true | Weight in lbs

<aside class="success">
Remember — Requests are rate limited at 10 requests per second
</aside>

### Return values

The call will receive a JSON object with a prices for a 2-year life insurance project (BT0201), 10-year product (BT1002), and a 20-year product (BT2002)

Product | Length of Policy
------ | ------
BT0201 | 2 year
BT1002 | 10 year
BT2002 | 20 year

Inside the Product offering, you will recieve different prices for different amounts of insurance the customer can buy.  In the example to the right, the values are

Product | Length of Policy | Face Value of Insurance | Price per Month
------- | ----- | --------------------- | ----
BT0201 | 2 year | $100,000 | $8.33
BT0201 | 2 year | $150,000 | $12.50
BT0201 | 2 year | $200,000 | $16.67


# Errors

The Bestow API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
404 | Not Found -- The specified url could not be found.
405 | Method Not Allowed -- You tried to access a quote with an invalid method.
429 | Too Many Requests -- You're requesting too many quotes! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
