# List Records

## Get All List Records On A List

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/lists/:list_id/list_records')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/lists/:list_id/list_records'
payload = {'key': 'abc123yourkeyhere'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/lists/:list_id/list_records?key=abc123yourkeyhere
```

> The above command returns a JSON array structured like this:

```json
[
  {
    "id":16347, 
    "first_name":"ryan", 
    "last_name":"buckerooski",
    "company":"toofr.com",
    "email_address":"ryan@toofr.com",
    "meta":{
      "top":"true"
    },
    "created_at":"2017-05-24T03:33:37.234Z",
    "processed_at":"2017-05-24T03:33:53.325Z"
  },
  {
    "id":16346,
    "first_name":"james",
    "last_name":"bond",
    "company":"toofr.com",
    "email_address":"bondjamesbond@toofr.com",
    "meta":{
      "top":"true"
    },
    "created_at":"2017-05-24T03:32:29.271Z",
    "processed_at":"2017-05-24T03:32:34.876Z"
  },
]
```

This endpoint delivers the array of list records you would see if you exported your list from https://www.toofr.com/lists/:id.

### HTTP Request

`GET https://www.toofr.com/api/v1/lists/:list_id/list_records`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)

## Get A Specific List Record

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/lists/:list_id/list_records/:id')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/lists/:list_id/list_records/:id'
payload = {'key': 'abc123yourkeyhere'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/lists/:list_id/list_records/:id?key=abc123yourkeyhere
```

> The above command returns JSON structured like this:

```json
{
  "id":16347, 
  "first_name":"ryan", 
  "last_name":"buckerooski",
  "company":"toofr.com",
  "email_address":"ryan@toofr.com",
  "meta":{
    "top":"true"
  },
  "created_at":"2017-05-24T03:33:37.234Z",
  "processed_at":"2017-05-24T03:33:53.325Z"
}
```

This endpoint delivers the JSON hash of a specific list_record.

### HTTP Request

`GET https://www.toofr.com/api/v1/lists/:id`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)

## Create A List Record

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/lists/:list_id/list_records')
res = Net::HTTP.post_form(uri, 'key' => 'abc123yourkeyhere', 'first_name' => 'Ryan', 'last_name' => 'Buckley', 'company' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/lists/:list_id/list_records'
payload = {'key': 'abc123yourkeyhere', 'first_name': 'Ryan', 'last_name': 'Buckley', 'company': 'toofr.com'}
r = requests.post(uri, data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&first_name=Ryan&last_name=Buckley&company=toofr.com" https://www.toofr.com/api/v1/lists/:list_id/list_records
```

> The above command returns JSON structured like this:

```json
{
  "id":16348,
  "first_name":"ryan",
  "last_name":"buckerooski",
  "company":"toofr.com",
  "email_address":null,
  "meta":{}
}
```

This endpoint creates and initiates a background process on the created list record. The type of process run will be based on the file_type of its associated list (the :list_id it's created on). 

### HTTP Request

`POST https://www.toofr.com/api/v1/lists/:list_id/list_records`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)