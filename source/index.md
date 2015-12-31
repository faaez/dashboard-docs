---
title: Teneo Dashboard API Reference

<!-- language_tabs:
  - shell
  - ruby
  - python -->

<!-- toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a> -->

includes:
  - errors

search: true
---

# Introduction

This is the proposed API for Teneo Dashboard. Feel free to give us feedback or request changes. 

# Authentication

All api requests need to be authorized with an API key, without which, an error will be returned. 

<aside class="notice">
You can request an API key by emailing faaez.ulhaq@teneostrategy.com.
</aside>

<aside class="warning">If you're not using an API key, note that the server will return a 403 Forbidden error.</aside>

# Client

## Reputation Score


```shell
curl "http://dashapi.teneodigital.com:8080/rep_score?client_id=<XXXX>&"
  -H "Authorization: <API KEY>"
```

<aside class="warning">If you're not using an API key, note that the server will return a 403 Forbidden error.</aside>

> The above command returns JSON structured like this:

```json
[
{
"date": "2015-12-30T11:10:36+0000",
"social_score": "1.4",
"news_score": "3.6",
"cadence" : "daily",
"aggregate_score": "3.0"
},
{
"date": "2015-12-29T11:10:36+0000",
"social_score": "1.3",
"news_score": "4.5",
"cadence":"daily",
"aggregate_score": "2.6"
}
]
```

This endpoint retrieves the reputation scores available for the client specified by client_id.

### HTTP Request

`GET http://dashapi.teneodigital.com:8080/rep_score`

### GET Paramaters

Parameter | Sample Value | Description
--------- | ------- | -----------
client_id | acme | The unique identifier for the client that you're querying for, usually the company name.
start_date [optional - will default to earliest available]| "2015-10-30" | Start time of data being requested, in the format "YYYY-MM-DD"
end_date [optional - will default to latest available] | "2015-10-30" | End time of data being requested, in the format "YYYY-MM-DD"
cadence [optional - will default to "daily"] | "daily" | Cadence at which data is required - valid values: daily, weekly, monthly

### Response Paramaters

Parameter | Sample Value | Description
--------- | ------- | -----------
date | "2015-12-29T11:10:36+0000" | The date for the data point. In case of a non-daily cadence, this will be the midpoint of the period aggregated for. 
social_score| 1.3 | Social rep score
news_score | 3.4 | News rep score
cadence | "daily" | Cadence at which data was aggregated

## Global Issues

```shell
curl "http://dashapi.teneodigital.com:8080/global_issues?client_id=<XXXX>&"
  -H "Authorization: <API KEY>"
```

<aside class="warning">If you're not using an API key, note that the server will return a 403 Forbidden error.</aside>

> The above command returns JSON structured like this:

```json
[
{
"date": "2015-12-30T11:28:50+0000",
"cadence": "daily",
"social_issues":{
"Politics of Fifa":{"volume": 5600, "sentiment": "0.5"},
"Corruption and Bribery":{"volume": 3380, "sentiment": "4.1"},
"International Tournaments":{"volume": 2410, "sentiment": "4.5"},
"Sponsorship":{"volume": 9270, "sentiment": "2.6"}
},
"news_issues":{
"Politics of Fifa":{"volume": 5550, "sentiment": "2.8"},
"Corruption and Bribery":{"volume": 4550, "sentiment": "0.6"},
"International Tournaments":{"volume": 9860, "sentiment": "3.2"},
"Sponsorship":{"volume": 7010, "sentiment": "1.3"}
},
"aggregate_issues":{
"Politics of Fifa":{"volume": 11150, "sentiment": "1.6"},
"Corruption and Bribery":{"volume": 7930, "sentiment": "2.3"},
"International Tournaments":{"volume": 12270, "sentiment": "3.9"},
"Sponsorship":{"volume": 16280, "sentiment": "2.0"}
}
},
{
"date": "2015-12-29T11:28:50+0000",
"cadence": "daily",
"social_issues":{
"Politics of Fifa":{"volume": 6750, "sentiment": "0.4"},
"Corruption and Bribery":{"volume": 2470, "sentiment": "3.3"},
"International Tournaments":{"volume": 2030, "sentiment": "3.0"},
"Sponsorship":{"volume": 40, "sentiment": "0.5"}
},
"news_issues":{
"Politics of Fifa":{"volume": 9400, "sentiment": "2.3"},
"Corruption and Bribery":{"volume": 1070, "sentiment": "3.4"},
"International Tournaments":{"volume": 5820, "sentiment": "2.5"},
"Sponsorship":{"volume": 1970, "sentiment": "0.4"}
},
"aggregate_issues":{
"Politics of Fifa":{"volume": 16150, "sentiment": "1.3"},
"Corruption and Bribery":{"volume": 3540, "sentiment": "3.3"},
"International Tournaments":{"volume": 7850, "sentiment": "2.8"},
"Sponsorship":{"volume": 2010, "sentiment": "0.5"}
}
}
]
```

This endpoint retrieves the reputation scores available for the client specified by client_id.

### HTTP Request

`GET http://dashapi.teneodigital.com:8080/global_issues`

### GET Paramaters

Parameter | Sample Value | Description
--------- | ------- | -----------
client_id | acme | The unique identifier for the client that you're querying for, usually the company name.
start_date [optional - will default to earliest available]| "2015-10-30" | Start time of data being requested, in the format "YYYY-MM-DD"
end_date [optional - will default to latest available] | "2015-10-30" | End time of data being requested, in the format "YYYY-MM-DD"
cadence [optiona - will default to "daily"] | "daily" | Cadence at which data is required - valid values: daily, weekly, monthly

### Response Paramaters

Parameter | Sample Value | Description
--------- | ------- | -----------
date | "2015-12-29T11:10:36+0000" | The date for the data point. In case of a non-daily cadence, this will be the midpoint of the period aggregated for. 
cadence | "daily" | Cadence at which data was aggregated
social_issues| see right | Social issues
news_issues | see right | News issues
aggregate_issues | see right | Aggregate of social and news issues

## Influencers


```shell
curl "http://dashapi.teneodigital.com:8080/influencers?client_id=<XXXX>&"
  -H "Authorization: <API KEY>"
```

<aside class="warning">If you're not using an API key, note that the server will return a 403 Forbidden error.</aside>

> The above command returns JSON structured like this:

```json
[
{
"name": "Dummy Influencer",
"handle": "BarackObama",
"profile": "https://twitter.com/BarackObama",
"profile_img": "https://pbs.twimg.com/profile_images/451007105391022080/iu1f7brY.png",
"bio": "This account is run by Organizing for Action staff. Tweets from the President are signed -bo.",
"followers": "67700000",
"following": "639000",
"rank": 1
},
{
"name": "Dummy Influencer",
"handle": "BarackObama",
"profile": "https://twitter.com/BarackObama",
"profile_img": "https://pbs.twimg.com/profile_images/451007105391022080/iu1f7brY.png",
"bio": "This account is run by Organizing for Action staff. Tweets from the President are signed -bo.",
"followers": "67700000",
"following": "639000",
"rank": 2
}
]
```

This endpoint retrieves all the influencers for this client.

### HTTP Request

`GET http://dashapi.teneodigital.com:8080/influencers?client_id=<id>`

### GET Paramaters

Parameter | Sample Value | Description
--------- | ------- | -----------
client_id | acme | The unique identifier for the client that you're querying for, usually the company name.
start_date [optional - will default to earliest available]| "2015-10-30" | Start time of data being requested, in the format "YYYY-MM-DD"
end_date [optional - will default to latest available] | "2015-10-30" | End time of data being requested, in the format "YYYY-MM-DD"
### Response Parameters

### Response Parameters

Parameter | Sample Value | Description
--------- | ------- | -----------
name | "Barack Obama" | This value can be used to query the financial_data endpoint
handle | "BarackObama" | Twitter handle of the influencer
profile | "https://twitter.com/BarackObama" | Link to the profile of the influencer
profile_img | "https://pbs.twimg.com/profile_images/451007105391022080/iu1f7brY.png" | Link to the profile image of the influencer
bio | See right | Bio of the influencer
followers | 674000 | Number of followers
following | 674000 | Number of people the influencer follows
rank | 1 | Rank of the influencer in the period specified

