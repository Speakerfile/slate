---
title: Expertfile API v2 Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Authentication

## Oauth 2.0
> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://public-api.expertfile.com/v2/oauth/token"
  -X POST
```

> Make sure to replace `xxx-xxx-xxx` with your Access Token.

Expertfile expects for the Accesstoken to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer xxx-xxx-xxx`

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
grant_type | true | 
client_id | true | 
client_secret| true |

<aside class="notice">
 You can find you client_id and client_secret in account/api in your app dashboard. The url is https://app.expertfile.com/account/api 
</aside>

# Experts

## Get All Experts

```shell
curl "https://public-api.expertfile.com/v2/:corporation/organization/experts"
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "experts": [
      {
        "username": "myusername",
        "corporation": "mycorporation",
        "topics":[
          {
            "title": "topicname1"
          }, 
          {
            "title": "topicname2"
          }
        ],
        "tagline": "My tagline",
        "avatar": {
          "small": "my small avatar url",
          "medium": "my medium avatar url",
          "large": "my large avatar url",
          "original": "my original avatar url"
        }
      }
    ],
    "total": 12,
    "aggregations": {

    }
  },
  "success": true
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`

### Url Parameters

Parameter  | Desription
---------  | ----------
corporation  | The corporation id

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
q | - | search query.
access | public | This can be public or private.
page_size | 10 | no. of experts to return.
page_from | 0 | 
countries | - |
topics | - | 
industries | - |
companies | - |
fields | - |
sort | name | name or featured. 


## Get a Specific Expert

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/username"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "accomplishment":[
      {
        "id": 1,
        "title": "my accomplishment title",
        "description": "my accomplishment description",
        "start": 1349841600, //unix time
        "end": 1349841600, //unix time
        "type": 71
      },
      {
        "id": 2,
        "title": "my another accomplishment title",
        "description": "my another accomplishment description",
        "start": 1349841600, //unix time
        "end": 1349841600, //unix time
        "type": 71
      }
    ],
    "account": [
      {
        "id": 53,
        "firstname": "Firstname",
        "lastname": "lastname",
        "corporation_id": 767,
        "job_title": "my job title",
        "gener": 0,
        "location_city": "Toronto",
        "location_state": "ON",
        "location_country": "CA",
        "location_postal": "M5G 1L7",
        "location_address": "my address",
        "email": "myemail@example.com",
        "company": "my company name",
        "phone_number": "123-456-7890",
        "username": "peter.evans"
      }
    ],
    "affiliation": [
      {
        "id": 1,
        "name": "my affiliation name",
        "notes": "",
        "link": ""
      },{
        "id": 2,
        "name": "my another affiliation name",
        "notes": "",
        "link": ""
      }
    ],
    "article": [],
    "assessment": [],
    "availability": [
      {
        "availability_keynote": 1,
        "availability_moderator": 1,
        "availability_panelist": 1,
        "availability_workshop": 1,
        "availability_host_mc": 1,
        "availability_appearance": 0,
        "availability_corptraining": 1,
        "availability_open": 1
      }
    ],
    "book": [],
    "biography": [
      {
        "biography": "my biography"
      }
    ],
    "course": [],
    "corporationProfile": [
      {
        "id": 1,
        "name": "name",
        "user_name": "username",
        "description": "",
        "location_country": "CA",
        "location_state": "ON",
        "location_city": "Toronto",
        "location_postal": "M5G 1L7",
        "location_address": "address",
        "website": "myswebsite.com",
        "private_username": "xxx"
      }
    ],
    "corporationSocial": [
      {
        "twitter": "https://twitter.com/xyz",
        "facebook": "https://www.facebook.com/xyz",
        "linkedin": "http://www.linkedin.com/company/xyz",
        "gplus": "https://plus.google.com/+xyz/posts"
      }
    ],
    "eventAppearance": [
      {
        "id": 1,
        "title": "my event title ",
        "event_name": "my event name",
        "location": "Toronto",
        "date": 1362027600, // unix time
        "time_zone": "",
        "time": ""
      },{
        "id": 2,
        "title": "my another event title ",
        "event_name": "my another event name",
        "location": "Toronto",
        "date": 1362027600,
        "time_zone": "",
        "time": ""
      }
    ],
    "education": [
      {
        "id": 1,
			  "institution": "My Institution",
			  "degree": "My Degree",
			  "description": "",
			  "major": "My major",
			  "date": 1998
      },
      {
        "id": 2,
			  "institution": "My 2nd Institution",
			  "degree": "My 2nd Degree",
			  "description": "",
			  "major": "My 2nd major",
			  "date": 1998
      }
    ],
    "document": [
      {
        "id": 1,
        "title": "my 1st document",
        "url": "https://documenturl.com"
		  },
      {
        "id": 2,
        "title": "my 2nd document",
        "url": "https://documenturl.com/2"
      }
    ],
    "video": [
      {
        "id": 1,
			  "title": "my 1st video",
			  "url": "https://videourl.com"
      },
      {
        "id": 2,
			  "title": "my 2nd video",
			  "url": "https://videourl.com/1"
      }
    ],
    "language": [],
    "partnership": [],
    "industry": [
      {
        "name": "Indutry1",
        "id": "1"
      },
      {
        "name": "Industry2",
        "id": "2"
      }
    ],
    "patents": [],
    "news": [
      {
        "spotlight_title": "title ",
        "spotlight_text": "Test",
        "news_title": "title",
        "news_description": "Description",
        "news_date": 1411508121,
        "image_url": "imageurl.com",
        "news_id": 1
      },
      {
        "spotlight_title": "title 1",
        "spotlight_text": "Test 1",
        "news_title": "title 1",
        "news_description": "Description 1",
        "news_date": 1411508121,
        "image_url": "imageurl.com",
        "news_id": 2
      }
    ]
  },
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data" : {
    "id": 2,
    "deleted" : true
  },
  "success": true
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert to retrieve


#Link

##Get All Links
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link"
  -X GET
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "link name",
      "url": "http://www.example.com/",
    },
    {
      "id": 2,
      "name": "link name1",
      "url": "http://www.example.com/1",
    }
  ]
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts/:username/link`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert to retrieve


## Get a Specific Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/1"
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "link name",
      "url": "http://linkurl.com"
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific Link.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add a Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | true | name of the link 
url | true | the actual url 


## Update a Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/"
  -X PUT
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the link
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | optional | name of the link 
url | optional | the actual url 

## Delete a Specific Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific link.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the link
corporation | The corporation id
username | The username of the expert


#Sample Talk

##Get All Sample Talks
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "Description"
    },
    {
      "id": 2,
      "title": "Title",
      "description": "Description"
    }
  ],
  "success": true
}
```

This endpoint retrieves all Sample Talks.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Sample Talk

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/2"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title",
      "description": "description"
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific Sample Talk.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve
corporation | The corporation id
username | The username of the expert to retrieve

## Add a SampleTalk

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | true | title of the talk 
description | true | description of the talk 

## Update a SampleTalk

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/2"
  -X PUT
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id |  id of Sample Talk
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | optional | title of the talk 
description | optional | description of the talk 

## Delete a Specific Sample Talk


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific 

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the link to delete
corporation | The corporation id
username | The username of the expert

#Accomplishment

##Get All Accomplishment
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "my accomplishment title",
      "description": "my accomplishment description",
      "start": 1349841600, //unix time
      "end": 1349841600, //unix time
      "type": 71
    },
    {
      "id": 2,
      "title": "my another accomplishment title",
      "description": "my another accomplishment description",
      "start": 1349841600, //unix time
      "end": 1349841600, //unix time
      "type": 71
    }
  ],
  "success": true
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Accomplishment

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/2"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "my accomplishment title",
      "description": "my accomplishment description",
      "start": 1349841600, //unix time
      "end": 1349841600, //unix time
      "type": 71
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the sample talk to retrieve
corporation | The corporation id
username | The username of the expert to retrieve

## Add an Accomplishment

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | required | title of the talk 
description | required | description of the talk 
type | optional | Type of accomplishment. 71 for 'professional' and 73 for 'personal'
date | optional | date in unix time

##Update a specific accomplishment

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/2"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of accomplishment
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | optional | title of the talk 
description | optional | description of the talk 
type | optional | Type of accomplishment. 71 for 'professional' and 73 for 'personal'
date | optional | date in unix time

## Delete a Specific Accomplishment


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accompishment/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific accomplishment.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the accomplishment to delete
corporation | The corporation id
username | The username of the expert


#Affiliation

##Get All Affiliation
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "my affiliation name",
      "notes": "",
      "link": ""
    },{
      "id": 2,
      "name": "my another affiliation name",
      "notes": "",
      "link": ""
    }
  ],
  "success": true
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Affiliation

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/1"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "my affiliation name",
      "notes": "",
      "link": ""
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific affiliation.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the affiliation to retrieve
corporation | The corporation id
username | The username of the expert to retrieve

## Add an Affiliation

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | required | name of the affiliation

##Update an Affiliation

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/2"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | optional | name of the affiliation

## Delete a Specific affiliation


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accompishment/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific affiliation.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the affiliation to delete
corporation | The corporation id
username | The username of the expert

#Talk

##Get All Talk
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/talk"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Talk

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/talk/2"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/talk/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the talk to retrieve
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Accomplishment


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/talk/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific accomplishment.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/talk/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the talk to delete
corporation | The corporation id
username | The username of the expert

#Event Appearances

##Get All Event Appearances
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title 1",
      "event_name": "Event Name",
      "location": "Toronto",
      "date": 1362027600, //unix time
    },
    {
      "id": 2,
      "title": "title 2",
      "event_name": "Event Name 2",
      "location": "Toronto",
      "date": 1362028900, //unix time
    }
  ],
  "success": true
}
```

This endpoint retrieves all Event Apperances for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Event Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/1"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data":[
    {
      "id": 1,
      "title": "title 1",
      "event_name": "Event Name",
      "location": "Toronto",
      "date": 1362027600, //unix time
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific event appearance of an expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/1`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add an Event Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | required | title of the Event 
event_name | required | name of the event 
location | optional | name of the city/country where event took place
date | optional | date in unix time

##Update an Event Appearance


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/2"
  -X PUT
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | optional | title of the Event 
event_name | optional | name of the event 
location | optional | name of the city/country where event took place
date | optional | date in unix time

## Delete a Specific Event Appearance


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/1"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a Specific Event Appearance.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/:username/eventAppearance/2`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the Event Appearance to delete
corporation | The corporation id
username | The username of the expert

#Media Appearance

##Get All Media Appearance
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title 1",
      "organization": "organization 1",
      "type": "",
      "url": "",
      "details": "details",
      "date": 1497412800,
      "cover_url": "",
      "large_cover_url": "",
      "cover_alt_title": ""
    },
    {
      "id": 2,
      "title": "title 2",
      "organization": "organization 2",
      "type": "",
      "url": "",
      "details": "details",
      "date": 1497412800,
      "cover_url": "",
      "large_cover_url": "",
      "cover_alt_title": ""
    }
  ],
  "success": true
}
```

This endpoint retrieves all media appearances for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts/mediaAppearance`


## Get a Specific Media Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/1"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title 1",
      "organization": "organization 1",
      "type": "",
      "url": "",
      "details": "details",
      "date": 1497412800,
      "cover_url": "",
      "large_cover_url": "",
      "cover_alt_title": ""
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/1`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve


## Add a Media Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | required | title of the media appearance
organiztion | required | name of the organization 
details | required | details of the media appearance 
type | optional | this can be one of 'print', 'online', 'tv', 'radio'
url | optional | link to the media appearance
date | optional | date in unix time

##Update a Media Appearance
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/2"
  -X PUT
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | optional | title of the media appearance
organiztion | optional | name of the organization 
details | optional | details of the media appearance 
type | optional | this can be one of 'print', 'online', 'tv', 'radio'
url | optional | link to the media appearance
date | optional | date in unix time

## Delete a Specific Media Appearance


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a Specific Media Appearance.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the Media Appearance to delete
corporation | The corporation id
username | The username of the expert

#Education

##Get All Education
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "institution": "My Institution",
      "degree": "My Degree",
      "description": "",
      "major": "My major",
      "date": 1998 // year 
    },
    {
      "id": 2,
      "institution": "My 2nd Institution",
      "degree": "My 2nd Degree",
      "description": "",
      "major": "My 2nd major",
      "date": 1998
    }
  ],
  "success": true
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts/:username/education`


## Get a Specific Education

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/1"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "institution": "My Institution",
      "degree": "My Degree",
      "description": "",
      "major": "My major",
      "date": 1998
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Education

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
institution | required | name of the instituion
degree | required | degree obtained.
major | optional | Level of study. Bachelors/Masters/Phd
description | optional | additional information for the degree
date | optional | year of graduation. Enter '1998' if graduation year is 1998

## Update an Education 

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
institution | optional | name of the instituion
degree | optional | degree obtained.
major | optional | Level of study. Bachelors/Masters/Phd
description | optional | additional information for the degree
date | optional | year of graduation. Enter '1998' if graduation year is 1998


## Delete a Specific Education


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific education.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the Education to delete
corporation | The corporation id
username | The username of the expert

#Testimonial

##Get All Testimonial
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "name",
      "title": "title",
      "email": "",
      "company": "company",
      "url": "https://url.com",
      "recommendation": "my amazing recommendation",
      "date": null
    },
    {
      "id": 2,
      "name": "name",
      "title": "title",
      "email": "",
      "company": "company",
      "url": "https://url.com",
      "recommendation": "my 2nd amazing recommendation",
      "date": null
    }
  ],
  "success": true
}
```

This endpoint retrieves all reccomendations for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`



## Get a Specific Testimonial

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/1"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data":[
    {
      "id": 1,
      "name": "name",
      "title": "title",
      "email": "",
      "company": "company",
      "url": "https://url.com", //company url
      "recommendation": "my amazing recommendation",
      "date": null
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/1`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Testimonial

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | required | name of the person
title | required | job title of the person
company | required | company of the person
recommendation | required | recommendation note
url | optional | url of the company where person works

## Update a Testimonial

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/2"
  -X PUT
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | optional | name of the person
title | optional | job title of the person
company | optional | company of the person
recommendation | optional | recommendation note
url | optional | url of the company where person works


## Delete a Specific Testimonial


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint retrieves a specific testimonial.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the testimonial to delete
corporation | The corporation id
username | The username of the expert

#Patent

##Get All Patent
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json

{
  "data": [
    {
      "id": 1,
      "title": "Title1",
      "detail": "detail1",
      "number": "100789",
      "date": 1499140800,
      "url": "http://www.example.com"
    },
    {
      "id": 2,
      "title": "Title2",
      "detail": "detail2",
      "number": "100789",
      "date": 1499140800,
      "url": "http://www.example.com"
    }
  ],
  "success": true
}

```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Patent

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/1"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [{
      "id": 1,
      "title": "Title1",
      "detail": "detail1",
      "number": "100789",
      "date": 1499140800,
      "url": "http://www.example.com"
  }],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/1`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Patent

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
number | required | patent number
title | required | title of the patent
detail | required | description of the patent
date | optional | date of the patent granted in unix time
url | optional | url of the patent

##Update a Patent

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/2"
  -X PUT
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
number | optional | patent number
title | optional | title of the patent
detail | optional | description of the patent
date | optional | date of the patent granted in unix time
url | optional | url of the patent

## Delete a Specific Patent


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint retrieves a specific Patent.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/2`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the patent to delete
corporation | The corporation id
username | The username of the expert

#Research Grant

##Get All Reseach Grant
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title1",
      "organization": "organization1",
      "url": "http://www.example.com",
      "details": "detail1",
      "date": 1499140800,
      "amount": "100"
    },
    {
      "id": 2,
      "title": "title1",
      "organization": "organization2",
      "url": "http://www.example.com",
      "details": "detail2",
      "date": 1499140800,
      "amount": "100"
    }
  ]
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Research grant

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/2"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title1",
      "organization": "organization1",
      "url": "http://www.example.com",
      "details": "detail1",
      "date": 1499140800,
      "amount": "100"
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Research Grant

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
organization | required | organization to give grant
title | required | title of the grant
detail | required | description of the grant
date | optional | date in unix time
url | optional | url
amount | optional | amount granted

##Update a Research Grant

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/2"
  -X PUT
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
organization | optional | organization to give grant
title | optional | title of the grant
detail | optional | description of the grant
date | optional | date in unix time
url | optional | url
amount | optional | amount granted

## Delete a Specific Research Grant


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific research grant.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the link to research grant
corporation | The corporation id
username | The username of the expert

#Partnerships

##Get All partnerships
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership"
  -X GET
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title1",
      "individual": "partner name1",
      "organization": "organization",
      "url": "http://www.example.com",
      "details": "detail1",
      "date": 1499140800
    },
    {
      "id": 2,
      "title": "title2",
      "individual": "partner name",
      "organization": "organization",
      "url": "http://www.example.com",
      "details": "detail1",
      "date": 1499140800
    }
  ],
  "success": true
}
```

This endpoint retrieves all partnerships for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Partnership

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/1"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title1",
      "individual": "partner name1",
      "organization": "organization",
      "url": "http://www.example.com",
      "details": "detail1",
      "date": 1499140800
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific partnership for an expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the Partnership to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Partnership

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | required | partnership title
name | required | partner name
details | required | description of the partnership
date | optional | date in unix time
url | optional | url
organization | optional | organization

##Update a Partnership

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/2"
  -X PUT
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | optional | partnership title
name | optional | partner name
details | optional | description of the partnership
date | optional | date in unix time
url | optional | url
organization | optional | organization


## Delete a Specific Partnership


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific partnership.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the Partnership to delete
corporation | The corporation id
username | The username of the expert to retrieve

#Courses

##Get All Courses
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "course title",
      "details": "course detail",
      "url": "http://www.example.com"
    },
    {
      "id": 2,
      "title": "course title2",
      "details": "course detail2",
      "url": "http://www.example2.com"
    }
  ],
  "success": true
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Course

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/2"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "course title",
      "details": "course detail",
      "url": "http://www.example.com"
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Course

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | required | course title
details | required | description/details of the course
url | optional | url

##Update a Specific Course

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/2"
  -X PUT
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "updated": true
  },
  "success": true
}
```

This endpoint updates a specific link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/2`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | optional | course title
details | optional | description/details of the course
url | optional | url

## Delete a Specific Course


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific course.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the course to delete
corporation | The corporation id
username | The username of the expert to retrieve

#Articles

##Get All Articles
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "article title",
      "publisher": "article publication",
      "details": "article detail",
      "date": 1499140800,
      "url": "http://www.example.com",
      "authors": "author"
    },
    {
      "id": 2,
      "title": "article title2",
      "publisher": "article publication2",
      "details": "article detail2",
      "date": 1499140800,
      "url": "http://www.example2.com",
      "authors": "author2"
    }
  ],
  "success": true
}
```

This endpoint retrieves all articles for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Article

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/2"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "article title",
      "publisher": "article publication",
      "details": "article detail",
      "date": 1499140800,
      "url": "http://www.example.com",
      "authors": "author"
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Article

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | required | course title
publisher | required | publisher name
details | required | description/details of the course
url | optional | url
authors | optional | co-authors
url | optional | link to the article

##Update a Artcile

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/2"
  -X PUT
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "updated": true
  },
  "success": true
}
```

This endpoint updates a specific article for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | optional | course title
publisher | optional | publisher name
details | optional | description/details of the course
url | optional | url
authors | optional | co-authors
url | optional | link to the article

## Delete a Specific Article


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "deleted": true
  },
  "success": true
}
```

This endpoint deletes a specific article.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the article to delete
corporation | The corporation id
username | The username of the expert to retrieve

#Research Focus

##Get All Research Focus
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus"
  -X GET
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "focus 1",
      "subtitle": "sub title",
      "details": "details 1",
      "date": null,
      "url": "",
      "cover_url": "exampleurl.com",
      "large_cover_url": "exampleurl.com",
      "cover_alt_title": null
    },
    {
      "id": 2,
      "title": "focus 2",
      "subtitle": "sub title",
      "details": "details 2",
      "date": null,
      "url": "",
      "cover_url": "exampleurl.com",
      "large_cover_url": "exampleurl.com",
      "cover_alt_title": null
    }
  ],
  "success": true
}
```

This endpoint retrieves all research focus for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Research Focus

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/2"
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "focus 1",
      "subtitle": "sub title",
      "details": "details 1",
      "date": null,
      "url": "",
      "cover_url": "exampleurl.com",
      "large_cover_url": "exampleurl.com",
      "cover_alt_title": null
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific kitten.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the research focus to retrieve
corporation | The corporation id
username | The username of the expert to retrieve

## Add Research Focus

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a research focus for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | required | course title
details | required | description/details of the course
url | optional | url
date | optional | date in unix format
subtitle | optional | 

##Update a Research Focus


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/"
  -X PUT
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "updated": true
  },
  "success": true
}
```

This endpoint updates a specific research focus for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | optional | course title
details | optional | description/details of the course
url | optional | url
date | optional | date in unix format
subtitle | optional | 

## Delete a Specific Research Focus


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted" : true
  },
  "success": true
  }
}
```

This endpoint deletes a specific research focus.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the research focus to delete
corporation | The corporation id
username | The username of the expert to retrieve

#Topics

##Get All Topics
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "topic 1"
    },
    {
      "id": 2,
      "name": "topic 2"
    }
  ],
  "success": true
}
```

This endpoint retrieves all Topics for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Topic

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/2"
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {
      "id": 1,
      "name": "topic 1"
     }
  ],
  "success": true
}
```

This endpoint retrieves a specific Topic for an expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the topic to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Topic

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | required | topic name


## Update Topic

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/2"
  -X PUT
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "updated": true
  },
  "success": true
}
```

This endpoint updates a specific topic.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | optional | topic name

## Delete a Specific Topic


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted" : true
  },
  "success": true
}
```

This endpoint deletes a specific topic for an expert.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the topic to delete
corporation | The corporation id
username | The username of the expert to retrieve

#Industry

##Get All Industry
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Industry 1"
    },
    {
      "id": 2,
      "name": "Industry 2"
    }
  ],
  "success": true
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Industry

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/1"
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Industry 1"
    }
  ]
}
```

This endpoint retrieves a specific Industry for an expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/1`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the industry to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve.

## Add Industry

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | required | Industry name

##Update Industry

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/2"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | optional | Industry name


## Delete a Specific Insutry

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/2"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data" : {
    "id": 2,
    "deleted" : true
  },
  "success": true
}
```

This endpoint deletes a specific Industry.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the industry to delete
corporation | The corporation id
username | The username of the expert to retrieve

#Languages

##Get All languages
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Language1"
    },
    {
      "id": 2,
      "name": "Language2"
    }
  ],
  "success": true
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Get a Specific Languages

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/1"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Language1"
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific language belonging to the expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the language to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Add Language

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | required | langauge name


##Update a Language

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/2"
  -X PUT
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2,
    "updated": true
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
name | optional | langauge name

## Delete a Specific Language

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "deleted" : true
  },
  "success": true
}
```

This endpoint deletes a specific language for an expert.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | id of the research focus to delete
corporation | The corporation id
username | The username of the expert to retrieve

#Fees

##Get All fees
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fees"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "fee_min": 100,
      "fee_max": 1000
    }
  ],
  "success": true
}
```

This endpoint retrieves fees for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts`


## Add fees

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fees/"
  -X POST
  -H "Authorization: xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fees/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
fee_minx | required | min fees
fee_max | required | max fees

#Availability

##Get availability
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/availability"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "availability_keynote": 1,
      "availability_moderator": 1,
      "availability_panelist": 1,
      "availability_workshop": 1,
      "availability_host_mc": 1,
      "availability_appearance": 0,
      "availability_corptraining": 1,
      "availability_open": 1
    }
  ],
  "success": true
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts/:username/availability`


#Social

##Get All Social
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/social"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "twitter": "http://www.twitter.com/techmarketer",
      "facebook": "",
      "linkedin": "http://ca.linkedin.com/in/peterevansprofile",
      "gplus": "",
      "stackexchange": "",
      "github": "",
      "flickr": "",
      "pinterest": "",
      "instagram": "",
      "tumblr": "",
      "youtube": ""
    }
  ],
  "success": true
}
```

This endpoint retrieves link for social profiles for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/social`


## Add social

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/social/"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "id" : 2
  },
  "success": true
}
```

This endpoint adds a link for expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
title | required | course title
details | required | description/details of the course
url | optional | url


#Youtube

##Get All Youtube Media
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/youtube"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "description",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null
    },
    {
      "id": 2,
      "title": "Title 2",
      "description": "description 2",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null 
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/social`


##Get a Specific youtube media

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/youtube/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "description",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/youtube/:id`



#Vimeo

##Get All Youtube Media
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/vimeo"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Video title",
      "description": "",
      "url": "http://vimeo.com/1",
      "external_id": "1", //vimeo video id. 
      "thumbnail_small": "http://i.vimeocdn.com/video/1.jpg",
      "thumbnail_alt_title": null
    },
    {
      "id": 2,
      "title": "Video title",
      "description": "",
      "url": "http://vimeo.com/1",
      "external_id": "2",
      "thumbnail_small": "http://i.vimeocdn.com/video/1.jpg",
      "thumbnail_alt_title": null
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/social`


##Get a Specific youtube media

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/vimeo/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Video title",
      "description": "",
      "url": "http://vimeo.com/1",
      "external_id": "1", //vimeo video id. 
      "thumbnail_small": "http://i.vimeocdn.com/video/1.jpg",
      "thumbnail_alt_title": null
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/vimeo/:id`


#Slideshare

##Get All Youtube Media
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/slideshare"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title 1",
      "description": "",
      "url": "slideshare url",
      "embed": "slideshare embed url",
      "thumbnail_url": "thumbnail url",
      "external_id": "1"// slideshare docuement id
    },
    {
      "id": 2,
      "title": "title 2",
      "description": "",
      "url": "slideshare url",
      "embed": "slideshare embed url",
      "thumbnail_url": "thumbnail url",
      "external_id": "1"// slideshare docuement id
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/social`


##Get a Specific slideshare media

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/slideshare/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "title 1",
      "description": "",
      "url": "slideshare url",
      "embed": "slideshare embed url",
      "thumbnail_url": "thumbnail url",
      "external_id": "1"// slideshare docuement id
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/slideshare/:id`


#Documents

##Get All Document Media
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/document"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "description",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null
    },
    {
      "id": 2,
      "title": "Title 2",
      "description": "description 2",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null 
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/social`


##Get a Specific document

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/document/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "description",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/document/:id`




#Photo

##Get All Photos
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/photo"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "description",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null
    },
    {
      "id": 2,
      "title": "Title 2",
      "description": "description 2",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null 
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/social`


##Get a Specific Photo
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/photo/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "description",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/photo/:id`



#Video

##Get All Videos (Uploaded)
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/video"
  -X DELETE
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "description",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null
    },
    {
      "id": 2,
      "title": "Title 2",
      "description": "description 2",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null 
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/social`


##Get a Specific Video (Uploaded)

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/video/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "title": "Title",
      "description": "description",
      "watch_page_url": "watch page url",
      "thumbnail_url": "thumbnail url",
      "flash_player_url": "flashplayerurl",
      "video_id": "video id",
      "thumbnail_alt_title": null
    }
  ],
  "success": true
}
```

This endpoint retrieves all youtube media for an Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/video/:id`


