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
