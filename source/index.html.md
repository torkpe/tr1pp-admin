---
title: API Reference

# language_tabs: # must be one of https://git.io/vQNgJ

#   - javascript

# toc_footers:
#   -

# includes:
#   - errors

search: true
---

# Introduction

## Admin API Design

`base URI` is http://3.9.38.52:4501/admin/



# MAKING REQUESTS

Aside the endpoints; login and signin, users are required to to provide an authorization token to utilize the various endpoints.

A token is generated after successful login or successful confirmation. This token is attached to requests as headers or body.


`Authorization: payload.secret.expiration date`

# Admin

## Admin Login

> Request body

```json
{"email":"username@email.com","password":"password"},

```
> Response body

```json
{
  "data":
    {
      "adminName": "first last",
      "status": "ACTIVE",
      "lastName": "last",
      "regionId": "c943e3887806ea974aaab83698e0cab5",
      "profileImage": "https://s3.amazonaws.com/tr1ppupload01_profile/tr1pp-LGGQc-man-image.png",
      "adminId": "04c80069297d7b5fb8ea5b7e53539cb4",
      "postalCode": "lagos",
      "isTeamLead": false,
      "category": "8d8dac51580302d06d723bff587cce67",
      "city": "lagos",
      "firstName": "first",
      "section": null,
      "subDepartment": "a4f0337dc39c963882526d38933e3add",
      "roleId": "cb7f7fd2331dfdbce606c5ae003b60a1",
      "state": "lagos",
      "changePasswordOnFirstLogin": false,
      "email": "username@email.com",
      "department": "7fd3bded7ad86077da221eff1607ac5d",
      "createdAt": 1562453398,
      "jobTitle": "Operations Analyst",
      "phoneNumber": "08055573128",
      "reason": null,
      "isOnline": true,
      "zoneId": "dfff35e0722b7a4e2dd3f93c5795e022",
      "language": null,
      "dob": "1989-07-26",
      "adminType": null,
      "firstLogin": false,
      "sex": null,
      "resetPassword": null,
      "devices": [],
      "iso2": "NG",
      "team": [
        "Driver Partner Payment",
        "general",
        "Driver Partner Registration",
        "Driver Partner Account"
      ],
      "region": null,
      "streetAddress": "20 Test",
      "role": {
        "otp": "3601",
        "name": "Global_Admin_L1",
        "policy": { "admin": 5, "superadmin": 3 },
        "accessLevel": "GLOBAL",
        "sensitiveDataAccess": true,
        "description": "Can login to all admin panels globally and perform all actions"
      },
      "expirySeconds": 86400,
      "lastRead": 1578559616539,
      "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ996de6594e1c.eyJwaG9uZV9udW1iZXIiOiIwODA1NTU3MzEyOCIsImxhc3RfbmFtZSI6IkF3b2RvbGEiLCJyZWdpb25faWQiOiJjOTQzZTM4ODc4MDZlYTk3NGFhYWI4MzY5OGUwY2FiNSIsImxhc3RfcmVhZCI6MTU3ODU1OTYxNjUzOSwicHJvZmlsZV9pbWFnZSI6Imh0dHBzOi8vczMuYW1hem9uYXdzLmNvbS90cjFwcHVwbG9hZDAxL2FkbWluX3Byb2ZpbGUvdHIxcHAtTEdHUWMtbWFuLWltYWdlLnBuZyIsInVwZGF0ZWRfYXQiOjE1NzYwODI4MjksImFkbWluX2lkIjoiMDRjODAwNjkyOTdkN2I1ZmI4ZWE1Yjdl"
    }
}
```
This endpoint logs in admin.

### HTTP Request

`Post /login`

### Request
* Body (application/json)


### Response
* Status: 200 success
* Body (application/json)

## Forgot password

> Request body

```json
{"email":"dayoajisebutu@gmail.com"},
```
> Response body

```json
{"message":"A link has been sent to your email."}
```
This endpoint sends forgot password link to admin's email

### HTTP Request

`Post /password/forgot`

### Request
* Body (application/json)


### Response
* Status: 200 success
* Body (application/json)


## Online

> Request body

```json

{"putOnline": false},


```
> Response body

```json
{"message":"Now you are offline"}
```
This endpoint updates admin's status to online or offline

### HTTP Request

`Put /online`

### Request
* Body (application/json)


### Response
* Status: 200 success
* Body (application/json)

## Get Admins

### HTTP Request

`Get /admins`

> Response body

```json
{
  "data": [
    {
      "phoneNumber": "08102505206",
      "lastName": "Oluwaseun",
      "regionId": "c943e3887806ea974aaab83698e0cab5",
      "profileImage": "https://s3.amazonaws.com/tr1ppupload01_profile/tr1pp-a4dRr-pers.png",
      "adminId": "f32ac8a854e5e4fd177043a83bc9093d",
      "postalCode": "2301",
      "isTeamLead": false,
      "category": "8d8dac51580302d06d723bff587cce67",
      "city": "Lagos",
      "firstName": "Temitope",
      "section": null,
      "subDepartment": "20384d82ff6316d46a1c8d3cd0d4d9de",
      "roleId": "7cc083217ef14d8e71592cff8dfef8cf",
      "state": "lagos",
      "email": "temitope.emmanuel63@gmail.com",
      "department": "4aff157154cbfe62cd6ce681cf2a50ef",
      "jobTitle": "Automation Tester",
      "status": "ACTIVE",
      "reason": null,
      "isOnline": false,
      "otp": "9093",
      "region": null,
      "zoneId": "dfff35e0722b7a4e2dd3f93c5795e022",
      "language": null,
      "dob": "1995-09-14",
      "adminType": null,
      "firstLogin": false,
      "sex": null,
      "devices": [],
      "iso2": "NG",
      "team": ["Driver Partner Payment"],
      "created_at": 1575539778,
      "street_address": "Osapa london"
    }
  ],
  "message": "Admins retrieved"
}
```
This endpoint gets all admins.

### Response
* Status: 200 success
* Body (application/json)

## Get Driver

### HTTP Request

`Get /drivers/:id`

> Response body

```json
{
  "data": {
    "driverType": 0,
    "lastName": "driver",
    "inUseBy": "415e3b50561ed630445185d13f519735",
    "iso2": "NG",
    "serviceStatus": "Disengaged",
    "documents_verified": 1,
    "referralCode": "RIDR6634",
    "holdType": null,
    "issues": [],
    "city": "Lagos",
    "firstName": "richie",
    "documents": [],
    "driverImage": "https://s3.amazonaws.com/tr1ppupload01/driver_profile/tr1pp_a1b12712c749108f986c73a33ac816a3_465f252f34c4ce5edc485eb082feaaea",
    "approvalStatus": false,
    "paymentInfo": [],
    "snId": "NG-RIDR6634",
    "walletId": "b76da76cfb73511fc163dde2dcde7102",
    "driverMobile": "+234-8035436136",
    "inUse": true,
    "vehicleVerified": 0,
    "address": "mushin",
    "statusReason": null,
    "zoneId": "dfff35e0722b7a4e2dd3f93c5795e022",
    "bankDetailsVerified": 1,
    "dob": "1996-01-02T12:29:11.070Z",
    "gender": 0,
    "createdAt": 1577957002,
    "driverEmail": "talktoriche@yahoo.com",
    "_id": "a1b12712c749108f986c73a33ac816a3",
    "status": "Disengaged",
    "pendingDocs": [],
    "devices": [],
    "team": ["Driver Partner Payment"],
  }
}

```
This endpoint gets a driver

## Entries

### HTTP Request

`Get /drivers`

> Response body

```json
{
  "data":  [
    {
      "driverType": 0,
      "lastName": "driver",
      "inUseBy": "415e3b50561ed630445185d13f519735",
      "iso2": "NG",
      "serviceStatus": "Disengaged",
      "documents_verified": 1,
      "referralCode": "RIDR6634",
      "holdType": null,
      "issues": [],
      "city": "Lagos",
      "firstName": "richie",
      "documents": [],
      "driverImage": "https://s3.amazonaws.com/tr1ppupload01/driver_profile/tr1pp_a1b12712c749108f986c73a33ac816a3_465f252f34c4ce5edc485eb082feaaea",
      "approvalStatus": false,
      "paymentInfo": [],
      "snId": "NG-RIDR6634",
      "walletId": "b76da76cfb73511fc163dde2dcde7102",
      "driverMobile": "+234-8035436136",
      "inUse": true,
      "vehicleVerified": 0,
      "address": "mushin",
      "statusReason": null,
      "zoneId": "dfff35e0722b7a4e2dd3f93c5795e022",
      "bankDetailsVerified": 1,
      "dob": "1996-01-02T12:29:11.070Z",
      "gender": 0,
      "createdAt": 1577957002,
      "driverEmail": "talktoriche@yahoo.com",
      "_id": "a1b12712c749108f986c73a33ac816a3",
      "status": "Disengaged",
      "pendingDocs": [],
      "devices": [],
      "team": ["Driver Partner Payment"]
    }
  ]
}
```
### Response
* Status: 200 success
* Body (application/json)

### URL Query Parameters

Parameter | Description
--------- | -----------
zoneId | Selected zone id
regionId | Selected zone id
skip | Number of entries to skip in DB
limit | Number of entries to return from DB

### URL Optional Query Parameters

Parameter | Description
--------- | -----------
verificationStatus | has value of boolean
approvalStatus | has value of boolean
status | String

### Query Sample

`status=pending%20failed%20passed&skip=10&limit=10&regionId=278372hd7y8dy2387yd72g&zoneId=29373927dh2dh872h29hd92&verificationStatus=true&approvalStatus=true`

## Error Response


{
  "error": {
    "message": "Some error message",
    "status": error status code
  }
 }

