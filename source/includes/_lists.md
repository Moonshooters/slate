# Lists

## Get All Lists

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/lists')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/lists'
payload = {'key': 'abc123yourkeyhere'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/lists?key=abc123yourkeyhere
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

This endpoint delivers the array of lists seen in your account at https://www.findemails.com/lists/owned.

### HTTP Request

`GET https://www.findemails.com/api/v1/lists`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.findemails.com/account)
marketplace | (optional) Set to `true` if you want to list only the lists for sale in the Toofr marketplace
page | (optional) Set to any integer to paginate through results 


## Search Lists

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/lists/search')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere',  'query' => 'foobar', 'marketplace' => true)
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/lists/search'
payload = {'key': 'abc123yourkeyhere', 'query': 'foobar', 'marketplace': 'true'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/lists?key=abc123yourkeyhere&query=foobar&marketplace=true
```

> The above command returns a JSON array structured like this:

```json
[
  { 
    "id":137,
    "name":"List for sale",
    "description":"Prospects generated from web scrape.", 
    "created_at":"2017-05-20T20:55:44.635Z", 
    "state":"finished",
    "records_count_in":5,
    "records_count_processed":5
  },
  {
    "id":134,
    "name":"Prospects for sale",
    "description":"Good emails found by my VA.", 
    "created_at":"2017-05-16T19:56:10.155Z",
    "state":"finished",
    "records_count_in":10,
    "records_count_processed":10
  }
]
```

This endpoint delivers the array of lists seen in your own account at `https://www.findemails.com/lists/owned` or if you include the marketplace parameter then it will search the public marketplace lists at `https://www.findemails.com/email-lists`.

### HTTP Request

`GET https://www.findemails.com/api/v1/lists/search`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.findemails.com/account)
query | The term(s) you want to search for
marketplace | (optional) Set to `true` if you want to list only the lists for sale in the Toofr marketplace
page | (optional) Set to any integer to paginate through results 


## Get A Specific List

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/lists/:id')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/lists/:id'
payload = {'key': 'abc123yourkeyhere'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/lists/:id?key=abc123yourkeyhere
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

`GET https://www.findemails.com/api/v1/lists/:id`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.findemails.com/account)

## Create A List

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/lists')
res = Net::HTTP.post_form(uri, 'key' => 'abc123yourkeyhere', 'name' => 'API list', 'description' => 'Created via API')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/lists'
payload = {'key': 'abc123yourkeyhere', 'name': 'API list', 'description': 'Created via API'}
r = requests.post(uri, data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&name='API list'&description='Created via API'" https://www.findemails.com/api/v1/lists
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

This endpoint delivers the array of lists seen in your account at https://www.findemails.com/lists/owned.

### HTTP Request

`POST https://www.findemails.com/api/v1/lists`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.findemails.com/account)
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



## Purchase A Marketplace List

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/lists/:id/purchase')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/lists/:id/purchase'
payload = {'key': 'abc123yourkeyhere'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/lists/:id/purchase?key=abc123yourkeyhere
```

> The above command returns JSON structured like this. Use the List ID returned to access the list records in the list:

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

`POST https://www.findemails.com/api/v1/lists/:id/purchase`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.findemails.com/account)