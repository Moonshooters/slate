# Credits

## View Your Credit Balance and Subscription Plan

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/credits/balance')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/credits/balance'
payload = {'key': 'abc123yourkeyhere'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/credits/balance?key=abc123yourkeyhere
```

> The above command returns JSON structured like this:

```json
{
  "credits": 2047,
  "plan_name": 'Expert',
  "overage_rate": 0.1,
}
```

This endpoint delivers the number of credits in your account, the plan you're on (response is `null` if no plan is present) and the overage rate that Toofr will charge for negative balances.

### HTTP Request

`GET https://www.toofr.com/api/v1/credits/balance`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)

## Purchase Credits

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/credits/purchase')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'credits' => 2000)
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/credits/purchase'
payload = {'key': 'abc123yourkeyhere', 'credits': 2000}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/credits/purchase?key=abc123yourkeyhere&credits=2000
```

> The above command returns JSON structured like this:

```json
{
  "credits": 2047,
  "plan_name": 'Expert',
  "overage_rate": 0.1,
  "charge_status": "failed",
  "charge_message": "Successful API purchase of 2000 credits at $0.01/ea"
}
```

This endpoint delivers the number of credits in your account, the plan you're on (response is `null` if no plan is present) and the overage rate that Toofr will charge for negative balances.

### HTTP Request

`GET https://www.toofr.com/api/v1/credits/purchase`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
credits | The number of credits you want to purchase. It must be greater than 1000.

## Reimburse Credits with Flag Reports

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/credits/flag')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'employee_id' => 19821994, 'reason' => 2)
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/credits/purchase'
payload = {'key': 'abc123yourkeyhere', 'employee_id': 19821994, 'reason' => 2}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/credits/flag?key=abc123yourkeyhere&employee_id=19821994&reason=2
```

> The above command returns JSON structured like this:

```json
{
  "credits": 2047,
  "plan_name": 'Expert',
  "overage_rate": 0.1,
}
```

This endpoint accepts a flag report in exchange for a credit added to the account associated with the API key used to submit the report. Only one report is accepted per Employee ID.

### HTTP Request

`GET https://www.toofr.com/api/v1/credits/flag`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
employee_id | The integer ID number of the employee you're flagging. Get the ID from an Audiences query.
reason | The integer associated with the reason in the table shown below. 

### Flag Reasons

Parameter | Description
--------- | -----------
1 | The employee has the wrong title. 
2 | The employee is no longer at the company.
3 | The employee has the wrong email.

