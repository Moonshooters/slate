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

This endpoint delivers the JSON hash of a specific list.

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

`POST https://www.toofr.com/api/v1/lists`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
name | A short string to name your list
description | A longer string to describe your list
file_type | For bulk processing, select the type of file it would be if you were to import it rather than use the API. See acceptable values below or leave blank if no processing is required.  

File Type | Description
--------- | -----------
guess | You provide the names and companies of prospects and Toofr appends the best email and confidence score
guess_all | Like guess, but Toofr gives all emails and confidence scores, not just the best one
test | You provide emails and Toofr appends a confidence score
get | You provide companies (names or websites) and Toofr returns all the related emails with confidence scores in our database 
pattern | You provide companies (names or websites) and Toofr returns the best related email pattern