# Lists

## Get All Lists

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/lists')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/lists'
payload = {'key': 'abc123yourkeyhere'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/lists?key=abc123yourkeyhere
```

> The above command returns a JSON array structured like this:

```json
[
  { 
    "id":137,
    "name":"My first file upload",
    "description":"Prospects generated from web scrape.", 
    "created_at":"2017-05-20T20:55:44.635Z", 
    "state":"finished",
    "records_count_in":5,
    "records_count_processed":5
  },
  {
    "id":134,
    "name":"Web results",
    "description":"Good emails found by my VA.", 
    "created_at":"2017-05-16T19:56:10.155Z",
    "state":"finished",
    "records_count_in":null,
    "records_count_processed":null
  }
]
```

This endpoint delivers the array of lists seen in your account at https://www.toofr.com/lists/owned.

### HTTP Request

`GET https://www.toofr.com/api/v1/lists`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)

## Get A Specific List

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/lists/:id')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/lists/:id'
payload = {'key': 'abc123yourkeyhere'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/lists/:id?key=abc123yourkeyhere
```

> The above command returns JSON structured like this:

```json
{
  "id":137,
  "name":"My first file upload",
  "description":"Prospects generated from web scrape.", 
  "created_at":"2017-05-20T20:55:44.635Z", 
  "state":"finished",
  "records_count_in":5,
  "records_count_processed":5
}
```

This endpoint delivers the array of lists seen in your account at https://www.toofr.com/lists/owned.

### HTTP Request

`GET https://www.toofr.com/api/v1/lists/:id`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)

## Create A List

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/lists')
res = Net::HTTP.post_form(uri, 'key' => 'abc123yourkeyhere', 'name' => 'API list', 'description' => 'Created via API')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/lists'
payload = {'key': 'abc123yourkeyhere', 'name': 'API list', 'description': 'Created via API'}
r = requests.post(uri, data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&name='API list'&description='Created via API'" https://www.toofr.com/api/v1/lists
```

> The above command returns JSON structured like this:

```json
{
  "id":137,
  "name":"My first file upload",
  "description":"Prospects generated from web scrape.", 
  "created_at":"2017-05-20T20:55:44.635Z", 
  "state":"finished",
  "records_count_in":5,
  "records_count_processed":5
}
```

This endpoint delivers the array of lists seen in your account at https://www.toofr.com/lists/owned.

### HTTP Request

`GET https://www.toofr.com/api/v1/lists/:id`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)