---
title: API Reference

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

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: xxx-xxx-xxx"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Experts

## Get All Experts

```shell
curl "https://public-api.expertfile.com/organization/:corporation/experts"
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

### Url Parameters

Parameter  | Desription
---------  | ----------
corporation  | The corporation id

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
accessToken | - | required.


## Get a Specific Expert

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/2"
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
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/:username`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete


#Link

##Get All Links
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/experts/:username/link`

### URL Parameters

Parameter | Description
--------- | -----------
corporation | The corporation id
username | The username of the expert to retrieve

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Link


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/link/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete


#Sample Talk

##Get All Sample Talks
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Link

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/sampleTalk/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Accomplishment

##Get All Accomplishment
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Accomplishment

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accomplishment/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/accompishment/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete


#Affiliation

##Get All Affiliation
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/affiliation"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

#Event Appearances

##Get All Event Appearances
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Event Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Event Appearance


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/eventAppearance/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Media Appearance

##Get All Media Appearance
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Media Appearance

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Media Appearance


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/mediaAppearance/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Education

##Get All Education
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Education

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/education/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Testimonial

##Get All Testimonial
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.


## Get a Specific Testimonial

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/testimonial/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Patent

##Get All Patent
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Patent

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Patent


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/patent/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Research Grant

##Get All Reseach Grant
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Research grant

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Research Grant


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchGrant/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Partnerships

##Get All partnerships
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Partnership

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Partnership


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/partnership/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Courses

##Get All Courses
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Course

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Course


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/course/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Articles

##Get All Articles
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Article

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Article


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/article/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Research Focus

##Get All Research Focus
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Research Focus

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Research Focus


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/researchFocus/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Topics

##Get All Topics
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Topic

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/topic/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Industry

##Get All Industry
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Industry

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve.

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/industry/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Languages

##Get All languages
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Languages

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/language/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Fees

##Get All fees
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fees"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Link

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fees/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
id | Id of the link to retrieve.
corporation | The corporation id
username | The username of the expert to retrieve.

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/fees/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Availability

##Get All availability
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/availability"
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

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Availability

```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/availability/2"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Expert


```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/availability/2"
  -X DELETE
  -H "Authorization: xxx-xxx-xxx"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ""
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE https://public-api.expertfile.com/v2/organization/:corporation/expert/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

#Social

##Get All Social
```shell
curl "https://public-api.expertfile.com/v2/organization/:corporation/expert/:username/social"
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

`GET https://public-api.expertfile.com/v2/organization/:corporation/social`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.



