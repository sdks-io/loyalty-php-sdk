# Authorization

Token and access code management

```php
$authorizationApi = $client->getAuthorizationApi();
```

## Class Name

`AuthorizationApi`

## Methods

* [Get Authorization Token](../../doc/controllers/authorization.md#get-authorization-token)
* [Exchange Access Code](../../doc/controllers/authorization.md#exchange-access-code)
* [Refresh](../../doc/controllers/authorization.md#refresh)


# Get Authorization Token

When partner wants to get the basic public token, to be authorized to perform any other call inside SSO, needs to call this endpoint

:information_source: **Note** This endpoint does not require authentication.

```php
function getAuthorizationToken(AuthTokenRequest $body): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`AuthTokenRequest`](../../doc/models/auth-token-request.md) | Body, Required | Digest data generated using sha256(client_id) |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AuthTokenResponse`](../../doc/models/auth-token-response.md).

## Example Usage

```php
$body = AuthTokenRequestBuilder::init()
    ->digest('Aaaaaaaaaaaaaa')
    ->build();

$authorizationApi = $client->getAuthorizationApi();
$apiResponse = $authorizationApi->getAuthorizationToken($body);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AuthTokenResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request. If the request is missing the digest field | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |
| 401 | Unauthorized. If the digest provided is not valid | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |
| 500 | Any unexpected error | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |


# Exchange Access Code

This endpoint allows to given an access code to retrieve an user profile with a pair of valid tokens. In this end point, accessCode can be exchanged for an accessToken which is user-authorization-token.

```php
function exchangeAccessCode(string $authorization, ExchangeAccessCodeRequest $body): ApiResponse
```

## Authentication

This endpoint requires [PublicBasicToken](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `authorization` | `string` | Header, Required | Basic Public token which was generated with auth/token end point. |
| `body` | [`ExchangeAccessCodeRequest`](../../doc/models/exchange-access-code-request.md) | Body, Required | Exchange access code data |

## Response Type

**200**: The response include the SSO user profile and a pair of access token and refresh token

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`M200UserPartners`](../../doc/models/m200-user-partners.md).

## Example Usage

```php
$authorization = 'Basic 31d9027a8...42146af077';

$body = ExchangeAccessCodeRequestBuilder::init()
    ->accessCode('AAAAAAAAAAAAA')
    ->build();

$authorizationApi = $client->getAuthorizationApi();
$apiResponse = $authorizationApi->exchangeAccessCode(
    $authorization,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'M200UserPartners:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "uuid": "bb0dffbe‑95c8‑442f‑b15e‑53b8cf0a3d99",
  "userStatus": "UNVERIFIED",
  "market": {
    "code": "en‑GB",
    "country": "GB"
  },
  "accessToken": "ACCESS_TOKEN",
  "refreshToken": "REFRESH_TOKEN"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 401 | Unauthorized. If making the call with an invalid token | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |
| 404 | Not found. If the access code is not in the database | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |
| 500 | Any unexpected error | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |


# Refresh

When an access token has expired, a partner that wants to get a new pair of valid tokens to go on performing operations against SSO needs to call this endpoint.

:information_source: **Note** This endpoint does not require authentication.

```php
function refresh(string $authorization, ?RefreshTokenRequest $body = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `authorization` | `string` | Header, Required | Basic Public token which was generated with auth/token end point. |
| `body` | [`?RefreshTokenRequest`](../../doc/models/refresh-token-request.md) | Body, Optional | - |

## Response Type

**200**: OK. Access token and refresh token are returned.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`RefreshTokenResponse`](../../doc/models/refresh-token-response.md).

## Example Usage

```php
$authorization = 'Basic 31d9027a8...42146af077';

$body = RefreshTokenRequestBuilder::init(
    'x5as2qv8hpercvq867gu'
)->build();

$authorizationApi = $client->getAuthorizationApi();
$apiResponse = $authorizationApi->refresh(
    $authorization,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'RefreshTokenResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "accessToken": "bzrz5f3qegav7xqv",
  "refreshToken": "u6junnmqqmsxx27ynsba",
  "expiresIn": 3600
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request. The request is missing the Refresh Token field. | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |
| 401 | Unauthorized. This response is generated when either the Basic Token is invalid or the Refresh Token is invalid (see examples) | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |
| 500 | Any unexpected error | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |

