# Companies

## Get Profiles

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/profile')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'first_name' => 'ryan', 'last_name' => 'buckley', 'email' => 'ryan@toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/profile'
payload = {'key': 'abc123yourkeyhere', 'first_name': 'ryan', 'last_name': 'buckley', 'email': 'ryan@toofr.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/profile?key=abc123yourkeyhere&first_name=ryan&last_name=buckley&email=ryan@toofr.com
```

> The above command returns JSON structured like this:

```json
{
  "profile": {
    "fn":"Ryan Buckley",
    "photo":"https://media.licdn.com/mpr/mpr/shrinknp_200_200/p/3/000/063/38c/276e158.jpg",
    "title":"CEO of Toofr",
    "linkedin_profile":"https://www.linkedin.com/in/rbuckley"
  }
}
```

This endpoint returns the profile data we have on a given prospect and attempts to fetch it in real-time if it's not in our database.

### HTTP Request

`GET https://www.toofr.com/api/v1/profile`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
first_name | The first name of the prospect
last_name | The last name of the prospect
email | The known email address of the prospect



## Get Company Industry and Agency Data

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/classify')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company_name' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/classify'
payload = {'key': 'abc123yourkeyhere', 'company_name': 'toofr.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/classify?key=abc123yourkeyhere&company_name=toofr.com
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

`GET https://www.toofr.com/api/v1/classify`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
company_name | This is the text of either the company name or website.

<aside class="success">
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
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

uri = URI('https://www.toofr.com/api/v1/get_domain')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company_name' => 'toofr')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/get_domain'
payload = {'key': 'abc123yourkeyhere', 'company_name': 'toofr'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/get_domain?key=abc123yourkeyhere&company_name=toofr
```

> The above command returns JSON structured like this:

```json
{
  "domain":"toofr.com"
}
```

This endpoint uses our natural language processing engine to determine the industry and agency category and status of any website.

### HTTP Request

`GET https://www.toofr.com/api/v1/get_domain`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
company_name | This is the text of the company name you need the website for.

### Query Responses

Parameter | Description
--------- | -----------
domain | The best matching domain we could find for the company_name you entered.