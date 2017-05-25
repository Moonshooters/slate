# Companies

## Get Prospects and Patterns

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/prospect')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/prospect'
payload = {'key': 'abc123yourkeyhere', 'company': 'toofr.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/get_prospects?key=abc123yourkeyhere&company=toofr.com
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

`GET https://www.toofr.com/api/v1/get_prospects`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
company | This is the text of either the company name or website.

<aside class="success">
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
</aside>

## Get Company Industry and Agency Data

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/classify')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/classify'
payload = {'key': 'abc123yourkeyhere', 'company': 'toofr.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/classify?key=abc123yourkeyhere&company=toofr.com
```

> The above command returns JSON structured like this:

```json
{
  "industry":"marketing_and_advertising",
  "agency_category":"advertising",
  "is_agency":"no"}
```

This endpoint uses our natural language processing engine to determine the industry and agency category and status of any website.

### HTTP Request

`GET https://www.toofr.com/api/v1/classify`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
company | This is the text of either the company name or website.

<aside class="success">
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
</aside>

### Query Responses

Parameter | Description
--------- | -----------
industry | The general industry our artificial intelligence believes the website to be in.
is_agency | A boolean (true / false) response on whether we believe the company is an agency.
agency_category | If we believe the company is an agency, this is the more specific agency category it falls under. 
