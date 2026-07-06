# Redemption

API for customer to redeem loyalty points

```php
$redemptionApi = $client->getRedemptionApi();
```

## Class Name

`RedemptionApi`


# Point Redemption

Point redemption API for customers to redeem loyalty points via the partner channel

```php
function pointRedemption(
    string $languageCode,
    string $userAuthorizationToken,
    string $consumerUuid,
    string $countryCode,
    ?string $xCorrelationId = null,
    ?string $channel = null,
    ?string $application = null,
    ?int $retryAfter = null,
    ?RedemptionRequest $body = null
): ApiResponse
```

## Authentication

This endpoint requires [client-authorization-token](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `languageCode` | `string` | Query, Required | A combination of [language code](https://www.iso.org/standard/22109.html) (lower case) and [country code](https://www.iso.org/iso-3166-country-codes.html) (upper case), separated by a hyphen. |
| `userAuthorizationToken` | `string` | Header, Required | The value of the accessToken retrieved from the /auth/exchangeAccessCode endpoint. This is referred to as user-authorization-token where the access is provided by the end user. |
| `consumerUuid` | `string` | Header, Required | SSO uuid of the user signed in with Shell credentials Format: 32 hexadecimal digits grouped the following way: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx |
| `countryCode` | `string` | Header, Required | The two character ISO 3166-1 alpha-2 [country code](https://www.iso.org/iso-3166-country-codes.html). |
| `xCorrelationId` | `?string` | Header, Optional | An unique ID in GUID format in order to track the request. |
| `channel` | [`?string(AssignOfferChannel)`](../../doc/models/assign-offer-channel.md) | Header, Optional | Channel. |
| `application` | `?string` | Header, Optional | String |
| `retryAfter` | `?int` | Header, Optional | Retry the operation after a specified number of seconds have elapsed. |
| `body` | [`?RedemptionRequest`](../../doc/models/redemption-request.md) | Body, Optional | Redeem a customer's loyalty points |

## Response Type

**200**: This API is used for Point Redemption by Customer and Partner

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`RedemptionResponse`](../../doc/models/redemption-response.md).

## Example Usage

```php
$languageCode = 'en-GB';

$userAuthorizationToken = 'Bearer asdfhalsdfheywuiryafhk';

$consumerUuid = 'cee1157e-cac0-4fc6-b92b-68a13b456b43';

$countryCode = 'GB';

$xCorrelationId = '8483a8c3-e2c7-4849-835f-8ed27e5be276';

$channel = AssignOfferChannel::PARTNER;

$application = 'PARTNER';

$retryAfter = 5;

$body = RedemptionRequestBuilder::init(
    'cee1157e-cac0-4fc6-b92b-68a13b456b43',
    'as3df5131fas3f54f92h5df',
    [
        RedemptionItemBuilder::init(
            '1005',
            50,
            'Cheeseburger'
        )
            ->quantity(2)
            ->build(),
        RedemptionItemBuilder::init(
            '1006',
            20,
            'Chips'
        )
            ->quantity(1)
            ->build(),
        RedemptionItemBuilder::init(
            '1007',
            10,
            'Ice Cream'
        )->build()
    ]
)->build();

$redemptionApi = $client->getRedemptionApi();
$apiResponse = $redemptionApi->pointRedemption(
    $languageCode,
    $userAuthorizationToken,
    $consumerUuid,
    $countryCode,
    $xCorrelationId,
    $channel,
    $application,
    $retryAfter,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'RedemptionResponse:';
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
| 401 | Unauthorized request, Missing Authorization header, or expired authorization token etc. It is returned from the application server<br>when application security is enabled, and authorization information was missing from the request. | [`ConsumersBalances400ErrorException`](../../doc/models/consumers-balances-400-error-exception.md) |
| 404 | Not found - the server can not find the requested resource. | [`ConsumersBalances400ErrorException`](../../doc/models/consumers-balances-400-error-exception.md) |
| 422 | Unprocessable Entity (WebDAV). If you are receiving an HTTP 422 - Unprocessable Entity error,<br>there are several possibilities for why it might be occurring-<br><br><br>- You are sending in a payload that is not valid JSON. <br><br>- You are sending HTTP headers, such as Content-Type or Accept, which specify a value other than application/json. <br><br>- The request may be valid JSON, but there is something wrong with the content. | [`ConsumersBalances400ErrorException`](../../doc/models/consumers-balances-400-error-exception.md) |
| 429 | Rate limit hit. See the Retry-After header to specify a delay, but note that there is no guarantee that subsequent requests won't be limited. | `ApiException` |
| 500 | Internal server error | `ApiException` |

