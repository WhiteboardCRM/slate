---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php
  - python
  - javascript

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Whiteboard CRM API! You can use our API to access Whiteboard CRM API endpoints, which can get information on various Contacts, Records, and Relationships in our database.

We have language bindings in Javascript, PHP, Python, and Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```php?start_inline=1
use 'wbcrm';

$api = wbcrm.authorize('myAuthToken');
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
```

> Make sure to replace <code>myAuthToken</code> with your Auth Token.

Whiteboard CRM uses Oauth2 Auth Tokens to allow access to the API.

Whiteboard CRM expects for the Auth Token to be included in all API requests to the server in a header that looks like the following:

`Authorization: myAuthToken`

<aside class="notice">
You must replace <code>myAuthToken</code> with your personal Auth Token.
</aside>

# Contacts

## Get All Contacts

```php?start_inline=1
// set headers

$api = WbCRM::APIClient->authorize!('myAuthToken');
$api->contacts->get();
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.contacts.get()
```

```shell
curl "http://api.whiteboardmortgage.com/v1/contacts"
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let contacts = api.contacts.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "lastName": "Pike",
    "fistName": "Rob",
    "createdDate": "2017-10-17T19:19:19-06:00",
    "cellPhone": 5551234567,
    "birthday": "1956-01-01T12:00:00-06:00"
  },
  {
    "id": 2,
    "lastName": "Thompson",
    "fistName": "Ken",
    "createdDate": "2016-10-17T19:19:19-06:00",
    "cellPhone": 5551234567,
    "birthday": "1943-02-04T12:00:00-06:00"
  },
]
```

This endpoint retrieves all contacts.

### HTTP Request

`GET http://api.whiteboardmortgage.com/v1/contacts`

### HTTP Response

Code | Meaning
---- | -------
200 | Found
204 | No Content

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
filter | null | A string given in format "field:text" performs a search where the field is like the text.
sort | null | A string given in format "field1,field2" sorts the returned results by the given fields. This can be prepended with negative(-) to reverse the sort order.
limit | null | A string given in format **"50,0"** limits by the first and uses the second as an offset. 

<aside class="success">
Slap Hands - we are so cool!
</aside>

## Create a new Contact

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.contacts.post($data);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.contacts.post(data)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/contacts"
  -X POST
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let data = someJson;
let api = wbcrm.authorize('myAuthToken');
let max = api.contacts.post(data);
```

This endpoint creates a new contact.

### HTTP Request

`POST http://api.whiteboard.com/v1/contacts`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 


## Get a Specific Contact

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.contacts.get(3);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.contacts.get(3)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/contacts/3"
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.contacts.get(3);
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "lastName": "Kernighan",
  "fistName": "Brian",
  "createdDate": "2015-10-17T19:19:19-06:00",
  "cellPhone": 5551234567,
  "birthday": "1942-01-01T12:00:00-06:00"
}
```

This endpoint retrieves a specific contact.

### HTTP Request

`GET http://api.whiteboardmortgage.com/v1/contacts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to retrieve

## Update a Specific Contact

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.contacts.update(5);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.contacts.update(5)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/contacts/5"
  -X UPDATE
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.contacts.updatee(5);
```

This endpoint updates a specific contact.

### HTTP Request

`PUT http://api.whiteboard.com/v1/contacts/<ID>`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 


## Delete a Specific Contact

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.contacts.delete(5);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.contacts.delete(5)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/contacts/5"
  -X DELETE
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.contacts.delete(5);
```

This endpoint deletes a specific contact.

### HTTP Request

`DELETE http://api.whiteboard.com/v1/contacts/<ID>`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete

# Records

## Get All Records

```php?start_inline=1
// set headers

$api = WbCRM::APIClient->authorize!('myAuthToken');
$api->relationships->get();
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.records.get()
```

```shell
curl "http://api.whiteboardmortgage.com/v1/records"
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let records = api.records.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "lastName": "Pike",
    "fistName": "Rob",
    "createdDate": "2017-10-17T19:19:19-06:00",
  },
  {
    "id": 2,
    "lastName": "Thompson",
    "fistName": "Ken",
    "createdDate": "2016-10-17T19:19:19-06:00",
  },
]
```

This endpoint retrieves all records.

### HTTP Request

`GET http://api.whiteboardmortgage.com/v1/records`

### HTTP Response

Code | Meaning
---- | -------
200 | Found
204 | No Content

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
filter | null | A string given in format "field:text" performs a search where the field is like the text.
sort | null | A string given in format "field1,field2" sorts the returned results by the given fields. This can be prepended with negative(-) to reverse the sort order.
limit | null | A string given in format **"50,0"** limits by the first and uses the second as an offset. 

<aside class="success">
Slap Hands - We got some records!
</aside>

## Create a new Record

```php?=start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.records.post($data);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.records.post(data)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/records"
  -X POST
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let data = someJson;
let api = wbcrm.authorize('myAuthToken');
let max = api.records.post(data);
```

This endpoint creates a new record.

### HTTP Request

`POST http://api.whiteboard.com/v1/records`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 


## Get a Specific Record

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.records.get(3);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.records.get(3)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/records/3"
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.records.get(3);
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "lastName": "Kernighan",
  "fistName": "Brian",
  "createdDate": "2015-10-17T19:19:19-06:00",
}
```

This endpoint retrieves a specific record.

### HTTP Request

`GET http://api.whiteboardmortgage.com/v1/records/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the record to retrieve

## Update a Specific Record

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.records.update(5);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.records.update(5)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/records/5"
  -X UPDATE
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.records.update(5);
```

This endpoint updates a specific record.

### HTTP Request

`PUT http://api.whiteboard.com/v1/records/<ID>`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 

## Delete a Specific Record

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.records.delete(5);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.records.delete(5)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/records/5"
  -X DELETE
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.records.delete(5);
```

This endpoint deletes a specific record.

### HTTP Request

`DELETE http://api.whiteboard.com/v1/records/<ID>`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the record to delete

# Relationships

## Get All Relationships

```php?start_inline=1
// set headers

$api = WbCRM::APIClient->authorize!('myAuthToken');
$api->relationships->get();
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.relationships.get()
```

```shell
curl "http://api.whiteboardmortgage.com/v1/relationships"
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let relationships = api.relationships.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "lastName": "Pike",
    "fistName": "Rob",
    "createdDate": "2017-10-17T19:19:19-06:00",
  },
  {
    "id": 2,
    "lastName": "Thompson",
    "fistName": "Ken",
    "createdDate": "2016-10-17T19:19:19-06:00",
  },
]
```

This endpoint retrieves all relationships.

### HTTP Request

`GET http://api.whiteboardmortgage.com/v1/relationships`

### HTTP Response

Code | Meaning
---- | -------
200 | Found
204 | No Content

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
filter | null | A string given in format "field:text" performs a search where the field is like the text.
sort | null | A string given in format "field1,field2" sorts the returned results by the given fields. This can be prepended with negative(-) to reverse the sort order.
limit | null | A string given in format **"50,0"** limits by the first and uses the second as an offset. 

<aside class="success">
Slap Hands - We got some relationships!
</aside>

## Create a new Relationship

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.relationships.post($data);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.relationships.post(data)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/relationships"
  -X POST
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let data = someJson;
let api = wbcrm.authorize('myAuthToken');
let max = api.relationships.post(data);
```

This endpoint creates a new relationship.

### HTTP Request

`POST http://api.whiteboard.com/v1/relationships`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 

## Get a Specific Relationship

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.relationships.get(3);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.relationships.get(3)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/relationships/3"
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.relationships.get(3);
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "lastName": "Kernighan",
  "fistName": "Brian",
  "createdDate": "2015-10-17T19:19:19-06:00",
}
```

This endpoint retrieves a specific relationship.

### HTTP Request

`GET http://api.whiteboardmortgage.com/v1/relationships/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the relationship to retrieve

## Update a Specific Relationship

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.relationships.update(5);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.relationships.update(5)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/relationships/5"
  -X UPDATE
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.relationships.update(5);
```

This endpoint updates a specific relationship.

### HTTP Request

`PUT http://api.whiteboard.com/v1/relationships/<ID>`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 



## Delete a Specific Relationship

```php?start_inline=1
require 'wbcrm';

$api = WbCRM::APIClient.authorize!('myAuthToken');
$api.relationships.delete(5);
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.relationships.delete(5)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/relationships/5"
  -X DELETE
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.relationships.delete(5);
```

This endpoint deletes a specific relationship.

### HTTP Request

`DELETE http://api.whiteboard.com/v1/relationships/<ID>`

### HTTP Response

Code | Meaning
---- | -------
200 | OK
404 | Not Found 

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the relationship to delete
