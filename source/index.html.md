---
title: Toofr Sales Hacking API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='https://www.toofr.com/registration'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Toofr Sales Hacking API! You can use our API to guess business emails, test emails, and extract prospects from webpages and our database.

We have language examples in Shell, Ruby, and Python. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

Every Toofr user has access to our API. API calls use credits in the same way that our web application use credits. For more information on how credits are used, view our [FAQ](https://www.toofr.com/faq).

To get an API key, first [register for a free Toofr account](https://www.toofr.com/registration). Check your email for a confirmation message, click through the link, and log in. Your API key is available on your [Account page](https://www.toofr.com/account).

If you run out of credits, you'll need to sign up for a [monthly plan](https://www.toofr.com/pricing) to get more. Currenty they start at just $29/mo.

Your API key is a long alphanumeric string that looks similar to this:

`e3eabca12ccabcd3dd1233fb506b7031`

<aside class="notice">
Key your API key secure! If you don't, someone can use all of your credits for the month, and even send you into overage. You're responsible for all API usage.
</aside>

# Emails

## Guess Emails

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/guess_email.json')
res = Net::HTTP.post_form(uri, 'key' => 'abc123yourkeyhere', 'first_name' => 'ryan', 'last_name' => 'buckley', 'company_name' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/guess_email.json'
payload = {'key': 'abc123yourkeyhere', 'first_name': 'ryan', 'last_name': 'buckley', 'company_name': 'toofr.com'}
r = requests.post('https://www.toofr.com/api/v1/guess_email.json', data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&first_name=ryan&last_name=buckley&company_name=toofr.com" https://www.toofr.com/api/v1/guess_email.json
```

> The above command returns JSON structured like this:

```json
{
  "ryan@toofr.com": {
    "confidence":119,"email":"ryan@toofr.com","default":20
  },
  "rbuckley@toofr.com": {
    "confidence":20,"email":"rbuckley@toofr.com","default":15
  },
  "ryan.buckley@toofr.com": {
    "confidence":18,"email":"ryan.buckley@toofr.com","default":16
  },
  "ryanbuckley@toofr.com": {
    "confidence":17,"email":"ryanbuckley@toofr.com","default":17
  },
  "ryan_buckley@toofr.com": {
    "confidence":16,"email":"ryan_buckley@toofr.com","default":18
  },
  "ryan-buckley@toofr.com": {
    "confidence":15,"email":"ryan-buckley@toofr.com","default":19
  },
  "ryanb@toofr.com": {
    "confidence":14,"email":"ryanb@toofr.com","default":14
  },
  "buckley@toofr.com": {
    "confidence":13,"email":"buckley@toofr.com","default":13
  }
}
```

This endpoint discovers emails based on the first name, last name, and company name.

### HTTP Request

`POST https://www.toofr.com/api/v1/guess_email.json`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
first_name | This is the text of the first name of your prospect, cleansed of spaces and non-ASCII characters (por favor!)
last_name | This is the text of the last name of your prospect, cleansed of spaces and non-ASCII characters (por favor!)
company_name | This is the text of either the company name or website

<aside class="success">
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple)
</aside>

## Test Emails

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/test_email.json')
res = Net::HTTP.post_form(uri, 'key' => 'abc123yourkeyhere', 'email' => 'ryan@toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/guess_email.json'
payload = {'key': 'abc123yourkeyhere', 'email': 'ryan@toofr.com'}
r = requests.post('https://www.toofr.com/api/v1/test_email.json', data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&email=ryan@scripted.com" https://www.toofr.com/api/v1/test_email.json
```

> The above command returns JSON structured like this:

```json
{ "email": "ryan@toofr.com", "confidence": 119 }
```

This endpoint discovers our [confidence score](http://blog.toofr.com/how-to-lower-your-bounce-rates-with-our-confidence-score/) for a given email address.

### HTTP Request

`POST https://www.toofr.com/api/v1/test_email.json`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
email | The properly formatted email address you want to test
