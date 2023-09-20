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
    ]  
  },
  "code": 200,
  "message": "Successful operation."
}
```

Gets list of end users associated to current user.

### HTTP Request

`GET https://api.usealan.com/v1/end_users?q=<criteria>`

### Query Parameters

Parameter | Description
--------- | -----------
q | (Optional) Search parameter to attempt to match leads by name, user_name or email.

# Leads

## Leads List

```shell
curl "https://api.usealan.com/v1/leads" \
  -X GET \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcdefgh12345678"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "leads": [
      {
        "id": "12345",
        "first_name": "John",
        "last_name": "Doe",
        "email": "john.doe@mail.com",
        "phone": "1122334455",
        "source": "click_funnel",
        "status": "unchecked",
        "campaign": "Sales Consultation",
        "created_at": "2023-08-20 19:12:16",
        "schedule_date_time": "2023-08-30 19:00:00",
        "sms_initiated": "2023-08-21 04:01:45",
        "last_message_sent": "2023-09-03 11:22:22",
        "last_message_reply": "2023-09-02 08:01:45"
      },
      {
        "id": "12345",
        "first_name": "James",
        "last_name": "Doe",
        "email": "james.doe@mail.com",
        "phone": "6677889900",
        "source": "click_funnel",
        "status": "unchecked",
        "campaign": "Sales Consultation",
        "created_at": "2023-08-21 19:12:16",
        "schedule_date_time": "2023-09-01 19:00:00",
        "sms_initiated": "2023-08-22 04:01:45",
        "last_message_sent": "2023-09-04 11:22:22",
        "last_message_reply": "2023-09-02 10:01:45"
      }
    ],
    "page": 1,
    "per_page": 50,
    "total": 2,
    "pages": 0,
    "start_date": "2023-08-20 00:00:00",
    "end_date": "2023-09-20 23:59:59"
  },
  "code": 200,
  "message": "Successful operation."
}
```

Gets list of leads for a specific user ordered from first. If no date range is specified last month will be used as default.

### HTTP Request

`GET https://api.usealan.com/v1/leads/<user_id>?start_date=<date>&end_date=<date>&q=<criteria>`

### Query Parameters

Parameter | Description
--------- | -----------
user_id | ID of the end user.
start_date | (Optional) YYYY-MM-DD Start date for query.
end_date | (Optional) YYYY-MM-DD End date for query. It can't be less than the start date.
q | (Optional) Search parameter to attempt to match leads by name, email or phone number.

# Appointments

## Appointments List

```shell
curl "https://api.usealan.com/v1/appointments/<user_id>?start_date=YYYY-MM-DD&end_date=YYYY-MM-DD" \
  -X GET \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcdefgh12345678"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "appointment_id": "140124",
      "appointment_status": "unchecked",
      "lead_name": "Mariam Mustafa",
      "lead_phone_number": "4148404738",
      "campaign": "The challenge",
      "appointment_date": "2020-07-06",
      "appointment_start_time": "12:00:00",
      "appointment_end_time": "12:30:00",
      "end_user_note": "",
      "down_payment": 0,
      "total_contract_value": 0
    },
    {
      "appointment_id": "139223",
      "appointment_status": "unchecked",
      "lead_name": "mark koss",
      "lead_phone_number": "2626139824",
      "campaign": "The challenge",
      "appointment_date": "2020-07-06",
      "appointment_start_time": "19:00:00",
      "appointment_end_time": "19:30:00",
      "end_user_note": "",
      "down_payment": 0,
      "total_contract_value": 0
    }
  ],
  "code": 200,
  "message": "Successful operation."
}
```

Gets list of appointments for a specific user ordered from last. If no date range is specified a limit of 50 appointments will be applied.

### HTTP Request

`GET https://api.usealan.com/v1/appointments/<user_id>?start_date=YYYY-MM-DD&end_date=YYYY-MM-DD`

### Query Parameters

Parameter | Description
--------- | -----------
user_id | ID of the end user.
start_date | (Optional) YYYY-MM-DD Start date for query.
end_date | (Optional) YYYY-MM-DD End date for query. It can't be less than the start date.

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
    "total_amount": 345,
    "amount_down": 73,
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
