---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell

toc_footers:
  - <a href='https://usealan.com/'>Sign Up for API Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Usealan API
---

# Introduction

Welcome to the Usealan API! You can use our API to access various API endpoints, which can get information about leads, appointments, messages and campaigns. Everything related to your business.

You can view code examples in the dark area to the right.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: Bearer abcdefgh12345678"
```

> Make sure to replace `abcdefgh12345678` with your API key.

Usealan uses API keys to allow access to the API. You can view your API key in your [admin portal](https://usealan.com/).

Usealan expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer abcdefgh12345678`

<aside class="notice">
You must replace <code>abcdefgh12345678</code> with your personal API key.
</aside>

# Users

## End Users

```shell
curl "https://api.usealan.com/v1/end_users" \
  -X GET \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcdefgh12345678"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "end_users": [
      {
        "id": "1001",
        "user_name": "john1",
        "user_code": "abcd1234",
        "first_name": "John",
        "last_name": "Doe",
        "full_name": "John Doe",
        "displayname": "John Doe",
        "email": "john@mail.com",
        "created_at": "2022-01-01 16:30:00"
      },
      {
        "id": "1002",
        "user_name": "james1",
        "user_code": "defg5678",
        "first_name": "James",
        "last_name": "Doe",
        "full_name": "James Doe",
        "displayname": "James Biz",
        "email": "james@mail.com",
        "created_at": "2022-02-02 13:00:00"
      }
    ],
    "code": 200,
    "message": "Successful operation."
  }
}
```

Gets list of end users associated to current user.

### HTTP Request

`GET https://api.usealan.com/v1/end_users`

# Appointments

## Mark Showed

```shell
curl "https://api.usealan.com/v1/mark_show/<appointment_id>" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcdefgh12345678"
```

> The above command returns JSON structured like this:

```json
{
  "data": null,
  "code": 200,
  "message": "Appointment <appointment_id> successfully marked as showed."
}
```

Marks appointment as 'Showed'.

### HTTP Request

`POST https://api.usealan.com/v1/mark_show/<appointment_id>`

### Query Parameters

Parameter | Description
--------- | -----------
appointment_id | ID of the appoinment to mark as 'Showed'.

## Mark No Showed

```shell
curl "https://api.usealan.com/v1/mark_no_show/<appointment_id>" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcdefgh12345678"
```

> The above command returns JSON structured like this:

```json
{
  "data": null,
  "code": 200,
  "message": "Appointment <appointment_id> successfully marked as no showed."
}
```

Marks appointment as ‘No Showed’.

### HTTP Request

`POST https://api.usealan.com/v1/mark_no_show/<appointment_id>`

### Query Parameters

Parameter | Description
--------- | -----------
appointment_id | ID of the appoinment to mark as 'No Showed'.

## Mark Sold

```shell
curl "https://api.usealan.com/v1/mark_sold/<appointment_id>" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcdefgh12345678"
  -d '{
    "down_payment": 70,
    "annual_contract_value": 5000
  }'
```

> The above command returns JSON structured like this:

```json
{
  "data": null,
  "code": 200,
  "message": "Appointment <appointment_id> successfully marked as sold."
}
```

Marks appointment as ‘Sold’.

### HTTP Request

`POST https://api.usealan.com/v1/mark_sold/<appointment_id>`

### Query Parameters

Parameter | Description
--------- | -----------
appointment_id | ID of the appoinment to mark as 'Sold'.
down_payment | Down payment value, double greater or equal than 0.
annual_contract_value | Annual contract value, double greater or equal than 0.

# Stats

## Main Stats

```shell
curl "https://api.usealan.com/v1/stats/<user_id>?start_date=YYYY-MM-DD&end_date=YYYY-MM-DD" \
  -X GET \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcdefgh12345678"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "business_details": {
      "id": "1001",
      "name": "John Doe",
      "email": "john@mail.com"
    },
    "leads": 239,
    "schedules": 75,
    "shows": 35,
    "solds": 25,
    "start_date": "2022-12-01 00:00:00",
    "end_date": "2022-12-31 23:59:59"
  },
  "code": 200,
  "message": "Successful operation."
}
```

Gets general stats for a specific user. If no date range is specified, lifetime stats will be returned.

### HTTP Request

`GEThttps://api.usealan.com/v1/stats/<user_id>?start_date=YYYY-MM-DD&end_date=YYYY-MM-DD`

### Query Parameters

Parameter | Description
--------- | -----------
user_id | ID of the end user.
start_date | (Optional) YYYY-MM-DD Start date for query.
end_date | (Optional) YYYY-MM-DD End date for query. It can't be less than the start date.
