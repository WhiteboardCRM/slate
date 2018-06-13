---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php
  - python
  - javascript

toc_footers:
#  - <a href='#'>Sign Up for a Developer Key</a>
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

```php
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

> Make sure to replace `myAuthToken` with your Auth Token.

Whiteboard CRM uses Oauth2 Auth Tokens to allow access to the API.

Whiteboard CRM expects for the Auth Token to be included in all API requests to the server in a header that looks like the following:

`Authorization: myAuthToken`

<aside class="notice">
You must replace <code>myAuthToken</code> with your personal Auth Token.
</aside>

# Contacts

## Get All Contacts

```php
// set headers

api = WbCRM::APIClient.authorize!('myAuthToken')
api.contacts.get
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

This endpoint retrieves all contacts.

### HTTP Request

`GET http://api.whiteboardmortgage.com/v1/contacts`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include contacts that have already been adopted.

<aside class="success">
Slap Hands - we are so cool!
</aside>

## Get a Specific Contact

```php
require 'wbcrm'

api = WbCRM::APIClient.authorize!('myAuthToken')
api.contacts.get(2)
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.contacts.get(2)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/contacts/2"
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.contacts.get(2);
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

This endpoint retrieves a specific contact.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://api.whiteboardmortgage.com/v1/contacts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to retrieve

## Delete a Specific Contact

```php
require 'wbcrm'

api = WbCRM::APIClient.authorize!('myAuthToken')
api.contacts.delete(2)
```

```python
import wbcrm

api = wbcrm.authorize('myAuthToken')
api.contacts.delete(2)
```

```shell
curl "http://api.whiteboardmortgage.com/v1/contacts/2"
  -X DELETE
  -H "Authorization: myAuthToken"
```

```javascript
const wbcrm = require('wbcrm');

let api = wbcrm.authorize('myAuthToken');
let max = api.contacts.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific contact.

### HTTP Request

`DELETE http://example.com/contacts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete

