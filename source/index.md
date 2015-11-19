---
title: Teneo EWS API Reference

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

This is the proposed API for Teneo EWS. Feel free to give us feedback or request changes. 

# Authentication

All api requests need to be authorized with an API key, without which, an error will be returned. 

<aside class="notice">
You can request an API key by emailing faaez.ulhaq@teneostrategy.com.
</aside>

<aside class="warning">If you're not using an API key, note that the server will return a 403 Forbidden error.</aside>
# Companies

## Get All Companies


```shell
curl "http://ewsapi.teneodigital.com/companies"
  -H "Authorization: <API KEY>"
```

<aside class="warning">If you're not using an API key, note that the server will return a 403 Forbidden error.</aside>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "ticker": "NYSE:AAPL",
    "name": "Apple, Inc.",
    "risk": 0.1
  },
  {
    "id": 2,
    "ticker": "NYSE:IBM",
    "name": "International Business Machines",
    "risk": 0.3
  }
]
```

This endpoint retrieves all companies to be displayed in the dashboard.

### HTTP Request

`GET http://ewsapi.teneodigital.com/companies`

### Response Paramaters

Parameter | Sample Value | Description
--------- | ------- | -----------
id | 1 | The unique identifier for the company, that will not change
ticker | "NYSE:AAPL" | The company's ticker
name | "Apple, Inc." | The company's name
risk | 0.1 | a decimal value between 0.0 and 1.0, where 0.0 is low risk and 1.0 is high risk


## Get a Specific Company

```shell
curl "http://ewsapi.teneodigital.com/company?id=2"
  -H "Authorization: <API KEY>"
```

> The above command returns JSON structured like this:

```json
{
    "id": 2,
    "ticker": "NYSE:IBM",
    "name": "International Business Machines",
    "risk": 0.3,
    "industry" : "Information Technology Services",
    "comps" : [ 
        1,
        3,
        4
    ],
    "iss_data" : {
        "AuditRank" : "2",
        "companyid" : "77251",
        "MeetingDate_Latest" : "Apr 28 2015 10:00AM",
        "NumDircOverBoarded" : "0",
        "MedianNEDPay" : "307980",
        "NumWomanOnBoard" : "3",
        "ShrdPropMoreThan40PctYN" : "No",
        "NumPartyTrans" : "0",
        "ResignationReq" : "Bylaws-Charter",
        "MajorityVoteRequirement" : "By-laws",
        "PTA" : "22",
        "MSOP_AgainstRate" : "6.4",
        "CompensationRank" : "7",
        "NumMinority" : "2",
        "DirAgeOver72" : "0",
        "ResponseToOutsVoteYN" : "Yes",
        "NumEthnicUnknown" : "0",
        "BoardRank" : "4",
        "RDA" : "-31",
        "ShareholderRank" : "3",
        "AvgDirAge" : "64",
        "NumDirWithPartyTrans" : "0",
        "DirRecMoreThan10PctAgainst" : "0",
        "ResponseToCastVoteYN" : "Yes",
        "NumNEDMedianPayCalc" : "12",
        "QSUpdateDate" : "Mar 27 2015  2:15PM",
        "MOM" : "1.03",
        "OverallQSRank" : "5"
    },
    "company_url" : "http://www.ibm.com",
    "profile" : "International Business Machines Corp is an Information Technology (IT) company. It creates business value for clients and solves business problems through integrated solutions that leverage information technology & knowledge of business processes.",
    "risk_history" : {
        "2015-05-08T00:00:00.000Z": 0.1, 
        "2015-05-07T00:00:00.000Z": 0.1, 
        "2015-05-06T00:00:00.000Z": 0.1, 
        "2015-05-05T00:00:00.000Z": 0.1, 
        "2015-05-04T00:00:00.000Z": 0.1, 
        "2015-05-01T00:00:00.000Z": 0.1, 
        "2015-04-30T00:00:00.000Z": 0.1, 
        "2015-04-29T00:00:00.000Z": 0.1, 
        "2015-04-28T00:00:00.000Z": 0.1, 
        "2015-04-27T00:00:00.000Z": 0.1, 
        "2015-05-20T00:00:00.000Z": 0.1, 
        "2015-05-19T00:00:00.000Z": 0.1, 
        "2015-05-18T00:00:00.000Z": 0.1, 
        "2015-05-15T00:00:00.000Z": 0.7, 
        "2015-05-14T00:00:00.000Z": 0.7, 
        "2015-05-13T00:00:00.000Z": 0.7, 
        "2015-05-12T00:00:00.000Z": 0.7, 
        "2015-05-11T00:00:00.000Z": 0.7, 
        "2015-05-08T00:00:00.000Z": 0.7, 
        "2015-05-07T00:00:00.000Z": 0.7, 
        "2015-05-26T00:00:00.000Z": 0.7, 
        "2015-05-26T00:00:00.000Z": 0.7, 
        "2015-05-26T00:00:00.000Z": 0.7, 
        "2015-05-26T00:00:00.000Z": 0.7, 
        "2015-05-26T00:00:00.000Z": 0.7, 
        "2015-05-26T00:00:00.000Z": 0.7
    },
    "indexname" : "S&P 500"
}
```

This endpoint retrieves a specific company.

<aside class="warning">If you're not using an API key, note that the server will return a 403 Forbidden error.</aside>

### HTTP Request

`GET http://ewsapi.teneodigital.com/company?id=<id>`

### GET Parameters

Parameter | Description 
--------- | -----------
id | The id of the company 

### Response Parameters

Parameter | Description 
--------- | -----------
id | The id of the company 
ticker | Ticker of the company
name | Name of the company
risk | A decimal value between 0.0 and 1.0, where 0.0 is low risk and 1.0 is high risk
industry | The industry this company belongs to
comps | An array of company ids, where each one corresponds to a 'comparable' or 'peer' of this company
iss_data | A dictionary of governance-related ISS data
company_url | URL of the company's website
profile | A text profile of the company
risk_history | A dictionary that gives the risk trejectory of this company
indexname | Name of the index this company belongs to, e.g., "S&P 500"

## Get a company's financial data

### HTTP Request

`GET http://ewsapi.teneodigital.com/financial_data?id=<id>&data_type=<data_type>`

### GET Parameters

Parameter | Description 
--------- | -----------
id | The id of the company 
data_type | Data type being queried. See below for available data types. 
start_time <optional - will default to earliest available>| Start time of data being requested, in the format "YYYY-MM-DD", e.g., "2015-10-30"
end_time <optional - will default to latest available> | End time of data being requested, in the format "YYYY-MM-DD", e.g., "2015-10-30"

### Data types available

Data type | Description 
--------- | -----------
price | Price of stock
one_month_total_return | 1 Month Total Shareholder Return
three_month_total_return | 3 Month Total Shareholder Return 
ten_month_total_return | 10 Month Total Shareholder Return 
one_year_total_return | 1 Year Total Shareholder Return
three_year_total_return | 3 Year Total Shareholder Return
