---
title: Phone Number Storer API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - Just testing Slate

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

The Phone Number Storer API stores your phone numbers in your Phone Book on our dedicated servers. It allows you to:

* Add a phone number to the Phone Book
* Modify or remove a record from your stored numbers
* Fetch the details of a specific number
* Download the whole Phone Book to your application

<aside>
Remember — Contact our support to get your <code>phoneBookID</code>!
</aside>

# Methods
The PhoneNumberStorer API supports the following methods:

## Add a Number

```ruby
require 'phoneNumberStorer'

api = phoneNumberStorer::APIClient.add!('{
		"phoneNumber": 2024441234,
		"name":"George Washington",
		"state":"DC"
	}')
api.phoneBook.post
```

```python
import phoneNumberStorer

api = phoneNumberStorer.add('{
		"phoneNumber": 2024441234,
		"name":"George Washington",
		"state":"DC"
	}')
api.phoneBook.post()
```

```shell
curl "http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/add" \
  -H "add: '{
		"phoneNumber": 2024441234,
		"name":"George Washington",
		"state":"DC"
	}'"
```

```javascript
const phoneNumberStorer = require('phoneNumberStorer');

let api = phoneNumberStorer.add('{
		"phoneNumber": 2024441234,
		"name":"George Washington",
		"state":"DC"
	}');
let phoneNumberStorer = api.phoneBook.post();
```

> The above command returns the following HTTP responses:

```HTTP
			200	- Success
			400 - Invalid request
			1010 - Invalid phone number
			1011 - Phone number exists
```

This endpoint adds a phone number to the phone book.

### HTTP Request

`POST http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/add`

### Query Parameters

Parameter | Type | Required | Description
--------- | ------- | ----- | ------
phoneNumber | uint64 | yes | The 10-digit phone number that also serves as the unique identifier of the record
name | string | yes | The name of the person to associate with the number
state | string | yes | The US state code, where the landline phone number is located or where the owner of the mobile phone number resides

## Update a Number

```ruby
require 'phoneNumberStorer'

api = phoneNumberStorer::APIClient.update!('{
		"phoneNumber": 2024441234,
		"name":"Abraham Lincoln",
		"state":"DC"
	}')
api.phoneBook.patch
```

```python
import phoneNumberStorer

api = phoneNumberStorer.update('{
		"phoneNumber": 2024441234,
		"name":"Abraham Lincoln",
		"state":"DC"
	}')
api.phoneBook.patch()
```

```shell
curl "http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/update" \
  -H "update: '{
		"phoneNumber": 2024441234,
		"name":"Abraham Lincoln",
		"state":"DC"
	}'"
```

```javascript
const phoneNumberStorer = require('phoneNumberStorer');

let api = phoneNumberStorer.update('{
		"phoneNumber": 2024441234,
		"name":"Abraham Lincoln",
		"state":"DC"
	}');
let phoneNumberStorer = api.phoneBook.patch();
```

> The above command returns the following HTTP responses:

```HTTP
			200	- Success
			400 - Invalid request
			1010 - Invalid phone number
```

This endpoint adds or modifies the **name** and the **state** of a phone number.

<aside class="notice">
You cannot modify the <b>phoneNumber</b> field.
</aside>

### HTTP Request

`PATCH http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/update`

### Query Parameters

Parameter | Type | Required | Description
--------- | ------- | ----- | ------
phoneNumber | uint64 | yes | The 10-digit phone number to identify the record that should be modified
name | string | no | The name of the person to modify
state | string | no | The US state of the phone number to modify

## Get All Numbers

```ruby
require 'phoneNumberStorer'

api = phoneNumberStorer::APIClient.getAllNumbers!()
api.phoneBook.get
```

```python
import phoneNumberStorer

api = phoneNumberStorer.getAllNumbers()
api.phoneBook.get()
```

```shell
curl "http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/getAllNumbers" \
  -H
```

```javascript
const phoneNumberStorer = require('phoneNumberStorer');

let api = phoneNumberStorer.getAllNumbers();
let phoneNumberStorer = api.phoneBook.get();
```

> The above command returns the following HTTP / JSON responses:

```HTTP
			200	- Success
			400 - Invalid request
```

```JSON
[
	{
		"phoneNumber": 2024441234,
		"name":"Abraham Lincoln",
		"state":"DC"	
	},
	{
		"phoneNumber": 9168458510,
		"name":"Arnold Schwarzenegger",
		"state":"CA"
	}
]	
```

This endpoint returns all phone number records from the phone book.

### HTTP Request

`GET http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/getAllNumbers`

### Query Parameters

This method takes no parameters.

## Get Number Details

```ruby
require 'phoneNumberStorer'

api = phoneNumberStorer::APIClient.getNumberDetails!(9168458510)
api.phoneBook.get
```

```python
import phoneNumberStorer

api = phoneNumberStorer.getNumberDetails(9168458510)
api.phoneBook.get()
```

```shell
curl "http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/getNumberDetails" \
  -H 9168458510
```

```javascript
const phoneNumberStorer = require('phoneNumberStorer');

let api = phoneNumberStorer.getNumberDetails(9168458510);
let phoneNumberStorer = api.phoneBook.get();
```

> The above command returns the following HTTP / JSON responses:

```HTTP
			200	- Success
			400 - Invalid request
			1010 - Invalid phone number
```

```JSON
{
	"phoneNumber": 9168458510,
	"name":"Arnold Schwarzenegger",
	"state":"CA"
}
```

This endpoint returns the details of a particular phone number record from the phone book.

### HTTP Request

`GET http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/getNumberDetails`

### Query Parameters

Parameter | Type | Required | Description
--------- | ------- | ----- | ------
phoneNumber | uint64 | yes | The 10-digit phone number to identify the record that should be fetched

## Delete a Number

```ruby
require 'phoneNumberStorer'

api = phoneNumberStorer::APIClient.deleteRecord!(9168458510)
api.phoneBook.delete
```

```python
import phoneNumberStorer

api = phoneNumberStorer.deleteRecord(9168458510)
api.phoneBook.delete()
```

```shell
curl "http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/deleteRecord" \
  -H 9168458510
```

```javascript
const phoneNumberStorer = require('phoneNumberStorer');

let api = phoneNumberStorer.deleteRecord(9168458510);
let phoneNumberStorer = api.phoneBook.delete();
```

> The above command returns the following HTTP / JSON responses:

```HTTP
			200	- Success
			400 - Invalid request
			1010 - Invalid phone number
```

```JSON
{
	"phoneNumber": 9168458510,
	"name":"Arnold Schwarzenegger",
	"state":"CA"
}
```

This endpoint returns the details of a particular phone number record from the phone book.

### HTTP Request

`DELETE http://example.com/api/phoneNumberStorer/{phoneBookID}/actions/deleteRecord`

### Query Parameters

Parameter | Type | Required | Description
--------- | ------- | ----- | ------
phoneNumber | uint64 | yes | The 10-digit phone number to identify the record that should be deleted

