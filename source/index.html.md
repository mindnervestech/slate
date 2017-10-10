---
title: Contextgrid API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - :http

<!-- toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a> -->

includes:
  - errors

search: true
---

# Introduction

Welcome to the Contextgrid API! You can use our API to access Contextgrid API endpoints, which can get information on  beacons in our database.

We have language bindings in http. You can view code examples in the dark area to the right.

# Authentication

> To authorize, use this code:



```python
# With http, you can just pass the correct header with each request
http://"api_endpoint_here"
  -H "X-AUTH-TOKEN: yourAuthToken"
```





> Make sure to replace `yourAuthToken` with your Auth Token key.

Contextgrid uses Token keys to allow access to the API. 

Contextgrid expects for the Token key to be included in all API requests to the server in a header that looks like the following:

`X-AUTH-TOKEN: eyJhbGciOiJIUzUxMiJ9.eyJwZXJtaXNzaW9ucyI6IltdIiwic3ViamVjdCI6ImFua2l0QGdtYWlsLmNvbWNvbXBhbnlPd25lciIsInJvbGVzIjoiW2NvbXBhbnlPd25lcl0ifQ.qWorUEDE5_ZWdBuded-U_OOhNWeymspy6xJ2ogXfM3GW6d9rW2_8J992y5fN71Rj17JgkmFe-PbwdgDqOL95CA`





# Beacons

## Get All Places



```python
GET  https://app.contextgrid.com/api/place/beacons?longitude=-74.0441844&latitude=40.7139937&apiKey=yourAppApiKey

Headers
X-AUTH-TOKEN: xAuthToken

Response
{
    "status": "200",
    "data": [
        {
            "placeName": "Surf City",
            "latitude": "40.7117978",
            "longitude": "-74.0432427",
            "beaconCount": 1,
            "placeId": "69fb9f18-6c79-49c4-b980-1c65bcb66ff2",
            "companyName": "Gmail",
            "address": "building no. 1, 1 Marin Blvd, Jersey City, New Jersey, USA, Post Code:07302"
        },
        {
            "placeName": "Marin Dry Cleaners",
            "latitude": "40.7149132",
            "longitude": "-74.043346",
            "beaconCount": 1,
            "placeId": "747b6f14-f1fe-496c-a25e-56b518de6b94",
            "companyName": "Gmail",
            "address": "201 Marin Blvd, Jersey City, New Jersey, USA, Post Code:07302"
        },
        {
            "placeName": "Airport 18 park",
            "latitude": "40.7139937",
            "longitude": "-74.0441844",
            "beaconCount": 4,
            "placeId": "6de3ef9f-9baf-490c-a7ce-8360a1aee65d",
            "companyName": "Gmail",
            "address": "building no. 18, 18 Park Ave, Apt 316, Jersey City, New Jersey, United States, Post Code:07302"
        }
    ]
}
```


This endpoint retrieves all places from given location.

### HTTP Request

`GET https://app.contextgrid.com/api/place/beacons`

### Query Parameters

Parameter |  Description
--------- |  -----------
longitude |  longitude of location where you want search places.
latitude |  latitude of location where you want search places.
apiKey |  apiKey of your app.

<aside class="success">
Remember — your apiKey of your app should be valid
</aside>

## Get beacons by place



```python
GET https://app.contextgrid.com/api/beacons/byPlace/6de3ef9f-9baf-490c-a7ce-8360a1aee65d/yourAppApiKey

Headers
X-AUTH-TOKEN: xAuthToken

Response
{
    "status": "200",
    "data": [
        {
            "id": "128b7bdc-03e6-42de-bc24-da4222644610",
            "beaconType": "iBeacon",
            "uuid": "B9407F30-F5F8-466E-AFF9-25556B57FE6D",
            "major": 53001,
            "minor": 51064,
            "microLoaction": "Security Room",
            "placeName": "Airport 18 park",
            "companyName": "Gmail",
            "latitude": "40.713884",
            "longitude": "-74.045034"
        }
    ]
}
```





This endpoint retrieves beacons belonging to place.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://app.contextgrid.com/api/beacons/byPlace/<PlaceId>/<AppApiKey>`

### URL Parameters

Parameter | Description
--------- | -----------
PlaceId | place id of given place
AppApiKey |  apiKey of your app.


## Get beacons by place (extended)



```python
GET https://app.contextgrid.com/api/allBeacons/byPlace/6de3ef9f-9baf-490c-a7ce-8360a1aee65d/yourAppApiKey

Headers
X-AUTH-TOKEN: xAuthToken

Response
{
    "status": "200",
    "data": [
        {
            "id": "128b7bdc-03e6-42de-bc24-da4222644610",
            "major": 53001,
            "minor": 51064,
            "beaconType": "iBeacon",
            "uuid": "B9407F30-F5F8-466E-AFF9-25556B57FE6D",
            "mataListName": "Room Actions",
            "metalist": [
                {
                    "key": "Who is in",
                    "value": "https://app.contextgrid.com/beacon/api/peopleCount/128b7bdc-03e6-42de-bc24-da4222644610/CE40B5BB4D793B18A9B87CCCFBF9F608"
                }
            ],
            "microLocation": "Security Room",
            "placeName": "Airport 18 park",
            "companyName": "Gmail",
            "cgId": "CG_BEC_0000050",
            "imageUrl": "http://52.1.88.195:8089/user/comapny/profile/id/f406fdbe-9213-4ccf-8f60-682fc7a68bc3",
            "notificationName": "Test",
            "notificationUrl": "test",
            "notificationFrequency": "Disabled",
            "notificationMessage": "test"
        }
    ]
}
```





This endpoint retrieves beacons with action list value (metadata) belonging to given place.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://app.contextgrid.com/api/allBeacons/byPlace/<PlaceId>/<AppApiKey>`

### URL Parameters

Parameter | Description
--------- | -----------
PlaceId | place id of given place
AppApiKey |  apiKey of your app.

## Get beacons by id



```python
GET https://app.contextgrid.com/api/beacon/byid/128b7bdc-03e6-42de-bc24-da4222644610/yourAppApiKey

Headers
X-AUTH-TOKEN: xAuthToken

Response
{
    "status": "200",
    "data": {
        "id": "128b7bdc-03e6-42de-bc24-da4222644610",
        "major": 53001,
        "minor": 51064,
        "beaconType": "iBeacon",
        "uuid": "B9407F30-F5F8-466E-AFF9-25556B57FE6D",
        "mataListName": "Room Actions",
        "metalist": [
            {
                "key": "Who is in",
                "value": "https://app.contextgrid.com/beacon/api/peopleCount/128b7bdc-03e6-42de-bc24-da4222644610/CE40B5BB4D793B18A9B87CCCFBF9F608"
            }
        ],
        "microLocation": "Security Room",
        "placeName": "Airport 18 park",
        "companyName": "Gmail",
        "cgId": "CG_BEC_0000050",
        "imageUrl": "http://52.1.88.195:8089/user/comapny/profile/id/f406fdbe-9213-4ccf-8f60-682fc7a68bc3",
        "notificationName": "Test",
        "notificationUrl": "test",
        "notificationFrequency": "Disabled",
        "notificationMessage": "test"
    }
}
```





This endpoint retrieves beacon information of given id.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://app.contextgrid.com/api/beacon/byid/<BeaconId>/<AppApiKey>`

### URL Parameters

Parameter | Description
--------- | -----------
BeaconId | id of beacon
AppApiKey |  apiKey of your app.

## Get beacons by major,minor,uuid



```python
GET https://app.contextgrid.com/api/beacon/getBy/B9407F30-F5F8-466E-AFF9-25556B57FE6D/53001/51064/gmail/yourAppApiKey


Headers
X-AUTH-TOKEN: xAuthToken

Response
{
    "status": "200",
    "data": {
        "id": "128b7bdc-03e6-42de-bc24-da4222644610",
        "major": 53001,
        "minor": 51064,
        "beaconType": "iBeacon",
        "uuid": "B9407F30-F5F8-466E-AFF9-25556B57FE6D",
        "mataListName": "Room Actions",
        "metalist": [
            {
                "key": "Who is in",
                "value": "https://app.contextgrid.com/beacon/api/peopleCount/128b7bdc-03e6-42de-bc24-da4222644610/CE40B5BB4D793B18A9B87CCCFBF9F608"
            }
        ],
        "microLocation": "Security Room",
        "placeName": "Airport 18 park",
        "companyName": "Gmail",
        "cgId": "CG_BEC_0000050",
        "imageUrl": "http://52.1.88.195:8089/user/comapny/profile/id/f406fdbe-9213-4ccf-8f60-682fc7a68bc3",
        "notificationName": "Test",
        "notificationUrl": "test",
        "notificationFrequency": "Disabled",
        "notificationMessage": "test"
    }
}
```





This endpoint retrieves beacon information of given major,minor,uuid.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

GET https://app.contextgrid.com/api/beacon/getBy/<UUID>/<Major>/<Minor>/<DomainName>/<AppApiKey>

### URL Parameters

Parameter | Description
--------- | -----------
UUID | uuid (Proximity_UUID) of beacon
Major | major of beacon
Minor | minor of beacon
DomainName | domain name of your company
AppApiKey |  apiKey of your app.

## Get all beacons by domain name



```python
GET https://app.contextgrid.com/api/beacons/all/gmail/yourCompanyApiKey



Headers
X-AUTH-TOKEN: xAuthToken

Response
{
    "status": "200",
    "data": [
        {
            "id": "8e0dd0fe-5957-488b-9506-17758bbcccc9",
            "cgId": "CG_BEC_0000074",
            "proxiUid": "uuid4011",
            "major": 45,
            "minor": 4,
            "orgName": "f406fdbe-9213-4ccf-8f60-682fc7a68bc3",
            "actionUrl": null,
            "beaconType": 1,
            "uidFrame": null,
            "broadcast": null,
            "namespaceId": null,
            "instanceId": null,
            "broadcastUrl": null,
            "userId": 1,
            "placeId": "69fb9f18-6c79-49c4-b980-1c65bcb66ff2",
            "latitude": "15.497242",
            "longitude": "73.825135",
            "actionList": [
                {
                    "key": "Spa Mother's Day",
                    "value": "https://www.spa810.com/weehawken/membership/"
                }
            ],
            "actionListId": null,
            "accessLevel": "public",
            "microLocation": "Bar Entrance",
            "notificationName": "1f07f2a7-d4c0-4d7b-8fd2-b086fd57be79",
            "notificationUrl": null,
            "notificationFrequency": null,
            "notificationMessage": null
        }
    ]
}
```





This endpoint retrieves beacon information of given major,minor,uuid.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

GET https://app.contextgrid.com/api/beacons/all/<DomainName>/<CompanyApiKey>

### URL Parameters

Parameter | Description
--------- | -----------
DomainName | domain name of your company
CompanyApiKey |  companyApiKey of your app.



