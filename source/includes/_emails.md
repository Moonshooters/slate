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
r = requests.post(uri, data = payload)
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
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
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
r = requests.post(uri, data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&email=ryan@scripted.com" https://www.toofr.com/api/v1/test_email.json
```

> The above command returns JSON structured like this:

```json
{ "email": "ryan@toofr.com", "confidence": 119 }
```

This endpoint delivers our [confidence score](http://blog.toofr.com/how-to-lower-your-bounce-rates-with-our-confidence-score/) for a given email address.

### HTTP Request

`POST https://www.toofr.com/api/v1/test_email.json`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
email | The properly formatted email address you want to test

## Get Prospects

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/get_prospects.json')
res = Net::HTTP.post_form(uri, 'key' => 'abc123yourkeyhere', 'company' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/get_prospects.json'
payload = {'key': 'abc123yourkeyhere', 'company': 'toofr.com'}
r = requests.post(uri, data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&company=toofr.com" https://www.toofr.com/api/v1/get_prospects.json
```

> The above command returns JSON structured like this:

```json
{ "prospects": {
  "domain":"toofr.com",
  "prospects":    
    [
      {"id":null,"email":"ryan@toofr.com","first_name":"Ryan","last_name":"Buckley","confidence":119},
      {"id":null,"email":"pinak@toofr.com","first_name":"Pinak","last_name":"Thakkar","confidence":79},
      {"id":null,"email":"Ryan@toofr.com","first_name":"Ryan","last_name":"Buckley","confidence":60},
      {"id":null,"email":"ryan.buckley@toofr.com","first_name":"ryan","last_name":"buckley","confidence":46},
      {"id":null,"email":"ryanbuckley@toofr.com","first_name":"ryan","last_name":"buckley","confidence":45},
      {"id":null,"email":"ryan_buckley@toofr.com","first_name":"ryan","last_name":"buckley","confidence":44},
      {"id":null,"email":"ryan-buckley@toofr.com","first_name":"ryan","last_name":"buckley","confidence":43}
    ]
  },
  "top_pattern":
  [ "first name", "miles@toofr.com" ]
}
```

This endpoint delivers the prospects in our database based on company name or website.

### HTTP Request

`POST https://www.toofr.com/api/v1/get_prospects.json`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
company | This is the text of either the company name or website.

<aside class="success">
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit. 
</aside>
