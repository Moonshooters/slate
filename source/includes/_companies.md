# Companies

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
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple)
</aside>
