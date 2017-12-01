# Audiences

## Build Email Lists and Audiences

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/audiences')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'websites' => 'toofr.com', 'titles' => 'ceo', 'page' => 1)
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/audiences'
payload = {'key': 'abc123yourkeyhere', 'websites': 'toofr.com', 'titles': 'ceo', 'page': 1}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/audiences?key=abc123yourkeyhere&websites=toofr.com&titles=ceo&page=1
```

> The above command returns JSON structured like this:

```json
{
  "total":10,
  "prospects": [
  {
    "id":2
    "first_name":"biz",
    "last_name":"stone",
    "title":"Head of social media",
    "profile": {
      "fn":"Biz Stone",
      "photo":"https://media.licdn.com/media/p/2/005/018/3d3/11bf5c3.jpg",
      "title":"Internet Guy",
      "linkedin_profile":"https://www.linkedin.com/in/bizstone/"
    },
    "email": {
      "email":"biz@scripted.com",
      "confidence":140,
      "state":"high"
    },
    "domain": {
      "domain":"scripted.com"
    },
    "title_confidence":280
  },
  {
    "id":1994
    "first_name":"kurdt",
    "last_name":"cobain",
    "title":"Nevermind",
    "profile": {},
    "email": {
      "email":"kurdt@scripted.com",
      "confidence":1994,
      "state":"high"
    },
    "domain": {
      "domain":"scripted.com"
    },
    "title_confidence":100
  },
  etc...
  ],
  "next_page":3,
  "total_pages":3,
  "status":"Succeeded."
  }
```

This endpoint delivers the prospects in our database based on websites or industries and titles. The response includes `total` which is the number of results delivered to the page and the credits consumed for the query as well as the pagination keys `next_page` and `total_pages`. A `status` message will alert you of any 202 status responses which require background processing. 

The results are sorted by title, so complete profiles are first, and then by confidence score. When your request doesn't yield any titles in the database, the API returns a 202 status and triggers a background process to search the internet. Run your request again in a minute to get the results.

### HTTP Request

`GET https://www.toofr.com/api/v1/audiences`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
websites | This is the website. It should be either a bare domain (like `google.com`) or a properly formed URL (like `https://www.google.com`). Include multiple websites by separating them with a comma.
industries | This is the industry category. It must match one or of the industry categories below. It must be an exact match. If you include both industries and websites, industries will be ignored.
titles | This is the title category. It must match one or of the title categories below. It must be an exact match. 
page | Optional integer to get another page of results (10 returned per page, so max of 10 credits consumed per page response).

### Title Categories

Use one of these title categories: `ceo`, `founder`, `cmo`, `cto`, `cfo`, `finance`, `marketing`, `engineering`, `product`, `sales`, `operations`,
`account_management`, `information_technology`, `data_science`, `human_resources`, `c_level`, `directors`, `presidents_and_vps`, `managers`

### Industry Categories

Use one of these industry categories: `construction`, `marketing_and_advertising`, `professional_training_coaching`, `consumer_services`, `leisure_travel_tourism`, `industrial_automation`, `computer_hardware`, `management_consulting`, `mining_metals`, `financial_services`, `medical_devices`, `information_technology_and_services`, `real_estate`, `consumer_electronics`, `computer_software`, `internet`, `hospitality`, `retail`, `accounting`, `research`, `hospital_health_care`, `oil_energy`, `music`, `computer_games`, `building_materials`, `law_practice`, `sporting_goods`, `nonprofit_organization_management`, `civic_social_organization`, `online_media`, `apparel_fashion`, `entertainment`, `individual_family_services`, `machinery`, `health_wellness_and_fitness`, `investment_banking`, `publishing`, `newspapers`, `architecture_planning`, `photography`, `shipbuilding`, `commercial_real_estate`, `cosmetics`, `import_and_export`, `medical_practice`, `fund_raising`, `media_production`, `insurance`, `printing`, `automotive`, `events_services`, `arts_and_crafts`, `renewables_environment`, `airlines_aviation`, `international_trade_and_development`, `telecommunications`, `philanthropy`, `design`, `human_resources`, `facilities_services`, `logistics_and_supply_chain`, `wholesale`, `farming`, `sports`, `transportation_trucking_railroad`, `staffing_and_recruiting`, `performing_arts`, `wine_and_spirits`, `environmental_services`, `packaging_and_containers`, `education_management`, `government_relations`, `chemicals`, `graphic_design`, `mental_health_care`, `plastics`, `computer_networking`, `mechanical_or_industrial_engineering`, `consumer_goods`, `military`, `food_beverages`, `computer_network_security`, `recreational_facilities_and_services`, `alternative_medicine`, `banking`, `information_services`, `government_administration`, `motion_pictures_and_film`, `outsourcing_offshoring`, `venture_capital_private_equity`, `legal_services`, `broadcast_media`, `biotechnology`, `pharmaceuticals`, `market_research`, `security_and_investigations`, `program_development`, `food_production`, `museums_and_institutions`, `luxury_goods_jewelry`, `fine_art`, `electrical_electronic_manufacturing`, `e_learning`, `higher_education`, `investment_management`, `religious_institutions`, `wireless`, `business_supplies_and_equipment`, `think_tanks`, `furniture`, `civil_engineering`, `capital_markets`, `executive_office`, `public_relations_and_communications`, `utilities`, `gambling_casinos`, `veterinary`, `translation_and_localization`, `maritime`, `textiles`, `writing_and_editing`, `primary_secondary_education`, `political_organization`, `international_affairs`, `public_policy`, `semiconductors`, `railroad_manufacture`, `aviation_aerospace`, `package_freight_delivery`, `animation`, `defense_space`, `restaurants`, `paper_forest_products`, `supermarkets`, `public_safety`, `glass_ceramics_concrete`, `ranching`, `tobacco`, `law_enforcement`, `warehousing`, `judiciary`, `alternative_dispute_resolution`, `dairy`, `fishery`, `libraries`, `nanotechnology`, `legislative_office`