# Emails

## Guess Emails

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/guess_email.json')
res = Net::HTTP.post_form(uri, 'key' => 'abc123yourkeyhere', 'first_name' => 'ryan', 'last_name' => 'buckley', 'company_name' => 'toofr.com', 'callback_url' => 'https://www.yourcallbackurlhere.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/guess_email.json'
payload = {'key': 'abc123yourkeyhere', 'first_name': 'ryan', 'last_name': 'buckley', 'company_name': 'toofr.com', 'callback_url' => 'https://www.yourcallbackurlhere.com'}
r = requests.post(uri, data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&first_name=ryan&last_name=buckley&company_name=toofr.com&callback_url=https://yourcallbackurlhere.com"" https://www.findemails.com/api/v1/guess_email.json
```

> Response without callback URL parameter:

```json
{
  "ryan@toofr.com": {
    "confidence": 100,
    "state": "high",
    "email": "ryan@toofr.com",
    "detail": [
      {"description": "Mailserver score", "response": "+40"}, 
      {"description": "Pattern score", "response": "+27"}, 
      {"description": "MX records score", "response": "+10"}, 
      {"description": "Catchall score", "response": "+10"}, 
      {"description": "Uniqueness score", "response": "+2"}, 
      {"description": "List score", "response": "+2"}, 
      {"description": "Name score", "response": "+2"}, 
      {"description": "Disposable score", "response": "+2"}, 
      {"description": "Gibberish score", "response": "+2"}
    ],
    "employee": {
      "first_name": "ryan",
      "last_name": "buckley",
      "title": "founder",
      "profile": {
        "fn":"Ryan Buckley",
        "photo":"https://media.licdn.com/dms/image/C4D03AQFIi292VtKikw/profile-displayphoto-shrink_200_200/0?e=1536192000&v=beta&t=aXWOwRlu17VF_r96euIeWvX00I8OYfOrwhaK-Xbmksg",
        "title":"Builder of ToOfr, Inlistio, and Voxloca. Author of The Parallel Entrepreneur. Resident of Contra Costa County.",
        "linkedin_profile":"https://www.linkedin.com/in/rbuckley"
      },
      "email": 
        {
          "email": "ryan@toofr.com",
          "confidence": 70,
          "state": "high"
        }
      }
    } 
  }
}
```

> Response with callback URL parameter:

```json
{
    "success": true
}

```

> Response at your callback URL:

```json
{
  "ryan@toofr.com": {
    "confidence": 100,
    "state": "high",
    "email": "ryan@toofr.com",
    "detail": [
      {"description": "Mailserver score", "response": "+40"},
      {"description": "Pattern score", "response": "+27"},
      {"description": "MX records score", "response": "+10"},
      {"description": "Catchall score", "response": "+10"},
      {"description": "Uniqueness score", "response": "+2"},
      {"description": "List score", "response": "+2"},
      {"description": "Name score", "response": "+2"},
      {"description": "Disposable score", "response": "+2"},
      {"description": "Gibberish score", "response": "+2"}
    ],
    "employee": {
      "first_name": "ryan",
      "last_name": "buckley",
      "title": "founder",
      "profile": {
        "fn":"Ryan Buckley",
        "photo":"https://media.licdn.com/dms/image/C4D03AQFIi292VtKikw/profile-displayphoto-shrink_200_200/0?e=1536192000&v=beta&t=aXWOwRlu17VF_r96euIeWvX00I8OYfOrwhaK-Xbmksg",
        "title":"Builder of ToOfr, Inlistio, and Voxloca. Author of The Parallel Entrepreneur. Resident of Contra Costa County.",
        "linkedin_profile":"https://www.linkedin.com/in/rbuckley"
      },
      "email":
        {
          "email": "ryan@toofr.com",
          "confidence": 70,
          "state": "high"
        }
      }
    }
  }

```

This endpoint discovers emails based on the first name, last name, and company name.

### HTTP Request 

`POST https://www.findemails.com/api/v1/guess_email.json`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [FindEmails account page](https://www.findemails.com/account)
first_name | This is the text of the first name of your prospect, cleansed of spaces and non-ASCII characters (por favor!)
last_name | This is the text of the last name of your prospect, cleansed of spaces and non-ASCII characters (por favor!)
company_name | This is the text of either the company name or website
callback_url (optional) | The URL where you want FindEmails to send the  response. It is recommended to add a callback URL to get the best results from our system .


<aside class="success">
FindEmails works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
</aside>

## Test or Verify Emails

```ruby
require 'net/http'
require 'json'
 
uri = URI('https://www.findemails.com/api/v1/test_email.json')
res = Net::HTTP.post_form(uri, 'key' => 'abc123yourkeyhere', 'email' => 'ryan@toofr.com', 'callback_url' => 'https://www.yourcallbackurlhere.com')
JSON.parse(res.body)
```

```python
import requests
 
uri = 'https://www.findemails.com/api/v1/guess_email.json'
payload = {'key': 'abc123yourkeyhere', 'email': 'ryan@toofr.com', 'callback_url': 'https://www.yourcallbackurlhere.com'}
r = requests.post(uri, data = payload)
r.json()
```

```shell
curl --data "key=abc123yourkeyhere&email=ryan@scripted.com&callback_url=https://www.yourcallbackurlhere.com" https://www.findemails.com/api/v1/test_email.json
```

> The above command returns JSON structured like this:

```json
{ 
  "email": "ryan@toofr.com", 
  "confidence": 100,
  "state": high,
  "detail": [
    {"description": "Mailserver score", "response": "+40"}, 
    {"description": "Pattern score", "response": "+27"}, 
    {"description": "MX records score", "response": "+10"}, 
    {"description": "Catchall score", "response": "+10"}, 
    {"description": "Uniqueness score", "response": "+2"}, 
    {"description": "List score", "response": "+2"}, 
    {"description": "Name score", "response": "+2"}, 
    {"description": "Disposable score", "response": "+2"}, 
    {"description": "Gibberish score", "response": "+2"}
  ],
  "employee": {
    "first_name": "ryan",
    "last_name": "buckley",
    "title": "founder",
    "profile": {
      "fn":"Ryan Buckley",
      "photo":"https://media.licdn.com/dms/image/C4D03AQFIi292VtKikw/profile-displayphoto-shrink_200_200/0?e=1536192000&v=beta&t=aXWOwRlu17VF_r96euIeWvX00I8OYfOrwhaK-Xbmksg",
      "title":"Builder of ToOfr, Inlistio, and Voxloca. Author of The Parallel Entrepreneur. Resident of Contra Costa County.",
      "linkedin_profile":"https://www.linkedin.com/in/rbuckley"
    },
    "email": 
      {
        "email": "ryan@toofr.com",
        "confidence": 70,
        "state": "high"
      }
    }
  }
}
```

This endpoint delivers our [confidence score](http://blog.toofr.com/how-to-lower-your-bounce-rates-with-our-confidence-score/) for a given email address.

### HTTP Request

`POST https://www.findemails.com/api/v1/test_email.json`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [FindEmails account page](https://www.findemails.com/account)
email | The properly formatted email address you want to test
callback_url | Where you want the response to be sent.