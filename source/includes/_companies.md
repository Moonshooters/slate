# Companies

## Get Company Industry and Agency Data

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/classify')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company_name' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/classify'
payload = {'key': 'abc123yourkeyhere', 'company_name': 'toofr.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/classify?key=abc123yourkeyhere&company_name=toofr.com
```

> The above command returns JSON structured like this:

```json
{
  "industry":"marketing_and_advertising",
  "agency_category":"advertising",
  "is_agency":"no"
}
```

This endpoint uses our natural language processing engine to determine the industry and agency category and status of any website.

### HTTP Request

`GET https://www.findemails.com/api/v1/classify`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [FindEmails account page](https://www.findemails.com/account)
company_name | This is the text of either the company name or website.

<aside class="success">
FindEmails works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
</aside>

### Query Responses

Parameter | Description
--------- | -----------
industry | The general industry our artificial intelligence believes the website to be in.
is_agency | A boolean (true / false) response on whether we believe the company is an agency.
agency_category | If we believe the company is an agency, this is the more specific agency category it falls under. 





## Convert Company Name to Domain

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/get_domain')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company_name' => 'toofr')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/get_domain'
payload = {'key': 'abc123yourkeyhere', 'company_name': 'toofr'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/get_domain?key=abc123yourkeyhere&company_name=toofr
```

> The above command returns JSON structured like this:

```json
{
  "domain":"toofr.com"
}
```

This endpoint uses our natural language processing engine to determine the industry and agency category and status of any website.

### HTTP Request

`GET https://www.findemails.com/api/v1/get_domain`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [FindEmails account page](https://www.findemails.com/account)
company_name | This is the text of the company name you need the website for.

### Query Responses

Parameter | Description
--------- | -----------
domain | The best matching domain we could find for the company_name you entered.