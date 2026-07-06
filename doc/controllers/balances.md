# Balances

API for retrieving a customer's loyalty point balance

```php
$balancesApi = $client->getBalancesApi();
```

## Class Name

`BalancesApi`


# Get Balance by Uuid

Retrieve the customer's loyalty point balance

```php
function getBalanceByUuid(
    string $languageCode,
    string $userAuthorizationToken,
    string $consumerUuid,
    string $countryCode,
    ?string $xCorrelationId = null,
    ?string $channel = null,
    ?string $application = null
): ApiResponse
```

## Authentication

This endpoint requires [customerHeader](../../doc/auth/custom-header-signature-2.md) **AND** [client-authorization-token](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `languageCode` | `string` | Query, Required | This is a concatenation of language in lower case as per ISO 639-1 , “-” and country code as per ISO 3166-1 alpha-2. |
| `userAuthorizationToken` | `string` | Header, Required | The value of the accessToken retrieved from the /auth/exchangeAccessCode endpoint. This is referred to as user-authorization-token where the access is provided by the end user. |
| `consumerUuid` | `string` | Header, Required | SSO uuid of the user signed in with Shell credentials Format: 32 hexadecimal digits grouped the following way: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx |
| `countryCode` | `string` | Header, Required | The two character ISO 3166-1 alpha-2 [country code](https://www.iso.org/iso-3166-country-codes.html). |
| `xCorrelationId` | `?string` | Header, Optional | An unique ID in GUID format in order to track the request. |
| `channel` | [`?string(AssignOfferChannel)`](../../doc/models/assign-offer-channel.md) | Header, Optional | Channel. |
| `application` | `?string` | Header, Optional | String |

## Response Type

**200**: success

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CustomerBalances`](../../doc/models/customer-balances.md).

## Example Usage

```php
$languageCode = 'en-GB';

$userAuthorizationToken = 'Bearer asdfhalsdfheywuiryafhk';

$consumerUuid = 'cee1157e-cac0-4fc6-b92b-68a13b456b43';

$countryCode = 'GB';

$xCorrelationId = '8483a8c3-e2c7-4849-835f-8ed27e5be276';

$channel = AssignOfferChannel::PARTNER;

$application = 'PARTNER';

$balancesApi = $client->getBalancesApi();
$apiResponse = $balancesApi->getBalanceByUuid(
    $languageCode,
    $userAuthorizationToken,
    $consumerUuid,
    $countryCode,
    $xCorrelationId,
    $channel,
    $application
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CustomerBalances:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request - The request was not valid. This code is returned when the server has attempted to process the request, but some aspect of the request is not valid, for example an incorrectly formatted resource or an attempt to deploy an invalid event project to the event runtime. Information about the request is provided in the response body, and includes an error code and error message. | [`ConsumersBalances400ErrorException`](../../doc/models/consumers-balances-400-error-exception.md) |
| 401 | Unauthorized request, Missing Authorization header, or expired authorization token etc. It is returned from the application server<br>when application security is enabled, and authorization information was missing from the request. | [`ConsumersBalances401ErrorException`](../../doc/models/consumers-balances-401-error-exception.md) |
| 404 | Not found - the server can not find the requested resource. | [`ConsumersBalances404ErrorException`](../../doc/models/consumers-balances-404-error-exception.md) |
| 422 | Unprocessable Entity (WebDAV). If you are receiving an HTTP 422 - Unprocessable Entity error,<br>there are several possibilities for why it might be occurring-<br><br><br>- You are sending in a payload that is not valid JSON. <br><br>- You are sending HTTP headers, such as Content-Type or Accept, which specify a value other than application/json. <br><br>- The request may be valid JSON, but there is something wrong with the content. | [`ConsumersBalances422ErrorException`](../../doc/models/consumers-balances-422-error-exception.md) |
| 429 | Rate limit hit. See the Retry-After header to specify a delay, but note that there is no guarantee that subsequent requests won't be limited. | `ApiException` |
| 500 | Internal error - the server encountered an unexpected condition that prevented it from fulfilling the request. | `ApiException` |

