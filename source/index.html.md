---
title: Expertfile API v2 Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

search: false
---

# Authentication

## Oauth 2.0
> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl -X POST \
  https://public-api.expertfile.com/v2/oauth/token \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/x-www-form-urlencoded' \
  -d 'client_id=<YOUR_ID>&client_secret=<YOUR_SECRET>&grant_type=client_credentials'

```

> Make sure to add you client ID and client secret.

Expertfile expects an access token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer xxx-xxx-xxx`

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`grant_type` | true |  __string__ enter client_credentials
`client_id` | true | __string__  your organization client id
`client_secret`| true | __string__  your organization client secret

<aside class="notice">
 You can find you client_id and client_secret in account/api in your app dashboard. The url is https://app.expertfile.com/account/api 
</aside>


# Experts

## Get All Experts

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert"
  -X GET
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

This endpoint retrieves all Experts.

To retreive the original photo uploaded to ExpertFile, access "avatar.original".

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert`

### Url Parameters

Parameter  | Desription
---------  | ----------
`corporation`  | __integer__The corporation id

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`q` | - | __string__search query.
`access` | public | __string__This can be public, private or all.
`status` | all | __string__This can be published, unpublished or all.
`page_size` | 10 | __integer__no. of experts to return.
`page_from` | 0 | __integer__
`countries` | all | __string__array of countries(i.e. ["CA","US"])
`topics` | all | __string__array of topics(i.e. ["topic1","topic2"])
`industries` | all | __string__array of industries(i.e. ["industry1","industry2"])
`category` | all | __string__array of categories(i.e. ["cat1","cat2"])
`tag` | all | __string__array of tags(i.e. ["tag1","tag2"])
`companies` | all | __string__
`fields` | - | __string__
`sort` | name | __string__ name or featured.  
`searchfield` | - | __string__ fullname to query only name field. 

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
        "url": "https://documenturl.com/:id"
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
This endpoint retrieves a specific Expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

##Add an Expert

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "firstname" : "firstName",
      "lastname" : "lastName",
      "job_title" : "jobTitle",
      "email" : "you@email.com",
      "company" : "companyName",
      "phone_number" : "phoneNumber",
      "location_city" : "city",
      "location_state" : "state_province",
      "location_country" : "country",
      "location_postal" : "postalCode",
      "location_address" :"address"    
    }
  ],
  "success": true
}
```


### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`firstname` | true | __string__first name
`lastname` | true |  __string__last name
`job_title` | true |  __string__job title
`email` | true |  __string__email address
`company` | true |  __string__company
`department` | optional |  __string__department
`phone_number` | optional | __string__ phone number
`phone_number_extension` | optional |  __string__phone number extension
`location_city` | optional |  __string__city
`location_state` | optional |  __string__state or province
`location_country` | optional |  __string__country
`location_postal` | optional |  __string__postal code
`location_address` | optional |  __string__address
`location_building` | optional |  __string__building
`location_room` | optional |  __string__room

## Update an Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username"
  -X PUT
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "user": "you.username",
    "updated": true
  },
  "success": true
}
```

This endpoint updates a expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`firstname` | true | __string__first name
`lastname` | true |  __string__last name
`job_title` | true |  __string__job title
`email` | true |  __string__email address
`company` | true |  __string__company
`department` | optional |  __string__department
`phone_number` | optional | __string__ phone number
`phone_number_extension` | optional |  __string__phone number extension
`location_city` | optional |  __string__city
`location_state` | optional |  __string__state or province
`location_country` | optional |  __string__country
`location_postal` | optional |  __string__postal code
`location_address` | optional |  __string__address
`location_building` | optional |  __string__building
`location_room` | optional |  __string__room
`is_private` | optional | __integer__1 or 0
`is_published` | optional | __integer__1 or 0


## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:id"
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

This endpoint deletes a specific Expert.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#Biography

##Get Biography
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/biography"
  -X GET
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "biography" : "your biography"
    }
  ]
}
```

This endpoint retrieves an expert's biography

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/biography`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

## Add Biography


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/biography"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": [
    {
      { "id" : null }
    }
  ]
}
```

This endpoint adds a Biography.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/biography`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`description` | optional | __string__biography content 



#Tagline

##Get Tagline
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tagline"
  -X GET
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "tagline" : "your tagline"
    }
  ]
}
```

This endpoint retrieves an expert's tagline

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tagline`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

## Add Tagline


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tagline"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "tagline" : {
        { "id" : null }
      }
    }
  ]
}
```

This endpoint adds a tagline.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tagline`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`tagline` | optional | __string__tagline content 


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint retrieves all Links.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve


## Get a Specific Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/:id"
  -X GET
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
`id` | __integer__Id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | true | __string__name of the link 
`url` | true | __string__the actual url 


## Update a Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/:id"
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

This endpoint updates a link for expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the link
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | optional | __string__name of the link 
`url` | optional | __string__the actual url 

## Delete a Specific Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/:id"
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
`id` | __integer__The ID of the link
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert


#Sample Talk

##Get All Sample Talks
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk"
  -X GET
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Sample Talk

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk/:id"
  -X GET
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the link to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Add a SampleTalk

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk/"
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

This endpoint adds a Sample Talk for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | true | __string__title of the talk 
`description` | true | __string__description of the talk 

## Update a SampleTalk

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk/:id"
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

This endpoint updates a Sample Talk for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` |  __integer__id of Sample Talk
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | optional | __string__title of the talk 
`description` | optional | __string__description of the talk 

## Delete a Specific Sample Talk


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk/:id"
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

This endpoint deletes a specific Sample Talk

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampletalk/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the link to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Accomplishment

##Get All Accomplishment
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment"
  -X GET
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

This endpoint retrieves all Accomplishments.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve


## Get a Specific Accomplishment

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id"
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

This endpoint retrieves a specific Accomplishment.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the sample talk to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds an Accomplishment for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | required | __string__title of the talk 
`description` | required | __string__description of the talk 
`type` | optional | __string__Type of accomplishment. 71 for 'professional' and 73 for 'personal'
`date` | optional | __integer__date in unix time

##Update a Specific Accomplishment

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id"
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

This endpoint updates an Accomplishment for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of accomplishment
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | optional | __string__title of the talk 
`description` | optional | __string__description of the talk 
`type` | optional | __string__Type of accomplishment. 71 for 'professional' and 73 for 'personal'
`date` | optional | __integer__date in unix time

## Delete a Specific Accomplishment


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accompishment/:id"
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

This endpoint deletes a specific Accomplishment.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the accomplishment to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert


#Affiliation

##Get All Affiliation
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation"
  -X GET
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

This endpoint retrieves all Affiliations.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Affiliation

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id"
  -X GET
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

This endpoint retrieves a specific Affiliation.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the affiliation to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds an Affiliation for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__name of the affiliation

##Update an Affiliation

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id"
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

This endpoint updates an Affiliation for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | optional | __string__name of the affiliation

## Delete a Specific affiliation


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id"
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

This endpoint deletes a specific Affiliation.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the affiliation to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Event Appearances

##Get All Event Appearances
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance"
  -X GET
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

This endpoint retrieves all Event Apperances for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve


## Get a Specific Event Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance/:id"
  -X GET
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

This endpoint retrieves a specific event appearance for an expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Add an Event Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance/"
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

This endpoint adds an Event Appearance for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | required | __string__title of the Event 
`event_name` | required | __string__name of the event 
`location` | optional | __string__name of the city/country where event took place
`date` | optional | __integer__date in unix time

##Update an Event Appearance


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance/:id"
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

This endpoint updates an Event Appearance for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | optional | __string__title of the Event 
`event_name` | optional | __string__name of the event 
`location` | optional | __string__name of the city/country where event took place
`date` | optional | __integer__date in unix time

## Delete a Specific Event Appearance


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventappearance/:id"
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

This endpoint deletes a specific Event Appearance.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/:username/eventappearance/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the Event Appearance to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Media Appearance

##Get All Media Appearance
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance"
  -X GET
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

This endpoint retrieves all Media Appearances for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Media Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance/:id"
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

This endpoint retrieves a specific Media Appearance.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve


## Add a Media Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance/"
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

This endpoint adds a Media Appearance for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | required | __string__title of the media appearance
`organization` | required | __string__name of the organization 
`details` | required | __string__details of the media appearance 
`type` | optional | __string__this can be one of 'print', 'online', 'tv', 'radio'
`url` | optional | __string__link to the media appearance
`date` | optional | __integer__date in unix time

##Update a Media Appearance
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance/:id"
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

This endpoint updates a Media Appearance for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | optional | __string__title of the media appearance
`organization` | optional | __string__name of the organization 
`details` | optional | __string__details of the media appearance 
`type` | optional | __string__this can be one of 'print', 'online', 'tv', 'radio'
`url` | optional | __string__link to the media appearance
`date` | optional | __integer__date in unix time

## Delete a Specific Media Appearance


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaappearance/:id"
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

This endpoint deletes a specific Media Appearance.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the Media Appearance to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Education

##Get All Education
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education"
  -X GET
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

This endpoint retrieves all Education.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Education

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/:id"
  -X GET
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

This endpoint retrieves a specific Education.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds an Education for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
institution | required | name of the instituion
degree | required | degree obtained.
major | optional | Level of study. Bachelors/Masters/Phd
`description` | optional | __string__additional information for the degree
`date` | optional | __integer__year of graduation. Enter '1998' if graduation year is 1998

## Update an Education 

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/:id"
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

This endpoint updates an Education for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`institution` | optional | __string__name of the instituion
`degree` | optional | __string__degree obtained.
`major` | optional | __string__Level of study. Bachelors/Masters/Phd
`description` | optional | __string__additional information for the degree
`date` | optional | __integer__year of graduation. Enter '1998' if graduation year is 1998


## Delete a Specific Education


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/:id"
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

This endpoint deletes a specific Education.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the Education to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Testimonial

##Get All Testimonial
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial"
  -X GET
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

This endpoint retrieves all Testimonials for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve


## Get a Specific Testimonial

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/:id"
  -X GET
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

This endpoint retrieves a specific Testimonial.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds an Testimonial for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__name of the person
`title` | required | __string__job title of the person
`company` | required | __string__company person works for
`recommendation` | required | __string__recommendation note
`url` | optional | __string__url of the company where person works

## Update a Testimonial

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/:id"
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

This endpoint updates a Testimonial for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | optional | __string__name of the person
`title` | optional | __string__job title of the person
`company` | optional | __string__company person works for
`recommendation` | optional | __string__recommendation note
`url` | optional | __string__url of the company where person works


## Delete a Specific Testimonial


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/:id"
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

This endpoint deletes a specific Testimonial.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the testimonial to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Patent

##Get All Patent
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent"
  -X GET
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

This endpoint retrieves all Patents.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Patent

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/:id"
  -X GET
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

This endpoint retrieves a specific Patent.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds a Patent for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`number` | required | __string__patent number
`title` | required | __string__title of the patent
`detail` | required | __string__description of the patent
`date` | optional | __integer__date of the patent granted in unix time
`url` | optional | __string__url of the patent

##Update a Patent

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/:id"
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

This endpoint updates a Patent for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`number` | optional | __string__patent number
`title` | optional | __string__title of the patent
`detail` | optional | __string__description of the patent
`date` | optional | __integer__date of the patent granted in unix time
`url` | optional | __string__url of the patent

## Delete a Specific Patent


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/:id"
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

This endpoint deletes a specific Patent.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the patent to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Research Grant

##Get All Research Grant
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant"
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

This endpoint retrieves all Reseach Grants.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Research grant

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant/:id"
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

This endpoint retrieves a specific Research Grant.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Add Research Grant

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant/"
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

This endpoint adds a Research Grant for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`organization` | required | __string__organization to give grant
`title` | required | __string__title of the grant
`detail` | required | __string__description of the grant
`date` | optional | __integer__date in unix time
`url` | optional | __string__url
`amount` | optional | __string__amount granted

##Update a Research Grant

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant/:id"
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

This endpoint updates a Research Grant for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`organization` | optional | __string__organization to give grant
`title` | optional | __string__title of the grant
`detail` | optional | __string__description of the grant
`date` | optional | __integer__date in unix time
`url` | optional | __string__url
`amount` | optional | __string__amount granted

## Delete a Specific Research Grant


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant/:id"
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

This endpoint deletes a specific Research Grant.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchgrant/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the link to research grant
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Partnerships

##Get All Partnerships
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

This endpoint retrieves all Partnerships for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Partnership

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id"
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
    }
  ],
  "success": true
}
```

This endpoint retrieves a specific Partnership for an expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the Partnership to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds a Partnership for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | required | __string__partnership title
`individual` | required | __string__partner name
`details` | required | __string__description of the partnership
`date` | optional | __integer__date in unix time
`url` | optional | __string__url
`organization` | optional | __string__organization

##Update a Partnership

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id"
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

This endpoint updates a Partnership for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | optional | __string__partnership title
`individual` | optional | __string__partner name
`details` | optional | __string__description of the partnership
`date` | optional | __integer__date in unix time
`url` | optional | __string__url
`organization` | optional | __string__organization


## Delete a Specific Partnership


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id"
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

This endpoint deletes a specific Partnership.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the Partnership to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint retrieves all Courses.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Course

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/:id"
  -X GET
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

This endpoint retrieves a specific Course.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds a Course for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | required | __string__course title
`details` | required | __string__description/details of the course
`url` | optional | __string__url

##Update a Specific Course

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/:id"
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

This endpoint updates a Course for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | optional | __string__course title
`details` | optional | __string__description/details of the course
`url` | optional | __string__url

## Delete a Specific Course


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/:id"
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

This endpoint deletes a specific Course.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the course to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint retrieves all Articles for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Article

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/:id"
  -X GET
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

This endpoint retrieves a specific Article.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds an Article for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | required | __string__course title
publisher | required | publisher name
`details` | required | __string__description/details of the course
`url` | optional | __string__url
authors | optional | co-authors
`url` | optional | __string__link to the article

##Update a Artcile

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/:id"
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

This endpoint updates a specific Article for expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | optional | __string__course title
`publisher` | optional | __string__publisher name
`details` | optional | __string__description/details of the course
`authors` | optional | __string__co-authors
`url` | optional | __string__link to the article

## Delete a Specific Article


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/:id"
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

This endpoint deletes a specific Article.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the article to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#Research Focus

##Get All Research Focus
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus"
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

This endpoint retrieves all Research Focus for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Research Focus

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/:id"
  -X GET
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

This endpoint retrieves a specific Research Focus.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the research focus to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Add Research Focus

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/"
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

This endpoint adds a Research Focus for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | required | __string__course title
`details` | required | __string__description/details of the course
`url` | optional | __string__url
`date` | optional | __integer__date in unix format
sub`title` | optional | __string__

##Update a Research Focus


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/"
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

This endpoint updates a specific Research Focus for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`title` | optional | __string__course title
`details` | optional | __string__description/details of the course
`url` | optional | __string__url
`date` | optional | __integer__date in unix format
`subtitle` | optional | __string__

## Delete a Specific Research Focus


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/:id"
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

This endpoint deletes a specific Research Focus.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchfocus/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the research focus to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#Topics

##Get All Topics
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/"
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

This endpoint retrieves all Topics for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Topic

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/:id"
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
`id` | __integer__id of the topic to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds a Topic for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__topic name


## Delete a Specific Topic


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/:id"
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

This endpoint deletes a specific Topic for an expert.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the topic to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#Industry

##Get All Industry
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/"
  -X GET
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

This endpoint retrieves all Industries.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Industry

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/:id"
  -X GET
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the industry to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve.

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

This endpoint adds an Industry for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__Industry name



## Delete a Specific Insutry

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/:id"
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
`id` | __integer__id of the industry to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#Languages

##Get All languages
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/"
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

This endpoint retrieves all Languages.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Languages

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id"
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

This endpoint retrieves a specific Language.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the language to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint adds a Language for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__langauge name


##Update a Language

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id"
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

This endpoint updates a Language for an expert.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | optional | __string__langauge name

## Delete a Specific Language

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id"
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

This endpoint deletes a specific Language.


### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the research focus to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#Fees

##Get All Fees
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fee"
  -X GET
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

This endpoint retrieves Fees for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fee`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Add Fees

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fee"
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

This endpoint adds a Fees for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fee`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`fee_min` | required | __integer__min fees
`fee_max` | required | __integer__max fees

#Availability

##Get Availability
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

This endpoint retrieves all Availability.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/availability`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve


##Add Availability
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/availability"
  -X POST
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

This endpoint adds Availability.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/availability`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`availability_keynote` | optional | __integer__available for keynote(1 or 0)
`availability_moderator` | optional | __integer__available for moderator(1 or 0)
`availability_panelist` | optional | __integer__available for panelist(1 or 0)
`availability_workshop` | optional | __integer__available for workshop(1 or 0)
`availability_host_mc` | optional | __integer__available for host/mc (1 or 0)
`availability_appearance`| optional | __integer__available for author appearance(1 or 0)
`availability_corptraining` | optional | __integer__available for corporate training(1 or 0)

#Social

##Get All Social
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/social"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      { "id" : null }
    }
  ],
  "success": true
}
```

This endpoint retrieves all Social Links.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/social`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Add Social

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/social/"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
      { "id" : null}
  },
  "success": true
}
```

This endpoint adds Social Links for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/social/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`twitter` | optional | __string__twitter url
`facebook` | optional | __string__facebook url
`linkedin` | optional | __string__linkedin url
`gplus` | optional | __string__gplus url
`stackexchange` | optional | __string__stackexchange url,
`github` | optional | __string__github url
`flickr` | optional | __string__flickr url
`pinterest` | optional | __string__pinterest url
`instagram` | optional | __string__instagram url
`tumblr` | optional | __string__tumblr url
`youtube` | optional | __string__youtube url


#Categories

##Get All Categories
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/category/"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "category 1"
    },
    {
      "id": 2,
      "name": "category 2"
    }
  ],
  "success": true
}
```

This endpoint retrieves all Categories for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/category/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Category

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/category/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {
      "id": 1,
      "name": "category 1"
     }
  ],
  "success": true
}
```

This endpoint retrieves a specific Category for an expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/category/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the category to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Add Category

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/category/"
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

This endpoint adds a Category for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/category/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__category name


## Delete a Specific Category


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/category/:id"
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

This endpoint deletes a specific Category for an expert.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/category/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the category to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Tags

##Get All Tags
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tag/"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "tag 1"
    },
    {
      "id": 2,
      "name": "tag 2"
    }
  ],
  "success": true
}
```

This endpoint retrieves all Tags for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tag/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Tag

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tag/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {
      "id": 1,
      "name": "tag 1"
     }
  ],
  "success": true
}
```

This endpoint retrieves a specific Tag for an expert.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tag/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the tag to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Add Tag

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tag/"
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

This endpoint adds a Tag for an expert.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tag/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__tag name


## Delete a Specific Tag


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tag/:id"
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

This endpoint deletes a specific Tag for an expert.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/tag/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the tag to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert

#Industry

##Get All Industry
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/"
  -X GET
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

This endpoint retrieves all Industries.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

## Get a Specific Industry

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/:id"
  -X GET
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the industry to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve.


#YouTube

##Get All YouTube Media
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

This endpoint retrieves all YouTube media for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/:username/media/youtube`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

##Get a Specific YouTube item

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

This endpoint retrieves a specific YouTube item.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/youtube/:id`

Parameter | Description
--------- | -----------
`id` | __integer__id of the youtube item to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve


#Vimeo

##Get All Vimeo Media
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

This endpoint retrieves all Vimeo item for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/vimeo`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

##Get a Specific Vimeo item

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

This endpoint retrieves a specific Vimeo item.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/vimeo/:id`

Parameter | Description
--------- | -----------
`id` | __integer__id of the vimeo item to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#SlideShare

##Get All SlideShare Media
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

This endpoint retrieves all SlideShare media for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/:username/media/slideshare`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

##Get a Specific SlideShare media

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

This endpoint retrieves all SlideShare media for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/slideshare/:id`

Parameter | Description
--------- | -----------
`id` | __integer__id of the slideshare item to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#Documents

##Get All Documents
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

This endpoint retrieves all Documents.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/document`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

##Get a Specific Document

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

This endpoint retrieves a specific Document.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/document/:id`

Parameter | Description
--------- | -----------
`id` | __integer__id of the document item to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint retrieves all Photos for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/photo`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

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

This endpoint retrieves a specific Photo.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/photo/:id`

Parameter | Description
--------- | -----------
`id` | __integer__id of the photo to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve


#Video

##Get All Videos
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/video"
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

This endpoint retrieves all Videos for an expert.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/video`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

##Get a Specific Video

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

This endpoint retrieves a specific Video.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/media/video/:id`

Parameter | Description
--------- | -----------
`id` | __integer__id of the video to retrieve
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

#CV

##Get CV
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/cv"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      {
        "id": "ID",
        "url":"url",
        "document_url":"document url"}
    }
  ],
  "success": true
}
```

This endpoint retrieves a cv.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/cv`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the expert to retrieve

# Staff

## Get All Employees

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/employee"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "staff": [
      {
        "username": "myusername",
        "corporation": "mycorporation",
        "tagline": "My tagline",
        "avatar": {
          "small": "my small avatar url",
          "medium": "my medium avatar url",
          "large": "my large avatar url",
          "original": "my original avatar url"
        }
      }
    ],
    "total": 12
  },
  "success": true
}
```

This endpoint retrieves all Employees. Please note that this endpoint returns both staff users and experts. 

To retreive the original photo uploaded to ExpertFile, access "avatar.original".

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/employee`

### Url Parameters

Parameter  | Desription
---------  | ----------
`corporation`  | __integer__The corporation id

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`q` | - | __string__search query.
`access` | public | __string__This can be public or private.
`page_size` | 10 | __integer__no. of experts to return.
`page_from` | 0 | __integer__
`countries` | - | __string__
`companies` | - | __string__
`fields` | - | __string__
`sort` | name | __string__ name or featured.
`searchfield` | - | __string__ fullname to query only name field. 

## Get a Specific Staff

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/username"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "account": [
            {
                "id": 1,
                "firstname": "firstname",
                "lastname": "lastname",
                "corporation_id": 1,
                "job_title": "job_title",
                "location_city": "location_city",
                "location_state": "location_state",
                "location_country": "location_country",
                "location_postal": "location_postal",
                "location_address": "location_address",
                "location_building": "location_building",
                "location_room": "location_room",
                "email": "myemail@example.com",
                "company": "company",
                "department": "department",
                "phone_number": "phone_number",
                "phone_number_extension": "phone_number_extension",
                "username": "username",
                "is_published": 0
            }
        ],
        "biography": [
            {
                "biography": ""
            }
        ],
        "category": [],
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
        "education": [],
        "language": [],
        "link": [],
        "tag": [],
        "tagline": [
            {
                "tagline": ""
            }
        ],
        "avatar": []
    },
    "success": true
}
```
This endpoint retrieves a specific Staff User.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

##Add a Staff User

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
    "data": {
        "username": "username",
        "inserted": true
    },
    "success": true
}
```


### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/staff`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`firstname` | true | __string__first name
`lastname` | true |  __string__last name
`job_title` | true |  __string__job title
`email` | true |  __string__email address
`company` | true |  __string__company
`department` | optional |  __string__department
`phone_number` | optional | __string__ phone number
`phone_number_extension` | optional |  __string__phone number extension
`location_city` | optional |  __string__city
`location_state` | optional |  __string__state or province
`location_country` | optional |  __string__country
`location_postal` | optional |  __string__postal code
`location_address` | optional |  __string__address
`location_building` | optional |  __string__building
`location_room` | optional |  __string__room

## Update a Staff User


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username"
  -X PUT
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": {
    "user": "you.username",
    "updated": true
  },
  "success": true
}
```

This endpoint updates a Staff User.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/staff`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff user

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`firstname` | true | __string__first name
`lastname` | true |  __string__last name
`job_title` | true |  __string__job title
`email` | true |  __string__email address
`company` | true |  __string__company
`department` | optional |  __string__department
`phone_number` | optional | __string__ phone number
`phone_number_extension` | optional |  __string__phone number extension
`location_city` | optional |  __string__city
`location_state` | optional |  __string__state or province
`location_country` | optional |  __string__country
`location_postal` | optional |  __string__postal code
`location_address` | optional |  __string__address
`location_building` | optional |  __string__building
`location_room` | optional |  __string__room
`is_private` | optional | __integer__1 or 0
`is_published` | optional | __integer__1 or 0


## Delete a Specific Staff


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:id"
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

This endpoint deletes a specific Staff User.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/staff/:username`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff user to retrieve

#Biography

##Get Biography
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/biography"
  -X GET
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "biography" : "your biography"
    }
  ]
}
```

This endpoint retrieves an staff user's biography

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/biography`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

## Add Biography


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/biography"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": [
    {
      { "id" : null }
    }
  ]
}
```

This endpoint adds a Biography.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/biography`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`description` | optional | __string__biography content 



#Tagline

##Get Tagline
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tagline"
  -X GET
  -H "Authorization: xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "tagline" : "your tagline"
    }
  ]
}
```

This endpoint retrieves an staff user's tagline

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tagline`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

## Add Tagline


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tagline"
  -X POST
  -H "Authorization: Bearer xxx-xxx-xxx"
```


> if successful, The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "tagline" : {
        { "id" : null }
      }
    }
  ]
}
```

This endpoint adds a tagline.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tagline`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`tagline` | optional | __string__tagline content 


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

#Link

##Get All Links
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link"
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

This endpoint retrieves all Links.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve


## Get a Specific Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link/:id"
  -X GET
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Add a Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link/"
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

This endpoint adds a link for a staff user.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | true | __string__name of the link 
`url` | true | __string__the actual url 


## Update a Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link/:id"
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

This endpoint updates a link for a staff user.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the link
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | optional | __string__name of the link 
`url` | optional | __string__the actual url 

## Delete a Specific Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link/:id"
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

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/link/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the link
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

#Education

##Get All Education
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/education"
  -X GET
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

This endpoint retrieves all Education.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/education`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Get a Specific Education

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/education/:id"
  -X GET
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

This endpoint retrieves a specific Education.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__Id of the link to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Add Education

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/education/"
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

This endpoint adds an Education for a staff user.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/education/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`institution` | required | __string__name of the instituion
`degree` | required | __string__degree obtained.
`major` | optional | __string__Level of study. Bachelors/Masters/Phd
`description` | optional | __string__additional information for the degree
`date` | optional | __integer__year of graduation. Enter '1998' if graduation year is 1998

## Update an Education 

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/education/:id"
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

This endpoint updates an Education for a staff user.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/education/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`institution` | optional | __string__name of the instituion
`degree` | optional | __string__degree obtained.
`major` | optional | __string__Level of study. Bachelors/Masters/Phd
`description` | optional | __string__additional information for the degree
`date` | optional | __integer__year of graduation. Enter '1998' if graduation year is 1998


## Delete a Specific Education


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/education/:id"
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

This endpoint deletes a specific Education.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/accomplishment/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__The ID of the Education to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

#Languages

##Get All languages
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/"
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

This endpoint retrieves all Languages.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Get a Specific Languages

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/:id"
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

This endpoint retrieves a specific Language.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the language to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Add Language

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/"
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

This endpoint adds a Language for a staff user.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__langauge name


##Update a Language

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/:id"
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

This endpoint updates a Language for a staff user.

### HTTP Request

`PUT https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | optional | __string__ langauge name

## Delete a Specific Language

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/:id"
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

This endpoint deletes a specific Language.


### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/language/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__ ID of the research focus to delete
`corporation` | __integer__ The corporation id
`username` | __integer__ The username of the staff to retrieve

#Categories

##Get All Categories
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/category/"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "category 1"
    },
    {
      "id": 2,
      "name": "category 2"
    }
  ],
  "success": true
}
```

This endpoint retrieves all Categories for a staff user.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/category/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Get a Specific Category

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/category/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {
      "id": 1,
      "name": "category 1"
     }
  ],
  "success": true
}
```

This endpoint retrieves a specific Category for a staff user.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/category/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the category to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Add Category

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/category/"
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

This endpoint adds a Category for a staff user.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/category/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__category name


## Delete a Specific Category


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/category/:id"
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

This endpoint deletes a specific Category for a staff user.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/category/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the category to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

#Tags

##Get All Tags
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tag/"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "tag 1"
    },
    {
      "id": 2,
      "name": "tag 2"
    }
  ],
  "success": true
}
```

This endpoint retrieves all Tags for a staff user.

### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tag/`

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Get a Specific Tag

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tag/:id"
  -X GET
  -H "Authorization: Bearer xxx-xxx-xxx"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {
      "id": 1,
      "name": "tag 1"
     }
  ],
  "success": true
}
```

This endpoint retrieves a specific Tag for a staff user.


### HTTP Request

`GET https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tag/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the tag to retrieve.
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff to retrieve

## Add Tag

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tag/"
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

This endpoint adds a Tag for a staff user.

### HTTP Request

`POST https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tag/`

### URL Parameters

Parameter | Description
--------- | -----------
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff

###Body Parameters
Parameter | Required | Description
--------- | -------- | ----------
`name` | required | __string__tag name


## Delete a Specific Tag


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tag/:id"
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

This endpoint deletes a specific Tag for a staff user.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/staff/:username/tag/:id`

### URL Parameters

Parameter | Description
--------- | -----------
`id` | __integer__id of the tag to delete
`corporation` | __integer__The corporation id
`username` | __string__The username of the staff


# Inquiry

## General

Will send a general inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a general inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
 curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/general" 
 -X POST 
 -H "Authorization: Bearer xxx-xxx-xxx" 
 -d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/general

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)

## Event

Will send a event inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a event inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
 curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/event" 
 -X POST 
 -H "Authorization: Bearer xxx-xxx-xxx" 
 -d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>&event_name=<EVENT_NAME>&event_location=<EVENT_LOCATION>&event_date=<EVENT_DATE>&event_description=<EVENT_DESCRIPTION>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/event

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)
`event_name`| true | __string__  Event name
`event_location`| true | __string__  Event Location
`event_date`| true | __string__  your Event date(must be sent as UNIX timestamp)
`event_description`| true | __string__  Event Description

## Media

Will send a media inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a media inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
 curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/media" 
 -X POST 
 -H "Authorization: Bearer xxx-xxx-xxx" 
 -d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>&media_position=<MEDIA_POSITION>&media_type=<MEDIA_TYPE>&media_deadline=<MEDIA_DEADLINE>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/media

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)
`media_position`| true | __string__  Media Postion(valid input: 'reporter','editor','news_director','researcher', 'other')
`media_type`| true | __string__  Media Type(valid input: 'print','online','tv','radio')
`media_deadline`| true | __string__  Media deadline(must be sent as UNIX timestamp)

## Partnership

Will send a partnership inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a partnership inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/partnership" 
-X POST 
-H "Authorization: Bearer xxx-xxx-xxx" 
-d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>&partner_organization_type=<TYPE>&partner_focus=<FOCUS>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/partnership

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)
`partner_organization_type`| true | __string__  Media Postion(valid input: 'corporate', 'government', 'ngo', 'not_for_profit', 'other')
`partner_focus`| true | __string__  Media Type(valid input: 'business_development', 'corporate', 'fundraising', 'licensing', 'research', 'sponsorship', 'technology', 'other')

## Admission

Will send a admission inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a partnership inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/admission" 
-X POST 
-H "Authorization: Bearer xxx-xxx-xxx" 
-d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>&admission_type=<TYPE>&admission_program_name=<PROGRAM_NAME>&admission_faculty=<FACULTY>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/admission

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)
`admission_type`| true | __string__  Admission Type(valid input: 'undergraduate', 'graduate')
`admission_program_name`| true | __string__  Admission Program Name
`admission_faculty`| true | __string__  Admission Faculty

## Research

Will send a research inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a research inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/research" 
-X POST 
-H "Authorization: Bearer xxx-xxx-xxx" 
-d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>&research_area=<AREA>&research_stage_in_process=<PROCESS>&research_deadline=<DEADLINE>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/research

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)
`research_area`| true | __string__  Research Area
`research_stage_in_process`| true | __string__  Research Stage(valid input: 'collaboration', 'funding', 'partnership', 'other')
`research_deadline`| true | __string__  Research Deadline

## Business

Will send a business inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a business inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/business" 
-X POST 
-H "Authorization: Bearer xxx-xxx-xxx" 
-d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>&business_opportunity_type=<TYPE>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/business

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)
`business_opportunity_type`| true | __string__  Business Stage(valid input: 'consulting_engagement', 'new_ventures/partnerships', 'business_deals', 'corporate_training')

## Donor

Will send a donor inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a donor inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/donor" 
-X POST 
-H "Authorization: Bearer xxx-xxx-xxx" 
-d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>&donor_type=<TYPE>&donor_focus=<FOCUS>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/donor

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)
`donor_type`| true | __string__  Donor Type(valid input: 'corporate','government','ngo','not_for_profit', 'other')
`donor_focus`| true | __string__  Donor Focus(valid input: 'one_time_gift','recurring_gift','endowments','bequests','other')

## Expert Witness

Will send a expert witness inquiry to the expert, agent(depending on notification settings found in app) and mailing list recipients.

> To send a donor inquiry, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://public-api.expertfile.com/v2/organization/:corporation/inquiry/expertwitness" 
-X POST 
-H "Authorization: Bearer xxx-xxx-xxx" 
-d "message=<MESSAGE>&email=<EMAIL>&lastname=<LASTNAME>&firstname=<FIRSTNAME>&location_city=<CITY>&location_country=<COUNTRY_CODE>&location_state=<STATE_CODE>&username=<USERNAME>&expertwitness_stage_in_process=<PROCESS>&expertwitness_organization_type=<TYPE>"

```

> The above command returns JSON structured like this:

```json

{
  "data" : {
    "id" : <INQUIRY_ID>
  } , 
  "success": true
}
```

### HTTP Request

POST https://public-api.expertfile.com/v2/organization/:corporation/inquiry/expertwitness

###Body Parameters 

Parameter | Required | Description
--------- | -------- | -----------
`firstname` | true |  __string__ Sender first name
`lastname` | true | __string__  Sender last name
`email`| true | __string__  Sender email
`phone`| false | __string__  Sender phone number
`website`| false | __string__  Sender website
`organization`| false | __string__  Sender organization
`message`| true | __string__  Sender message
`location_city`| true | __string__  Sender city
`location_state` | true |  __string__ Sender state/province(if country is Canada or U.S.A valid state or province codes must be passed(See Helper->State/Province section for list).
`location_country` | true | __string__  Sender country(See Helper->Country/Province section for list) 
`username` | true | __string__  Recipient username(may only send to experts belonging to organization)
`expertwitness_stage_in_process`| true | __string__  Donor Type(valid input: 'investigation', 'in_litigation', 'approaching_trial','other')
`expertwitness_organization_type`| true | __string__  Donor Focus(valid input: 'legal_firm', 'corporate_legal_department', 'insurance_provider', 'government_agency', 'legal_nurse_consultant', 'other')

# Helper

## Country

These are the valid country codes and their corresponding names that may be used when sending location_country params to ExpertFile's API.

```json

{
  US : "UNITED STATES",
  CA : "CANADA",
  AF : "AFGHANISTAN",
  AL : "ALBANIA",
  DZ : "ALGERIA",
  AS : "AMERICAN SAMOA",
  AD : "ANDORRA",
  AO : "ANGOLA",
  AI : "ANGUILLA",
  AQ : "ANTARCTICA",
  AG : "ANTIGUA AND BARBUDA",
  AR : "ARGENTINA",
  AM : "ARMENIA",
  AW : "ARUBA",
  AU : "AUSTRALIA",
  AT : "AUSTRIA",
  AZ : "AZERBAIJAN",
  BS : "BAHAMAS",
  BH : "BAHRAIN",
  BD : "BANGLADESH",
  BB : "BARBADOS",
  BY : "BELARUS",
  BE : "BELGIUM",
  BZ : "BELIZE",
  BJ : "BENIN",
  BM : "BERMUDA",
  BT : "BHUTAN",
  BO : "BOLIVIA",
  BA : "BOSNIA AND HERZEGOVINA",
  BW : "BOTSWANA",
  BV : "BOUVET ISLAND",
  BR : "BRAZIL",
  IO : "BRITISH INDIAN OCEAN TERRITORY",
  BN : "BRUNEI DARUSSALAM",
  BG : "BULGARIA",
  BF : "BURKINA FASO",
  BI : "BURUNDI",
  KH : "CAMBODIA",
  CM : "CAMEROON",
  CV : "CAPE VERDE",
  KY : "CAYMAN ISLANDS",
  CF : "CENTRAL AFRICAN REPUBLIC",
  TD : "CHAD",
  CL : "CHILE",
  CN : "CHINA",
  CX : "CHRISTMAS ISLAND",
  CC : "COCOS (KEELING) ISLANDS",
  CO : "COLOMBIA",
  KM : "COMOROS",
  CG : "CONGO",
  CD : "CONGO, THE DEMOCRATIC REPUBLIC OF THE",
  CK : "COOK ISLANDS",
  CR : "COSTA RICA",
  CI : "COTE D IVOIRE",
  HR : "CROATIA",
  CU : "CUBA",
  CY : "CYPRUS",
  CZ : "CZECH REPUBLIC",
  DK : "DENMARK",
  DJ : "DJIBOUTI",
  DM : "DOMINICA",
  DO : "DOMINICAN REPUBLIC",
  TP : "EAST TIMOR",
  EC : "ECUADOR",
  EG : "EGYPT",
  SV : "EL SALVADOR",
  GQ : "EQUATORIAL GUINEA",
  ER : "ERITREA",
  EE : "ESTONIA",
  ET : "ETHIOPIA",
  FK : "FALKLAND ISLANDS (MALVINAS)",
  FO : "FAROE ISLANDS",
  FJ : "FIJI",
  FI : "FINLAND",
  FR : "FRANCE",
  GF : "FRENCH GUIANA",
  PF : "FRENCH POLYNESIA",
  TF : "FRENCH SOUTHERN TERRITORIES",
  GA : "GABON",
  GM : "GAMBIA",
  GE : "GEORGIA",
  DE : "GERMANY",
  GH : "GHANA",
  GI : "GIBRALTAR",
  GR : "GREECE",
  GL : "GREENLAND",
  GD : "GRENADA",
  GP : "GUADELOUPE",
  GU : "GUAM",
  GT : "GUATEMALA",
  GN : "GUINEA",
  GW : "GUINEA-BISSAU",
  GY : "GUYANA",
  HT : "HAITI",
  HM : "HEARD ISLAND AND MCDONALD ISLANDS",
  VA : "HOLY SEE (VATICAN CITY STATE)",
  HN : "HONDURAS",
  HK : "HONG KONG",
  HU : "HUNGARY",
  IS : "ICELAND",
  IN : "INDIA",
  ID : "INDONESIA",
  IR : "IRAN, ISLAMIC REPUBLIC OF",
  IQ : "IRAQ",
  IE : "IRELAND",
  IL : "ISRAEL",
  IT : "ITALY",
  JM : "JAMAICA",
  JP : "JAPAN",
  JO : "JORDAN",
  KZ : "KAZAKSTAN",
  KE : "KENYA",
  KI : "KIRIBATI",
  KP : "KOREA DEMOCRATIC PEOPLES REPUBLIC OF",
  KR : "KOREA REPUBLIC OF",
  KW : "KUWAIT",
  KG : "KYRGYZSTAN",
  LA : "LAO PEOPLES DEMOCRATIC REPUBLIC",
  LV : "LATVIA",
  LB : "LEBANON",
  LS : "LESOTHO",
  LR : "LIBERIA",
  LY : "LIBYAN ARAB JAMAHIRIYA",
  LI : "LIECHTENSTEIN",
  LT : "LITHUANIA",
  LU : "LUXEMBOURG",
  MO : "MACAU",
  MK : "MACEDONIA, THE FORMER YUGOSLAV REPUBLIC OF",
  MG : "MADAGASCAR",
  MW : "MALAWI",
  MY : "MALAYSIA",
  MV : "MALDIVES",
  ML : "MALI",
  MT : "MALTA",
  MH : "MARSHALL ISLANDS",
  MQ : "MARTINIQUE",
  MR : "MAURITANIA",
  MU : "MAURITIUS",
  YT : "MAYOTTE",
  MX : "MEXICO",
  FM : "MICRONESIA, FEDERATED STATES OF",
  MD : "MOLDOVA, REPUBLIC OF",
  MC : "MONACO",
  MN : "MONGOLIA",
  MS : "MONTSERRAT",
  MA : "MOROCCO",
  MZ : "MOZAMBIQUE",
  MM : "MYANMAR",
  NA : "NAMIBIA",
  NR : "NAURU",
  NP : "NEPAL",
  NL : "NETHERLANDS",
  AN : "NETHERLANDS ANTILLES",
  NC : "NEW CALEDONIA",
  NZ : "NEW ZEALAND",
  NI : "NICARAGUA",
  NE : "NIGER",
  NG : "NIGERIA",
  NU : "NIUE",
  NK : "NORFOLK ISLAND",
  MP : "NORTHERN MARIANA ISLANDS",
  NO : "NORWAY",
  OM : "OMAN",
  PK : "PAKISTAN",
  PW : "PALAU",
  PS : "PALESTINIAN TERRITORY, OCCUPIED",
  PA : "PANAMA",
  PG : "PAPUA NEW GUINEA",
  PY : "PARAGUAY",
  PE : "PERU",
  PH : "PHILIPPINES",
  PN : "PITCAIRN",
  PL : "POLAND",
  PT : "PORTUGAL",
  PR : "PUERTO RICO",
  QA : "QATAR",
  RE : "REUNION",
  RO : "ROMANIA",
  RU : "RUSSIAN FEDERATION",
  RW : "RWANDA",
  SH : "SAINT HELENA",
  KN : "SAINT KITTS AND NEVIS",
  LC : "SAINT LUCIA",
  PM : "SAINT PIERRE AND MIQUELON",
  VC : "SAINT VINCENT AND THE GRENADINES",
  WS : "SAMOA",
  SM : "SAN MARINO",
  ST : "SAO TOME AND PRINCIPE",
  SA : "SAUDI ARABIA",
  SN : "SENEGAL",
  SC : "SEYCHELLES",
  SL : "SIERRA LEONE",
  SG : "SINGAPORE",
  SK : "SLOVAKIA",
  SI : "SLOVENIA",
  SB : "SOLOMON ISLANDS",
  SO : "SOMALIA",
  ZA : "SOUTH AFRICA",
  GS : "SOUTH GEORGIA AND THE SOUTH SANDWICH ISLANDS",
  ES : "SPAIN",
  LK : "SRI LANKA",
  SD : "SUDAN",
  SR : "SURINAME",
  SJ : "SVALBARD AND JAN MAYEN",
  SZ : "SWAZILAND",
  SE : "SWEDEN",
  CH : "SWITZERLAND",
  SY : "SYRIAN ARAB REPUBLIC",
  TW : "TAIWAN, PROVINCE OF CHINA",
  TJ : "TAJIKISTAN",
  TZ : "TANZANIA, UNITED REPUBLIC OF",
  TH : "THAILAND",
  TG : "TOGO",
  TK : "TOKELAU",
  TO : "TONGA",
  TT : "TRINIDAD AND TOBAGO",
  TN : "TUNISIA",
  TR : "TURKEY",
  TM : "TURKMENISTAN",
  TC : "TURKS AND CAICOS ISLANDS",
  TV : "TUVALU",
  UG : "UGANDA",
  UA : "UKRAINE",
  AE : "UNITED ARAB EMIRATES",
  GB : "UNITED KINGDOM",
  UM : "UNITED STATES MINOR OUTLYING ISLANDS",
  UY : "URUGUAY",
  UZ : "UZBEKISTAN",
  VU : "VANUATU",
  VE : "VENEZUELA",
  VN : "VIET NAM",
  VG : "VIRGIN ISLANDS, BRITISH",
  VI : "VIRGIN ISLANDS, U.S.",
  WF : "WALLIS AND FUTUNA",
  EH : "WESTERN SAHARA",
  YE : "YEMEN",
  YU : "YUGOSLAVIA",
  ZM : "ZAMBIA",
  ZW : "ZIMBABWE"
}
```

## State/Province

These are the valid state/province codes that may be used when sending location_state param to ExpertFile's API and the location_country is set to CA/US.

```json
 ["AB", "BC", "ON", "NF", "NS", "PE", "NU", "NB", "QC", "MB"]
```
```json
["AB","NT","YT","AL","AK","AZ","AR","CA","CO","CT","DE","DC","FL","GA","HI","ID","IL","IN","IA","KS","KY","LA","ME","MD","MA","MI","MN","MS","MO","MT","NE","NV","NH","NJ","NM","NY","NC","ND","OH","OK","OR","PA","RI","SC","SD","TN","TX","UT","VT","VA","WA","WV","WI","WY"]
```
