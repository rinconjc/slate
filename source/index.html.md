---
title: API Reference
language_tabs:
  - shell
  - java
toc_footers:
 - <a href='#'>Sign Up for a Developer Key</a>
includes:
    - errors
search: true
---
# Introduction

We have language bindings in java! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.
### Version
Version: 1.0.2

### URI scheme
BasePath: /
Schemes: HTTP, HTTPS

# Payer


null

## Get registered payers
```shell
curl "/v2/payer" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.getPayers(limit, offset, order, orderBy, drn, firstName, lastName, email, contactNumber, cardBin, cardLast4, cardHolder, bsb, bankAccountNumber, bankAccountName, status);

```

> The above command returns JSON structured like this:

```json
{
  "summary" : {
    "limit" : 1,
    "offset" : 1,
    "order" : "ASC",
    "orderBy" : "str",
    "total" : 1
  },
  "results" : [ {
    "userName" : "str",
    "firstName" : "str",
    "lastName" : "str",
    "emailAddress" : "str",
    "mobileNumber" : "str",
    "id" : 1,
    "lastLogin" : "2016-03-03T10:15:30.00Z",
    "intlPhoneNumber" : "str",
    "status" : "MIGRATION_READY",
    "address" : {
      "country" : "str",
      "state" : "NSW",
      "suburb" : "str",
      "postCode" : "str",
      "streetLine1" : "str",
      "streetLine2" : "str",
      "australian" : true
    },
    "subscriptions" : [ {
      "id" : 1,
      "warningMessage" : "str",
      "displayText" : "str",
      "shortName" : "str"
    } ],
    "dob" : "2016-03-03T10:15:30.00Z",
    "displayName" : "str",
    "landLine" : "str"
  } ]
}
```

### HTTP Request
`GET /v2/payer`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|limit|false|integer (int32)||
|offset|false|integer (int32)||
|order|false|enum (ASC, DESC)||
|orderBy|false|string||
|drn|false|string||
|firstName|false|string||
|lastName|false|string||
|email|false|string||
|contactNumber|false|string||
|cardBin|false|string||
|cardLast4|false|string||
|cardHolder|false|string||
|bsb|false|string||
|bankAccountNumber|false|string||
|bankAccountName|false|string||
|status|false|multi enum (MIGRATION_READY, SELF_REGISTRATION_STARTED, BILLER_REGISTRATION_STARTED, MIGRATION_STARTED, SELF_REGISTRATION_COMPLETE_DETAILS, BILLER_REGISTRATION_CONFIRM_DETAILS, MIGRATION_CONFIRM_DETAILS, ACTIVE, INACTIVE) array||


### Responses for status codes
|200|400|403|
|----|----|----|
|[PayerSearchResult](#payersearchresult)|[ErrorValue](#errorvalue) array|[ErrorValue](#errorvalue) array|


## Create a Payer
```shell
curl "/v2/payer" -X POST -d @- << EOF 
{
  "userName" : "str",
  "firstName" : "str",
  "lastName" : "str",
  "emailAddress" : "str",
  "mobileNumber" : "str",
  "id" : 1,
  "lastLogin" : "2016-03-03T10:15:30.00Z",
  "status" : "MIGRATION_READY",
  "salutation" : "str",
  "intlPhoneNumber" : "str",
  "address" : {
    "country" : "str",
    "state" : "NSW",
    "suburb" : "str",
    "postCode" : "str",
    "streetLine1" : "str",
    "streetLine2" : "str",
    "australian" : true
  },
  "dob" : "2016-03-03T10:15:30.00Z",
  "preferredContactMethod" : "EMAIL",
  "channel" : "INTERNET",
  "subscriptions" : [ 1 ],
  "captchaResponse" : "str",
  "landLine" : "str"
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.createPayer(body);

```

> The above command returns JSON structured like this:

```json
{
  "userName" : "str",
  "firstName" : "str",
  "lastName" : "str",
  "emailAddress" : "str",
  "mobileNumber" : "str",
  "id" : 1,
  "lastLogin" : "2016-03-03T10:15:30.00Z",
  "intlPhoneNumber" : "str",
  "status" : "MIGRATION_READY",
  "address" : {
    "country" : "str",
    "state" : "NSW",
    "suburb" : "str",
    "postCode" : "str",
    "streetLine1" : "str",
    "streetLine2" : "str",
    "australian" : true
  },
  "subscriptions" : [ {
    "id" : 1,
    "warningMessage" : "str",
    "displayText" : "str",
    "shortName" : "str"
  } ],
  "dob" : "2016-03-03T10:15:30.00Z",
  "displayName" : "str",
  "landLine" : "str"
}
```

### HTTP Request
`POST /v2/payer`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|userName|true|string|Email address|
|firstName|true|string|First name|
|lastName|true|string|Last name|
|emailAddress|false|string||
|mobileNumber|false|string||
|id|false|integer (int64)||
|lastLogin|false|string (date-time)||
|status|false|enum (MIGRATION_READY, SELF_REGISTRATION_STARTED, BILLER_REGISTRATION_STARTED, MIGRATION_STARTED, SELF_REGISTRATION_COMPLETE_DETAILS, BILLER_REGISTRATION_CONFIRM_DETAILS, MIGRATION_CONFIRM_DETAILS, ACTIVE, INACTIVE)||
|salutation|false|string|Salutation|
|intlPhoneNumber|false|string||
|address|false|[AddressDto](#addressdto)||
|dob|false|string (date-time)|Date of birth (yyyy-MM-dd)|
|preferredContactMethod|false|enum (EMAIL, LANDLINE, MOBILE)|Preferred contact method|
|channel|false|enum (INTERNET, IVR, BPAY, AUSTRALIA_POST, LOCKED_BAG, PAYER_PORTAL_ONE_TIME, PAYER_PORTAL, BILLER_PORTAL, BILLER_PORTAL_VIRTUAL_TERMINAL, ADMIN_PORTAL, API, ECOM_TRANSPARENT_REDIRECT, ECOM_IFRAME, ECOM_HOSTED_PAYMENT_PAGE, API_EBIX, API_EDGEWISE, API_GALLAGHERS, API_GENKAN, API_RAW_IDEAS, AUCTION_PAY)||
|subscriptions|false|integer (int32) array||
|captchaResponse|false|string||
|landLine|false|string|Contact phone number|


### Responses for status codes
|200|201|400|
|----|----|----|
|[PayerResponseDto](#payerresponsedto)|



This operation is to create a Payer. <br>Any authenticated user can create a Payer but for the authenticated username only.<br>TODO - implement security once API infrastructure is in place.

## Payer enquiry email notification
```shell
curl "/v2/payer/enquiry" -X POST -d @- << EOF 
{
  "phoneNumber" : "str",
  "payerId" : 1,
  "drn" : "str"
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.payerEnquiry(body);

```

### HTTP Request
`POST /v2/payer/enquiry`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|phoneNumber|true|string||
|payerId|false|integer (int64)||
|drn|false|string||


### Responses for status codes
|400|204|
|----|----|
||


## Is user ready for migration?
```shell
curl "/v2/payer/migration-ready" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.migrationReady(email);

```

> The above command returns JSON structured like this:

```json
{
  "migrationReady" : true
}
```

### HTTP Request
`GET /v2/payer/migration-ready`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|email|true|string|Payer's email to determine|


### Responses for status codes
|200|
|----|
|[MigrationReadyResponse](#migrationreadyresponse)|



This operation checks if the payer is ready for migration

## Resets payers password
```shell
curl "/v2/payer/password" -X POST -d @- << EOF 
{
  "email" : "str",
  "captchaResponse" : "str"
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.resetPassword(body);

```

### HTTP Request
`POST /v2/payer/password`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|email|true|string||
|captchaResponse|false|string||


### Responses for status codes
|400|204|
|----|----|
||


## Retrieve a Payer
```shell
curl "/v2/payer/{id}" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.retrieve(id);

```

> The above command returns JSON structured like this:

```json
{
  "userName" : "str",
  "firstName" : "str",
  "lastName" : "str",
  "emailAddress" : "str",
  "mobileNumber" : "str",
  "id" : 1,
  "lastLogin" : "2016-03-03T10:15:30.00Z",
  "intlPhoneNumber" : "str",
  "status" : "MIGRATION_READY",
  "address" : {
    "country" : "str",
    "state" : "NSW",
    "suburb" : "str",
    "postCode" : "str",
    "streetLine1" : "str",
    "streetLine2" : "str",
    "australian" : true
  },
  "subscriptions" : [ {
    "id" : 1,
    "warningMessage" : "str",
    "displayText" : "str",
    "shortName" : "str"
  } ],
  "dob" : "2016-03-03T10:15:30.00Z",
  "displayName" : "str",
  "landLine" : "str"
}
```

### HTTP Request
`GET /v2/payer/{id}`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)||


### Responses for status codes
|200|201|400|
|----|----|----|
|[PayerResponseDto](#payerresponsedto)|



This operation is to retrieve Payer details. <br>Any authenticated user can retrieve a Payer but for the authenticated username only.<br>TODO - implement security once API infrastructure is in place.

## Updates a Payer (for browser compatibility only)
```shell
curl "/v2/payer/{id}" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.updateCompatibility(id, body);

```

> The above command returns JSON structured like this:

```json
{
  "userName" : "str",
  "firstName" : "str",
  "lastName" : "str",
  "emailAddress" : "str",
  "mobileNumber" : "str",
  "id" : 1,
  "lastLogin" : "2016-03-03T10:15:30.00Z",
  "intlPhoneNumber" : "str",
  "status" : "MIGRATION_READY",
  "address" : {
    "country" : "str",
    "state" : "NSW",
    "suburb" : "str",
    "postCode" : "str",
    "streetLine1" : "str",
    "streetLine2" : "str",
    "australian" : true
  },
  "subscriptions" : [ {
    "id" : 1,
    "warningMessage" : "str",
    "displayText" : "str",
    "shortName" : "str"
  } ],
  "dob" : "2016-03-03T10:15:30.00Z",
  "displayName" : "str",
  "landLine" : "str"
}
```

### HTTP Request
`PUT /v2/payer/{id}`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)||


### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|userName|true|string|Email address|
|firstName|true|string|First name|
|lastName|true|string|Last name|
|emailAddress|false|string||
|mobileNumber|false|string||
|id|false|integer (int64)||
|lastLogin|false|string (date-time)||
|status|false|enum (MIGRATION_READY, SELF_REGISTRATION_STARTED, BILLER_REGISTRATION_STARTED, MIGRATION_STARTED, SELF_REGISTRATION_COMPLETE_DETAILS, BILLER_REGISTRATION_CONFIRM_DETAILS, MIGRATION_CONFIRM_DETAILS, ACTIVE, INACTIVE)||
|salutation|false|string|Salutation|
|intlPhoneNumber|false|string||
|address|false|[AddressDto](#addressdto)||
|dob|false|string (date-time)|Date of birth (yyyy-MM-dd)|
|preferredContactMethod|false|enum (EMAIL, LANDLINE, MOBILE)|Preferred contact method|
|channel|false|enum (INTERNET, IVR, BPAY, AUSTRALIA_POST, LOCKED_BAG, PAYER_PORTAL_ONE_TIME, PAYER_PORTAL, BILLER_PORTAL, BILLER_PORTAL_VIRTUAL_TERMINAL, ADMIN_PORTAL, API, ECOM_TRANSPARENT_REDIRECT, ECOM_IFRAME, ECOM_HOSTED_PAYMENT_PAGE, API_EBIX, API_EDGEWISE, API_GALLAGHERS, API_GENKAN, API_RAW_IDEAS, AUCTION_PAY)||
|subscriptions|false|integer (int32) array||
|splashClosed|false|boolean||
|securityCode|false|string||
|password|false|string array||
|landLine|false|string|Contact phone number|


### Responses for status codes
|200|201|400|
|----|----|----|
|[PayerResponseDto](#payerresponsedto)|



This operation is to update a Payer. <br>Any authenticated user can create a Payer but for the authenticated username only.<br>TODO - implement security once API infrastructure is in place.

## Remove the payer and associated linkages.
```shell
curl "/v2/payer/{id}" -X DELETE
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.deletePayer(id);

```

### HTTP Request
`DELETE /v2/payer/{id}`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)||


### Responses for status codes
|400|204|
|----|----|
||


## Updates a Payer
```shell
curl "/v2/payer/{id}" -X PATH -d @- << EOF 
{ }
EOF
```

## Get Payer to DRN associations
```shell
curl "/v2/payer/{id}/drn" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.getPayerDrnLinks(id, payerId, limit, offset, order, orderBy, includeInactive);

```

> The above command returns JSON structured like this:

## (This has been deprecated. Please use the POST/PUT/DELETE /{payerId}/drn/{drn} instead) Modify Payer to DRN and IVR code associations
```shell
curl "/v2/payer/{id}/drn" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.modifyPayerDrnLinks(id, body);

```

> The above command returns JSON structured like this:

## Associate a DRN to a payer
```shell
curl "/v2/payer/{id}/drn" -X POST -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.associateDrnToPayer(id, body);

```

> The above command returns JSON structured like this:

```json
{
  "payerId" : 1,
  "drnId" : 1,
  "drn" : "str",
  "startDate" : "2016-03-03T10:15:30.00Z",
  "endDate" : "2016-03-03T10:15:30.00Z",
  "nickName" : "str",
  "status" : "ACTIVE",
  "ivrCode" : "str"
}
```

### HTTP Request
`POST /v2/payer/{id}/drn`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)||


### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|drn|true|string||
|ivrCode|false|string||
|nickname|false|string||


### Responses for status codes
|200|400|
|----|----|
|[PayerDrnDto](#payerdrndto)|[ErrorValue](#errorvalue) array|



<ul><li>400510: DRN is not valid </li><li>6000041: IVR Security code already in use </li><li>400511: Biller Account could not be resolved for DRN - [DRN] </li></ul>

## Update a payer's DRN association
```shell
curl "/v2/payer/{id}/drn/{drn}" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.updatePayerDrn(id, drn, body);

```

> The above command returns JSON structured like this:

## Associate a DRN to a payer
```shell
curl "/v2/payer/{id}/drn/{drn}" -X DELETE
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.dissociateDrnFromPayer(id, drn);

```

### HTTP Request
`DELETE /v2/payer/{id}/drn/{drn}`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)||
|drn|true|string||


### Responses for status codes
|201|400|
|----|----|
|[ErrorValue](#errorvalue) array|



<ul><li>400105, DRN not associated to payer</li></ul>

## Updates a Payer Email Address/ Username
```shell
curl "/v2/payer/{id}/email" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PayerApi;

ApiClient apiClient = new ApiClient();

PayerApi api = new PayerApi(apiClient);
api.updateEmail(id, body);

```

> The above command returns JSON structured like this:

```json
{
  "userName" : "str",
  "firstName" : "str",
  "lastName" : "str",
  "emailAddress" : "str",
  "mobileNumber" : "str",
  "id" : 1,
  "lastLogin" : "2016-03-03T10:15:30.00Z",
  "intlPhoneNumber" : "str",
  "status" : "MIGRATION_READY",
  "address" : {
    "country" : "str",
    "state" : "NSW",
    "suburb" : "str",
    "postCode" : "str",
    "streetLine1" : "str",
    "streetLine2" : "str",
    "australian" : true
  },
  "subscriptions" : [ {
    "id" : 1,
    "warningMessage" : "str",
    "displayText" : "str",
    "shortName" : "str"
  } ],
  "dob" : "2016-03-03T10:15:30.00Z",
  "displayName" : "str",
  "landLine" : "str"
}
```

### HTTP Request
`PUT /v2/payer/{id}/email`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)||


### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|captchaResponse|false|string||
|emailAddress|false|string||
|channel|false|enum (INTERNET, IVR, BPAY, AUSTRALIA_POST, LOCKED_BAG, PAYER_PORTAL_ONE_TIME, PAYER_PORTAL, BILLER_PORTAL, BILLER_PORTAL_VIRTUAL_TERMINAL, ADMIN_PORTAL, API, ECOM_TRANSPARENT_REDIRECT, ECOM_IFRAME, ECOM_HOSTED_PAYMENT_PAGE, API_EBIX, API_EDGEWISE, API_GALLAGHERS, API_GENKAN, API_RAW_IDEAS, AUCTION_PAY)||
|id|false|integer (int64)||


### Responses for status codes
|200|201|400|
|----|----|----|
|[PayerResponseDto](#payerresponsedto)|



This operation is used as the initial step to update the Payer's Email. It will accept the new email address, store it and then sends the 4 digit  security code to the Payer's current email address for verification.<br>Then a subsequent call to the Update Payer service will finalize the change to the Payer's Email,  which will verify the generated security code that this service had previously generated. <br>

# Bank token


null

## Retrieves a list of bank Tokens
```shell
curl "/v2/bank-token" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BanktokenApi;

ApiClient apiClient = new ApiClient();

BanktokenApi api = new BanktokenApi(apiClient);
api.getBankTokens(payerId);

```

> The above command returns JSON structured like this:

## Create a Bank Account token
```shell
curl "/v2/bank-token" -X POST -d @- << EOF 
{
  "bsb" : "str",
  "accountNumber" : "str",
  "accountName" : "str",
  "defaultFlag" : true,
  "token" : "str",
  "id" : 1,
  "payerId" : 1
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BanktokenApi;

ApiClient apiClient = new ApiClient();

BanktokenApi api = new BanktokenApi(apiClient);
api.createWalletAccount(body);

```

> The above command returns JSON structured like this:

```json
{
  "bsb" : "str",
  "accountNumber" : "str",
  "accountName" : "str",
  "defaultFlag" : true,
  "token" : "str",
  "id" : 1,
  "payerId" : 1,
  "warningMessageCode" : 1,
  "warningMessage" : "str",
  "bankBranch" : {
    "bsb" : "str",
    "city" : "str",
    "state" : "str",
    "financialName" : "str"
  },
  "created" : "2016-03-03T10:15:30.00Z",
  "updated" : "2016-03-03T10:15:30.00Z"
}
```

### HTTP Request
`POST /v2/bank-token`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|bsb|true|string||
|accountNumber|true|string||
|accountName|true|string||
|defaultFlag|false|boolean||
|token|false|string||
|id|false|integer (int64)||
|payerId|false|integer (int64)||


### Responses for status codes
|200|201|400|
|----|----|----|
|[BankAccountResponseDto](#bankaccountresponsedto)|



This operation is to create a Bank Account in the Payer's Wallet. <br>Any authenticated user can create a Bank Account but for the authenticated username only.<h4>Exceptions</h4><br/><table class='fullwidth'><thead><th>Code</th><th>Description</th></thead><tbody><tr><td width='15%' class='code'>400515</td><td>Wallet account does not exists</td></tr><tr><td width='15%' class='code'>400514</td><td>Account already exist for the payer</td></tr><tr><td width='15%' class='code'>400530</td><td>BSB does not exists</td></tr></tbody></table>

## Update a Bank Account token
```shell
curl "/v2/bank-token/{token}" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BanktokenApi;

ApiClient apiClient = new ApiClient();

BanktokenApi api = new BanktokenApi(apiClient);
api.updateWalletAccount(token, body);

```

> The above command returns JSON structured like this:

```json
{
  "bsb" : "str",
  "accountNumber" : "str",
  "accountName" : "str",
  "defaultFlag" : true,
  "token" : "str",
  "id" : 1,
  "payerId" : 1,
  "warningMessageCode" : 1,
  "warningMessage" : "str",
  "bankBranch" : {
    "bsb" : "str",
    "city" : "str",
    "state" : "str",
    "financialName" : "str"
  },
  "created" : "2016-03-03T10:15:30.00Z",
  "updated" : "2016-03-03T10:15:30.00Z"
}
```

### HTTP Request
`PUT /v2/bank-token/{token}`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|token|true|string|Bank account id to be updated|


### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|bsb|true|string||
|accountNumber|true|string||
|accountName|true|string||
|defaultFlag|false|boolean||
|token|false|string||
|id|false|integer (int64)||
|payerId|false|integer (int64)||


### Responses for status codes
|200|201|400|
|----|----|----|
|[BankAccountResponseDto](#bankaccountresponsedto)|



This operation is to update a Bank Account in the Payer's Wallet. <br>Any authenticated user can update a Bank Account but for the authenticated username only.<h4>Exceptions</h4><br/><table class='fullwidth'><thead><th>Code</th><th>Description</th></thead><tbody><tr><td width='15%' class='code'>400515</td><td>Wallet account does not exists</td></tr><tr><td width='15%' class='code'>400530</td><td>BSB does not exists</td></tr></tbody></table>

## Remove bank account from wallet for payer.
```shell
curl "/v2/bank-token/{token}" -X DELETE
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BanktokenApi;

ApiClient apiClient = new ApiClient();

BanktokenApi api = new BanktokenApi(apiClient);
api.deleteWalletAccount(token);

```

### HTTP Request
`DELETE /v2/bank-token/{token}`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|token|true|string|Bank account token which will be removed from payer|


### Responses for status codes
|400|
|----|
||



This operation removes the bank account from Payer <br>If the bank account removed is a default bank account for the payer, payer will not have a default account after this operation.<h4>Exceptions</h4><br/><table class='fullwidth'><thead><th>Code</th><th>Description</th></thead><tbody><tr><td width='15%' class='code'>400515</td><td>Wallet account does not exists</td></tr></tbody></table>

# Transaction


null

## Search for Transactions
```shell
curl "/v2/transaction" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.getTransactions(limit, offset, order, orderBy, payerIds, drn, minAmount, maxAmount, minTotalAmount, maxTotalAmount, fromDateTime, toDateTime, receiptNumber, billerId, cardFirstSixDigits, cardLastFourDigits, bsb, cardHolderName, accountNumber, paymentMethod, cardScheme, channel, messageType, status, scheduledPaymentOnly, scheduleId, includeInactiveDrns, dtrn, customerReference, customerTransactionId, ddaPaymentOnly, bulkDDAId, settlementDate);

```

> The above command returns JSON structured like this:

## Amount calculation for the transaction
## Create Card Transaction
## Confirm Card Transaction
```shell
curl "/v2/transaction/card/confirmation" -X POST -d @- << EOF 
{
  "dtrn" : 1,
  "settlementDate" : "2016-03-03T10:15:30.00Z",
  "responseCode" : "str",
  "responseMessage" : "str",
  "stan" : "str",
  "providerResponseCode" : "str",
  "providerResponseMessage" : "str",
  "responseTimestamp" : "2016-03-03T10:15:30.00Z",
  "paidUsing" : "CARD",
  "token" : "str",
  "cardInfo" : {
    "cardBin" : "str",
    "lastFourDigits" : "str",
    "cardHolderName" : "str",
    "expiryDate" : "str",
    "cardScheme" : "str"
  },
  "processorRef" : "str",
  "userType" : "MGL"
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.confirmCardTransactionV2(request);

```

> The above command returns JSON structured like this:

## Refund Card Transaction
## Validate Card Transaction
## Datetime query for a transaction
```shell
curl "/v2/transaction/datetime/dtrn/{dtrn}" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.getDateTimeForTransaction(dtrn);

```

> The above command returns JSON structured like this:

```json
{
  "transactionDateTime" : "2016-03-03T10:15:30.00Z"
}
```

### HTTP Request
`GET /v2/transaction/datetime/dtrn/{dtrn}`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|dtrn|true|integer (int64)||


### Responses for status codes
|200|404|
|----|----|
|[TransactionDateTimeDto](#transactiondatetimedto)|[ErrorContainerDto](#errorcontainerdto)|



This operation to return date time for a existing transaction, by DTRN

## Create Direct Debit Transaction
```shell
curl "/v2/transaction/direct-debit" -X POST -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.createAndValidateDebitTransaction(request, rootBillerId);

```

> The above command returns JSON structured like this:

## Send email receipt for a transaction
```shell
curl "/v2/transaction/receipt" -X POST -d @- << EOF 
{
  "transactionId" : 1,
  "recipientEmail" : "str"
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.emailReceipt(body);

```

### HTTP Request
`POST /v2/transaction/receipt`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|transactionId|false|integer (int64)||
|recipientEmail|false|string||


### Responses for status codes
|default|
|----|
||



This operation to sends a email receipt for the existing transaction

## Search for Transactions
## Get transaction summary
```shell
curl "/v2/transaction/summary/fromdate/{fromdate}/todate/{todate}" -X POST
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.summary(fromdate, todate);

```

> The above command returns JSON structured like this:

## Get surcharge calculation
## Total Amount calculation with fee and surcharge both for the transaction
## Requests Automatic/Asynchronous Card Payment cancellation
```shell
curl "/v2/transaction/{dtrn}/autoCancel" -X POST
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.sendAutomaticCardPaymentCancellation(dtrn, RESOURCE_TOKEN);

```

### HTTP Request
`POST /v2/transaction/{dtrn}/autoCancel`
### Header Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|RESOURCE_TOKEN|false|string||


### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|dtrn|true|integer (int64)||


### Responses for status codes
|201|303|
|----|----|
|[ErrorValue](#errorvalue) array|[ErrorValue](#errorvalue) array|


## Requests Card Payment cancellation
```shell
curl "/v2/transaction/{dtrn}/cancel" -X POST
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.sendCardPaymentCancellation(dtrn);

```

> The above command returns JSON structured like this:

```json
{
  "transactionStatus" : "APPROVED",
  "transactionId" : 1,
  "responseCode" : "str",
  "dtrn" : 1,
  "success" : true
}
```

### HTTP Request
`POST /v2/transaction/{dtrn}/cancel`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|dtrn|true|integer (int64)||


### Responses for status codes
|200|406|
|----|----|
|[SuccessResponse](#successresponse)|[ErrorValue](#errorvalue) array|


## Requests card transaction completion status
```shell
curl "/v2/transaction/{dtrn}/status" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.getTransactionStatus(dtrn, t);

```

> The above command returns JSON structured like this:

```json
{
  "transactionStatus" : "APPROVED",
  "transactionId" : 1,
  "responseCode" : "str",
  "dtrn" : 1,
  "success" : true
}
```

### HTTP Request
`GET /v2/transaction/{dtrn}/status`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|_t|false|string||


### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|dtrn|true|integer (int64)||


### Responses for status codes
|200|400|
|----|----|
|[SuccessResponse](#successresponse)|[FailureResponse](#failureresponse)|


## Return details of a transaction.
```shell
curl "/v2/transaction/{id}" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.TransactionApi;

ApiClient apiClient = new ApiClient();

TransactionApi api = new TransactionApi(apiClient);
api.getTransactionDetails(id);

```

> The above command returns JSON structured like this:

# Biller


null

## Search for Billers
```shell
curl "/v2/biller" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BillerApi;

ApiClient apiClient = new ApiClient();

BillerApi api = new BillerApi(apiClient);
api.getBillers(limit, offset, order, orderBy, id, rootBillerId, name, type, status, includeParents, ddaEnabled);

```

> The above command returns JSON structured like this:

```json
[ {
  "id" : 1,
  "type" : "GROUP_CUSTOMER",
  "name" : "str",
  "status" : "INACTIVE",
  "accessible" : true,
  "ddaEnabled" : true
} ]
```

### HTTP Request
`GET /v2/biller`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|limit|false|integer (int32)||
|offset|false|integer (int32)||
|order|false|enum (ASC, DESC)||
|orderBy|false|string||
|id|false|integer (int64)||
|rootBillerId|false|integer (int64)||
|name|false|string||
|type|false|string||
|status|false|string||
|includeParents|false|boolean||
|ddaEnabled|false|boolean||


### Responses for status codes
|200|400|
|----|----|
|[BillerSearchDto](#billersearchdto) array|[ErrorValue](#errorvalue) array|



This operation to search billers based on the following - id, name, status and type

## Get biller roots for user
```shell
curl "/v2/biller/list-root" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BillerApi;

ApiClient apiClient = new ApiClient();

BillerApi api = new BillerApi(apiClient);
api.getBillerRoots(permissionId);

```

> The above command returns JSON structured like this:

```json
[ {
  "id" : 1,
  "type" : "GROUP_CUSTOMER",
  "name" : "str",
  "status" : "str",
  "accessible" : true,
  "drn" : "str"
} ]
```

### HTTP Request
`GET /v2/biller/list-root`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|permission-id|false|integer (int64)|permission-id|


### Responses for status codes
|200|
|----|
|[BillerDto](#billerdto) array|



This operation is for getting distinct biller roots(ancestors) for a give user id

## Search for Billers
```shell
curl "/v2/biller/search" -X POST -d @- << EOF 
{
  "limit" : 1,
  "offset" : 1,
  "order" : "ASC",
  "orderBy" : "str",
  "id" : 1,
  "rootBillerId" : 1,
  "name" : "str",
  "type" : "str",
  "status" : "str",
  "pageInfo" : {
    "limit" : 1,
    "offset" : 1,
    "order" : "ASC",
    "orderBy" : "str"
  },
  "includeParents" : true,
  "ddaEnabled" : true
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BillerApi;

ApiClient apiClient = new ApiClient();

BillerApi api = new BillerApi(apiClient);
api.billerSearch(body);

```

> The above command returns JSON structured like this:

```json
[ {
  "id" : 1,
  "type" : "GROUP_CUSTOMER",
  "name" : "str",
  "status" : "INACTIVE",
  "accessible" : true,
  "ddaEnabled" : true
} ]
```

### HTTP Request
`POST /v2/biller/search`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|limit|false|integer (int32)||
|offset|false|integer (int32)||
|order|false|enum (ASC, DESC)||
|orderBy|false|string||
|id|false|integer (int64)||
|rootBillerId|false|integer (int64)||
|name|false|string||
|type|false|string||
|status|false|string||
|pageInfo|false|[Paging](#paging)||
|includeParents|false|boolean||
|ddaEnabled|false|boolean||


### Responses for status codes
|200|
|----|
|[BillerSearchDto](#billersearchdto) array|



This operation to search billers based on the following parameters - id, name, status and type

## Get biller hierarchy from id
```shell
curl "/v2/biller/tree" -X POST -d @- << EOF 
{
  "id" : 1,
  "pageInfo" : {
    "limit" : 1,
    "offset" : 1,
    "order" : "ASC",
    "orderBy" : "str"
  }
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BillerApi;

ApiClient apiClient = new ApiClient();

BillerApi api = new BillerApi(apiClient);
api.billerTree(body);

```

> The above command returns JSON structured like this:

```json
{
  "biller" : {
    "id" : 1,
    "type" : "GROUP_CUSTOMER",
    "name" : "str",
    "status" : "str",
    "accessible" : true,
    "drn" : "str"
  },
  "children" : [ {
    "id" : 1,
    "type" : "GROUP_CUSTOMER",
    "name" : "str",
    "status" : "str",
    "accessible" : true,
    "drn" : "str"
  } ]
}
```

### HTTP Request
`POST /v2/biller/tree`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|false|integer (int64)||
|pageInfo|false|[Paging](#paging)||


### Responses for status codes
|200|
|----|
|[BillerHierarchyDto](#billerhierarchydto)|



This operation is for viewing biller hierarchy

## Retrieve Biller details
```shell
curl "/v2/biller/{id}" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BillerApi;

ApiClient apiClient = new ApiClient();

BillerApi api = new BillerApi(apiClient);
api.getBillerDetails(id, rootBillerId);

```

> The above command returns JSON structured like this:

## Update Biller information
```shell
curl "/v2/biller/{id}" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BillerApi;

ApiClient apiClient = new ApiClient();

BillerApi api = new BillerApi(apiClient);
api.updateBiller(id, body, rootBillerId);

```

> The above command returns JSON structured like this:

## Get biller hierarchy from id
```shell
curl "/v2/biller/{id}/tree" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.BillerApi;

ApiClient apiClient = new ApiClient();

BillerApi api = new BillerApi(apiClient);
api.getBillerHierarchy(id, offset, limit, orderBy, order);

```

> The above command returns JSON structured like this:

```json
{
  "biller" : {
    "id" : 1,
    "type" : "GROUP_CUSTOMER",
    "name" : "str",
    "status" : "str",
    "accessible" : true,
    "drn" : "str"
  },
  "children" : [ {
    "id" : 1,
    "type" : "GROUP_CUSTOMER",
    "name" : "str",
    "status" : "str",
    "accessible" : true,
    "drn" : "str"
  } ]
}
```

### HTTP Request
`GET /v2/biller/{id}/tree`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|offset|false|integer (int32)|skips the first n records|
|limit|false|integer (int32)|maximum number of records to return|
|order-by|false|enum (name, id, type, status)|order-by field|
|order|false|enum (ASC, DESC)|sort order for results - ASC/DESC|


### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)|Biller Identifier|


### Responses for status codes
|200|
|----|
|[BillerHierarchyDto](#billerhierarchydto)|



This operation is for viewing biller hierarchy

# Payment


null

## Payment API endpoint used by Apigee
```shell
curl "/v2/payment" -X POST -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentApi;

ApiClient apiClient = new ApiClient();

PaymentApi api = new PaymentApi(apiClient);
api.mockApigeePayment(request, rootBillerId);

```

> The above command returns JSON structured like this:

## Process Bulk DDA payments - card/bank payments based on the registered payer's DRN
```shell
curl "/v2/payment/bulk-dda" -X POST -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentApi;

ApiClient apiClient = new ApiClient();

PaymentApi api = new PaymentApi(apiClient);
api.processBulkDDAPayment(transactionRequestDto, rootBillerId);

```

> The above command returns JSON structured like this:

```json
{
  "id" : 1,
  "customerBulkTransactionId" : "str",
  "responseTimestamp" : "2016-03-03T10:15:30.00Z",
  "total" : 1,
  "status" : "str",
  "totalErrors" : 1,
  "errors" : [ {
    "drn" : "str",
    "errorCode" : 1,
    "details" : "str",
    "message" : "str"
  } ]
}
```

### HTTP Request
`POST /v2/payment/bulk-dda`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|rootBillerId|false|integer (int64)||


### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|customerBulkTransactionId|false|string||
|paymentDDAs|false|[DDAPaymentRequest](#ddapaymentrequest) array||


### Responses for status codes
|200|400|
|----|----|
|[BulkDDAPaymentResponse](#bulkddapaymentresponse)|[ErrorValue](#errorvalue) array|



This operation is for processing  payments by a authorised biller

## Returns the status of a bulk payment
```shell
curl "/v2/payment/bulk-dda/{id}" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentApi;

ApiClient apiClient = new ApiClient();

PaymentApi api = new PaymentApi(apiClient);
api.getBulkPaymentStatus(id);

```

> The above command returns JSON structured like this:

```json
{
  "id" : 1,
  "customerBulkTransactionId" : "str",
  "responseTimestamp" : "2016-03-03T10:15:30.00Z",
  "total" : 1,
  "status" : "str",
  "totalErrors" : 1,
  "errors" : [ {
    "drn" : "str",
    "errorCode" : 1,
    "details" : "str",
    "message" : "str"
  } ]
}
```

### HTTP Request
`GET /v2/payment/bulk-dda/{id}`
### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)|Bulk Payment Identifier|


### Responses for status codes
|200|400|404|
|----|----|----|
|[BulkDDAPaymentResponse](#bulkddapaymentresponse)|[ErrorValue](#errorvalue) array|[ErrorValue](#errorvalue) array|



Returns the status of a bulk payment

## Validates and process card/bank payments based on the registered payer's DRN
```shell
curl "/v2/payment/dda" -X POST -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentApi;

ApiClient apiClient = new ApiClient();

PaymentApi api = new PaymentApi(apiClient);
api.processDDAPayment(transactionRequestDto, rootBillerId);

```

> The above command returns JSON structured like this:

# Auth


null

## Returns the user details of the authenticated user
```shell
curl "/v2/auth" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.AuthApi;

ApiClient apiClient = new ApiClient();

AuthApi api = new AuthApi(apiClient);
api.getUserDetails();

```

> The above command returns JSON structured like this:

```json
{
  "userName" : "str",
  "firstName" : "str",
  "lastName" : "str",
  "emailAddress" : "str",
  "mobileNumber" : "str",
  "id" : 1,
  "lastLogin" : "2016-03-03T10:15:30.00Z",
  "status" : "str",
  "showSplash" : true,
  "userType" : "MGL",
  "permissions" : [ {
    "id" : 1,
    "name" : "str",
    "description" : "str",
    "type" : "MGL"
  } ],
  "landLine" : "str"
}
```

### HTTP Request
`GET /v2/auth`
### Responses for status codes
|200|
|----|
|[UserDetailsResponse](#userdetailsresponse)|


## Authenticates payers drn and ivr code
```shell
curl "/v2/auth/ivr" -X POST -d @- << EOF 
{
  "drn" : "str",
  "ivrCode" : "str"
}
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.AuthApi;

ApiClient apiClient = new ApiClient();

AuthApi api = new AuthApi(apiClient);
api.ivrAuthValidation(body);

```

> The above command returns JSON structured like this:

## A wrapped JWT value
```shell
curl "/v2/auth/token" -X POST -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.AuthApi;

ApiClient apiClient = new ApiClient();

AuthApi api = new AuthApi(apiClient);
api.generateJwt(subject, ttl, login, body);

```

> The above command returns JSON structured like this:

```json
{
  "token" : "str",
  "expiry" : "2016-03-03T10:15:30.00Z"
}
```

### HTTP Request
`POST /v2/auth/token`
# Payment schedule


null

## Get Payer's Scheduled Payments
```shell
curl "/v2/payment-schedule" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentscheduleApi;

ApiClient apiClient = new ApiClient();

PaymentscheduleApi api = new PaymentscheduleApi(apiClient);
api.getPayerPaymentSchedules(limit, offset, order, orderBy, payerId, rootBillerId, status, id, drn, minAmount, maxAMount, frequency, interval, channel, cardBin, cardLast4, cardHolder, bankBsb, bankAccountNumber, bankAccountName, minNextPaymentDate, maxNextPaymentDate, billerId);

```

> The above command returns JSON structured like this:

## Create schedule transaction
```shell
curl "/v2/payment-schedule" -X POST -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentscheduleApi;

ApiClient apiClient = new ApiClient();

PaymentscheduleApi api = new PaymentscheduleApi(apiClient);
api.createPaymentSchedule(body, rootBillerId);

```

> The above command returns JSON structured like this:

## Executes a scheduled payment identified by the parameter id
```shell
curl "/v2/payment-schedule/execute/{id}" -X POST
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentscheduleApi;

ApiClient apiClient = new ApiClient();

PaymentscheduleApi api = new PaymentscheduleApi(apiClient);
api.executePayment(id, date);

```

> The above command returns JSON structured like this:

```json
{
  "result" : "str"
}
```

### HTTP Request
`POST /v2/payment-schedule/execute/{id}`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|date|true|string||


### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)||


### Responses for status codes
|200|400|
|----|----|
|[PaymentExecutionResponse](#paymentexecutionresponse)|[ErrorValue](#errorvalue) array|


## Get schedule transaction
```shell
curl "/v2/payment-schedule/{id}" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentscheduleApi;

ApiClient apiClient = new ApiClient();

PaymentscheduleApi api = new PaymentscheduleApi(apiClient);
api.getPaymentSchedule(id, rootBillerId);

```

> The above command returns JSON structured like this:

## Update schedule transaction
```shell
curl "/v2/payment-schedule/{id}" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentscheduleApi;

ApiClient apiClient = new ApiClient();

PaymentscheduleApi api = new PaymentscheduleApi(apiClient);
api.updatePaymentSchedule(id, body, rootBillerId);

```

> The above command returns JSON structured like this:

## Delete a payment schedule
```shell
curl "/v2/payment-schedule/{id}" -X DELETE
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.PaymentscheduleApi;

ApiClient apiClient = new ApiClient();

PaymentscheduleApi api = new PaymentscheduleApi(apiClient);
api.deletePaymentSchedule(id, rootBillerId);

```

> The above command returns JSON structured like this:

```json
{
  "id" : 1,
  "createdTimestamp" : "2016-03-03T10:15:30.00Z",
  "nextPaymentDate" : "2016-03-03T10:15:30.00Z",
  "drn" : "str",
  "crn" : "str",
  "status" : "ACTIVE",
  "updatedDate" : "2016-03-03T10:15:30.00Z",
  "endPaymentCount" : 1
}
```

### HTTP Request
`DELETE /v2/payment-schedule/{id}`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|rootBillerId|false|integer (int64)||


### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int64)||


### Responses for status codes
|200|400|
|----|----|
|[PaymentScheduleResponse](#paymentscheduleresponse)|[ErrorValue](#errorvalue) array|


# Card token


null

## Retrieves a list of Card Tokens
```shell
curl "/v2/card-token" -X GET
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.CardtokenApi;

ApiClient apiClient = new ApiClient();

CardtokenApi api = new CardtokenApi(apiClient);
api.getCardTokens(payerId, rootBillerId, dbc);

```

> The above command returns JSON structured like this:

```json
[ {
  "cardExpiryDate" : "str",
  "token" : "str",
  "cardBin" : "str",
  "lastFourDigits" : "str",
  "cardHolderName" : "str",
  "tokenRefNumber" : "str",
  "rootBillerId" : 1,
  "dbc" : 1,
  "payerId" : 1,
  "id" : 1,
  "cardScheme" : "str",
  "issuingOrganization" : "str",
  "created" : "2016-03-03T10:15:30.00Z",
  "updated" : "2016-03-03T10:15:30.00Z",
  "expired" : true,
  "default" : true
} ]
```

### HTTP Request
`GET /v2/card-token`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|payerId|false|integer (int64)||
|rootBillerId|false|integer (int64)||
|dbc|false|integer (int64)||


### Responses for status codes
|200|
|----|
|[WalletPaymentCardResponseDto](#walletpaymentcardresponsedto) array|


## Updates a card token
```shell
curl "/v2/card-token" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.CardtokenApi;

ApiClient apiClient = new ApiClient();

CardtokenApi api = new CardtokenApi(apiClient);
api.updateCardTokenCompatible(updateCardToken, rootBillerId);

```

> The above command returns JSON structured like this:

```json
{
  "cardExpiryDate" : "str",
  "token" : "str",
  "cardBin" : "str",
  "lastFourDigits" : "str",
  "cardHolderName" : "str",
  "tokenRefNumber" : "str",
  "rootBillerId" : 1,
  "dbc" : 1,
  "payerId" : 1,
  "id" : 1,
  "cardScheme" : "str",
  "issuingOrganization" : "str",
  "created" : "2016-03-03T10:15:30.00Z",
  "updated" : "2016-03-03T10:15:30.00Z",
  "expired" : true,
  "default" : true
}
```

### HTTP Request
`PUT /v2/card-token`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|rootBillerId|false|integer (int64)||


### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|false|integer (int64)||
|payerId|false|integer (int64)||
|token|false|string||
|rootBillerId|false|integer (int64)||
|dbc|false|integer (int64)||
|default|false|boolean||
|cardDetails|false|[WalletPaymentCardExpiryDateDto](#walletpaymentcardexpirydatedto)||


### Responses for status codes
|200|400|
|----|----|
|[WalletPaymentCardResponseDto](#walletpaymentcardresponsedto)|[ErrorValue](#errorvalue) array|



Error Codes:<ul><li>403001: Card token doesn't belong to the payer or biller </li><li>400002: Missing mandatory field</li><li>404000: Card token not found by ID</li><li>404001: Card token not found for payer or biller</li></ul>

## Create a card token
```shell
curl "/v2/card-token" -X POST -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.CardtokenApi;

ApiClient apiClient = new ApiClient();

CardtokenApi api = new CardtokenApi(apiClient);
api.createCardToken(cardToken, rootBillerId);

```

> The above command returns JSON structured like this:

```json
{
  "cardExpiryDate" : "str",
  "token" : "str",
  "cardBin" : "str",
  "lastFourDigits" : "str",
  "cardHolderName" : "str",
  "tokenRefNumber" : "str",
  "rootBillerId" : 1,
  "dbc" : 1,
  "payerId" : 1,
  "id" : 1,
  "cardScheme" : "str",
  "issuingOrganization" : "str",
  "created" : "2016-03-03T10:15:30.00Z",
  "updated" : "2016-03-03T10:15:30.00Z",
  "expired" : true,
  "default" : true
}
```

### HTTP Request
`POST /v2/card-token`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|rootBillerId|false|integer (int64)||


### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|cardExpiryDate|true|string||
|token|true|string||
|cardBin|true|string||
|lastFourDigits|true|string||
|cardHolderName|true|string||
|tokenRefNumber|true|string||
|rootBillerId|false|integer (int64)||
|dbc|false|integer (int64)||
|payerId|false|integer (int64)||
|default|false|boolean||


### Responses for status codes
|200|400|
|----|----|
|[WalletPaymentCardResponseDto](#walletpaymentcardresponsedto)|[ErrorValue](#errorvalue) array|



Error Codes:<ul><li>400922: Invalid rootBillerId, billerId combination</li><li>400002: Missing mandatory field</li><li>400023: Invalid field format or length</li></ul>

## Updates a card token
```shell
curl "/v2/card-token/{token}" -X PUT -d @- << EOF 
{ }
EOF
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.CardtokenApi;

ApiClient apiClient = new ApiClient();

CardtokenApi api = new CardtokenApi(apiClient);
api.cardTokenUpdate(token, updateCardToken, rootBillerId);

```

> The above command returns JSON structured like this:

```json
{
  "cardExpiryDate" : "str",
  "token" : "str",
  "cardBin" : "str",
  "lastFourDigits" : "str",
  "cardHolderName" : "str",
  "tokenRefNumber" : "str",
  "rootBillerId" : 1,
  "dbc" : 1,
  "payerId" : 1,
  "id" : 1,
  "cardScheme" : "str",
  "issuingOrganization" : "str",
  "created" : "2016-03-03T10:15:30.00Z",
  "updated" : "2016-03-03T10:15:30.00Z",
  "expired" : true,
  "default" : true
}
```

### HTTP Request
`PUT /v2/card-token/{token}`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|rootBillerId|false|integer (int64)||


### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|token|true|string||


### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|false|integer (int64)||
|payerId|false|integer (int64)||
|token|false|string||
|rootBillerId|false|integer (int64)||
|dbc|false|integer (int64)||
|default|false|boolean||
|cardDetails|false|[WalletPaymentCardExpiryDateDto](#walletpaymentcardexpirydatedto)||


### Responses for status codes
|200|400|
|----|----|
|[WalletPaymentCardResponseDto](#walletpaymentcardresponsedto)|[ErrorValue](#errorvalue) array|



Error Codes:<ul><li>403001: Card token doesn't belong to the payer or biller </li><li>400002: Missing mandatory field</li><li>404000: Card token not found by ID</li><li>404001: Card token not found for payer or biller</li></ul>

## Deletes a card token
```shell
curl "/v2/card-token/{token}" -X DELETE
```

```java
import io.swagger.client.api.ApiClient;
import io.swagger.client.api.CardtokenApi;

ApiClient apiClient = new ApiClient();

CardtokenApi api = new CardtokenApi(apiClient);
api.deleteToken(token, rootBillerId);

```

### HTTP Request
`DELETE /v2/card-token/{token}`
### Query Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|rootBillerId|false|integer (int64)||


### Path Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|token|true|string||


### Responses for status codes
|400|
|----|
|[ErrorValue](#errorvalue) array|



Error Codes:<ul><li>403001: Card token doesn't belong to the payer or biller </li><li>400002: Missing mandatory field</li><li>404001: Card token not found for payer or biller</li></ul>


## Definitions
### PayerSearchResult
|name|description|required|schema|default|
|----|----|----|----|----|
|summary||false|[PageSummary](#pagesummary)||
|results||false|[PayerResponseDto](#payerresponsedto) array||


### SuccessResponse
|name|description|required|schema|default|
|----|----|----|----|----|
|transactionStatus||false|enum (APPROVED, ERROR, DECLINED, DISHONOURED, PROCESSED, SUBMITTED, PENDING, INITIAL, INPROGRESS, REFUNDED, PARTIALLY_REFUNDED, CLEARED, CANCELLED)||
|transactionId||false|integer (int64)||
|responseCode||false|string||
|dtrn||false|integer (int64)||
|success||false|boolean|false|


### BankAccountResponseDto
|name|description|required|schema|default|
|----|----|----|----|----|
|bsb||true|string||
|accountNumber||true|string||
|accountName||true|string||
|defaultFlag||false|boolean|false|
|token||false|string||
|id||false|integer (int64)||
|payerId||false|integer (int64)||
|warningMessageCode||false|integer (int32)||
|warningMessage||false|string||
|bankBranch||false|[BankBranchDto](#bankbranchdto)||
|created||false|string (date-time)||
|updated||false|string (date-time)||


### Paging
|name|description|required|schema|default|
|----|----|----|----|----|
|limit||false|integer (int32)||
|offset||false|integer (int32)||
|order||false|enum (ASC, DESC)||
|orderBy||false|string||


### BulkDDAPaymentResponse
|name|description|required|schema|default|
|----|----|----|----|----|
|id||false|integer (int64)||
|customerBulkTransactionId||false|string||
|responseTimestamp||false|string (date-time)||
|total||false|integer (int64)||
|status||false|string||
|totalErrors||false|integer (int64)||
|errors||false|[FailedDDAPaymentDto](#failedddapaymentdto) array||


### FailureResponse
|name|description|required|schema|default|
|----|----|----|----|----|
|status||false|enum (APPROVED, ERROR, DECLINED, DISHONOURED, PROCESSED, SUBMITTED, PENDING, INITIAL, INPROGRESS, REFUNDED, PARTIALLY_REFUNDED, CLEARED, CANCELLED)||
|responseCode||false|string||
|switchResponseCode||false|string||
|responseTimestamp||false|string (date-time)||
|receiptNumber||false|string||
|dtrn||false|integer (int64)||
|success||false|boolean|false|


### AddressDto
|name|description|required|schema|default|
|----|----|----|----|----|
|country|Country|false|string||
|state|State; mandatory for an Australian address|true|enum (NSW, VIC, QLD, SA, NT, ACT, WA, TAS)||
|suburb|Suburb; mandatory for an Australian address|true|string||
|postCode|Post code; mandatory for an Australian address|true|string||
|streetLine1|First street line; mandatory for an Australian address|true|string||
|streetLine2|Second street line|false|string||
|australian|Is this an Australian address?|true|boolean|false|


### PayerResponseDto
|name|description|required|schema|default|
|----|----|----|----|----|
|userName|Email address|true|string||
|firstName|First name|true|string||
|lastName|Last name|true|string||
|emailAddress||false|string||
|mobileNumber||false|string||
|id||false|integer (int64)||
|lastLogin||false|string (date-time)||
|intlPhoneNumber||false|string||
|status||false|enum (MIGRATION_READY, SELF_REGISTRATION_STARTED, BILLER_REGISTRATION_STARTED, MIGRATION_STARTED, SELF_REGISTRATION_COMPLETE_DETAILS, BILLER_REGISTRATION_CONFIRM_DETAILS, MIGRATION_CONFIRM_DETAILS, ACTIVE, INACTIVE)||
|address||false|[AddressDto](#addressdto)||
|subscriptions||false|[UserSubscriptionsDto](#usersubscriptionsdto) array||
|dob||false|string (date-time)||
|displayName||false|string||
|landLine|Contact phone number|false|string||


### ErrorContainerDto
|name|description|required|schema|default|
|----|----|----|----|----|
|errors||false|[ErrorDto](#errordto) array||


### WalletPaymentCardResponseDto
|name|description|required|schema|default|
|----|----|----|----|----|
|cardExpiryDate||true|string||
|token||true|string||
|cardBin||true|string||
|lastFourDigits||true|string||
|cardHolderName||true|string||
|tokenRefNumber||true|string||
|rootBillerId||false|integer (int64)||
|dbc||false|integer (int64)||
|payerId||false|integer (int64)||
|id||false|integer (int64)||
|cardScheme||false|string||
|issuingOrganization||false|string||
|created||false|string (date-time)||
|updated||false|string (date-time)||
|expired||false|boolean|false|
|default||false|boolean|false|


### PayerDrnDto
|name|description|required|schema|default|
|----|----|----|----|----|
|payerId||false|integer (int64)||
|drnId||false|integer (int64)||
|drn||false|string||
|startDate||false|string (date-time)||
|endDate||false|string (date-time)||
|nickName||false|string||
|status||false|enum (ACTIVE, INACTIVE, SUSPENDED)||
|ivrCode||false|string||


### BillerHierarchyDto
|name|description|required|schema|default|
|----|----|----|----|----|
|biller||false|[BillerDto](#billerdto)||
|children||false|[BillerDto](#billerdto) array||


### MigrationReadyResponse
|name|description|required|schema|default|
|----|----|----|----|----|
|migrationReady||false|boolean|false|


### PaymentExecutionResponse
|name|description|required|schema|default|
|----|----|----|----|----|
|result||false|string||


### PaymentScheduleResponse
|name|description|required|schema|default|
|----|----|----|----|----|
|id||false|integer (int64)||
|createdTimestamp||false|string (date-time)||
|nextPaymentDate||false|string (date-time)||
|drn||false|string||
|crn||false|string||
|status||false|enum (ACTIVE, CANCELLED, COMPLETE, EXECUTING)||
|updatedDate||false|string (date-time)||
|endPaymentCount||false|integer (int32)||


### TransactionDateTimeDto
|name|description|required|schema|default|
|----|----|----|----|----|
|transactionDateTime||false|string (date-time)||


### ErrorValue
|name|description|required|schema|default|
|----|----|----|----|----|
|errorCode||false|integer (int32)||
|message||false|string||
|details||false|string||
|type||false|enum (ACCESS_ERROR, REQUEST_ERROR, LOGIC_ERROR, SYSTEM_ERROR, USER_MESSAGE, REFUND_ERROR, PAYMENT_METHOD_ERROR)||
|field||false|string||


### WalletPaymentCardExpiryDateDto
|name|description|required|schema|default|
|----|----|----|----|----|
|cardExpiryDate||true|string||


### DDAPaymentRequest
|name|description|required|schema|default|
|----|----|----|----|----|
|drn|Deft Reference Number (DRN)|true|string||
|currencyCode|Currency code in ISO 4217 Alphabetic code (e.g. AUD)|true|string||
|amount|Amount of the main payment|true|number||
|paymentFrequency|Payment frequency for this payment (e.g. RECURRING or ONE_OFF)|true|enum (ONE_OFF, RECURRING)||
|customerReference||false|string||
|dbc||false|integer (int64)||
|crn||false|integer (int64)||
|customerTransactionId||false|string||


### BillerDto
|name|description|required|schema|default|
|----|----|----|----|----|
|id||false|integer (int64)||
|type||false|enum (GROUP_CUSTOMER, BUSINESS_CUSTOMER, FACILITY, ACCOUNT)||
|name||false|string||
|status||false|string||
|accessible||false|boolean|false|
|drn||false|string||


### UserDetailsResponse
|name|description|required|schema|default|
|----|----|----|----|----|
|userName|Email address|true|string||
|firstName|First name|true|string||
|lastName|Last name|true|string||
|emailAddress||false|string||
|mobileNumber||false|string||
|id||false|integer (int64)||
|lastLogin||false|string (date-time)||
|status||false|string||
|showSplash||false|boolean|false|
|userType||false|enum (MGL, PAYER, BILLER, API, BATCH)||
|permissions||false|[PermissionDetailedDto](#permissiondetaileddto) array||
|landLine|Contact phone number|false|string||


### BillerSearchDto
|name|description|required|schema|default|
|----|----|----|----|----|
|id||false|integer (int64)||
|type||false|enum (GROUP_CUSTOMER, BUSINESS_CUSTOMER, FACILITY, ACCOUNT)||
|name||false|string||
|status||false|enum (INACTIVE, ACTIVE)||
|accessible||false|boolean|false|
|ddaEnabled||false|boolean|false|


