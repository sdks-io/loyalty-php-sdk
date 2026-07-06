# Offer

APIs to assign and revoke an offer for the customer

```php
$offerApi = $client->getOfferApi();
```

## Class Name

`OfferApi`

## Methods

* [Assign Partner Offer](../../doc/controllers/offer.md#assign-partner-offer)
* [Revoke Partner Offer](../../doc/controllers/offer.md#revoke-partner-offer)


# Assign Partner Offer

Assigning a partner based offer to a customer by the partner

```php
function assignPartnerOffer(
    string $languageCode,
    string $userAuthorizationToken,
    string $countryCode,
    ?string $xCorrelationId = null,
    ?string $channel = null,
    ?string $application = null,
    ?OfferAssignment $body = null
): ApiResponse
```

## Authentication

This endpoint requires [client-authorization-token](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `languageCode` | `string` | Query, Required | This is a concatenation of language in lower case as per ISO 639-1 , “-” and country code as per ISO 3166-1 alpha-2. |
| `userAuthorizationToken` | `string` | Header, Required | The value of the `accessToken` retrieved from the `/auth/exchangeAccessCode` endpoint. This is referred to as user-authorization-token where the access is provided by the end user. |
| `countryCode` | `string` | Header, Required | Two character ISO 3166-1 alpha-2 country code. |
| `xCorrelationId` | `?string` | Header, Optional | An unique ID in GUID format in order to track the request. |
| `channel` | [`?string(AssignOfferChannel)`](../../doc/models/assign-offer-channel.md) | Header, Optional | Channel. |
| `application` | `?string` | Header, Optional | String |
| `body` | [`?OfferAssignment`](../../doc/models/offer-assignment.md) | Body, Optional | assign offer to customer |

## Response Type

**200**: Successful partner offer assignment, response contains all relevant data of the Offer.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Offer`](../../doc/models/offer.md).

## Example Usage

```php
$languageCode = 'en-GB';

$userAuthorizationToken = 'ckr08brxj00zp0rqkrlq5526q';

$countryCode = 'GB';

$xCorrelationId = '7c9a45de-00f5-4b13-9a0b-50e16c462a4e';

$channel = AssignOfferChannel::PARTNER;

$application = 'PARTNER';

$body = OfferAssignmentBuilder::init(
    'as3df5131fas3f54f92h5df',
    'cee1157e-cac0-4fc6-b92b-68a13b456b43',
    'offerId1234'
)
    ->validFrom(DateTimeHelper::fromRfc3339DateTime('03/08/2021 17:12:55'))
    ->validityPeriod(31)
    ->validTo(DateTimeHelper::fromRfc3339DateTime('03/08/2021 17:12:55'))
    ->build();

$offerApi = $client->getOfferApi();
$apiResponse = $offerApi->assignPartnerOffer(
    $languageCode,
    $userAuthorizationToken,
    $countryCode,
    $xCorrelationId,
    $channel,
    $application,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Offer:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request as certain mandatory parameters were not provided by the client in the request. | [`CommonErrorException`](../../doc/models/common-error-exception.md) |
| 401 | Unauthorized request, Missing Authorization header, or expired authorization token. | [`CommonErrorException`](../../doc/models/common-error-exception.md) |
| 404 | Offer/Customer does not exist. | [`CommonErrorException`](../../doc/models/common-error-exception.md) |
| 422 | All offer assignment based error what it caused by the "Offer" | [`CommonErrorException`](../../doc/models/common-error-exception.md) |
| 429 | Rate limit hit. See Retry-After header for a minimum amount of delay, but note that there is no guarantee<br>that subsequent request won't be limited. | `ApiException` |
| 500 | Internal server error | `ApiException` |


# Revoke Partner Offer

Revoking a partner based offer from customer by Partner.

```php
function revokePartnerOffer(
    string $languageCode,
    string $userAuthorizationToken,
    string $clientAuthorizationToken,
    string $countryCode,
    string $consumerUuid,
    string $partnerReferenceId,
    ?string $xCorrelationId = null,
    ?string $channel = null,
    ?string $application = null
): ApiResponse
```

## Authentication

This endpoint requires [client-authorization-token](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `languageCode` | `string` | Query, Required | This is a concatenation of language in lower case as per ISO 639-1 , “-” and country code as per ISO 3166-1 alpha-2. |
| `userAuthorizationToken` | `string` | Header, Required | The value of the `accessToken` retrieved from the `/auth/exchangeAccessCode` endpoint. This is referred to as user-authorization-token where the access is provided by the end user. |
| `clientAuthorizationToken` | `string` | Header, Required | The value of the `accessToken` retrieved from the `/oauth/token` endpoint. This is client authorization between Shell and Partner system. |
| `countryCode` | `string` | Header, Required | Two character ISO 3166-1 alpha-2 country code. |
| `consumerUuid` | `string` | Header, Required | SSO uuid of the user signed in with Shell credentials. |
| `partnerReferenceId` | `string` | Header, Required | Unique Reference ID for the transaction which was used when assigning the offer from the partner in Assign Offer API |
| `xCorrelationId` | `?string` | Header, Optional | An unique ID in GUID format in order to track the request. |
| `channel` | [`?string(AssignOfferChannel)`](../../doc/models/assign-offer-channel.md) | Header, Optional | Channel. |
| `application` | `?string` | Header, Optional | String |

## Response Type

**200**: Successful partner offer assignment, response contains all relevant data of the Offer.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Offer`](../../doc/models/offer.md).

## Example Usage

```php
$languageCode = 'en-GB';

$userAuthorizationToken = 'ckr08brxj00zp0rqkrlq5526q';

$clientAuthorizationToken = 'dtcdhdhTGSAHSJS78HAJAN';

$countryCode = 'GB';

$consumerUuid = '7c9a45de-00f5-4b13-9a0b-50e16c462a4e';

$partnerReferenceId = '7c9a45de-00f5-4b13-9a0b-50e16c462a4e';

$xCorrelationId = '7c9a45de-00f5-4b13-9a0b-50e16c462a4e';

$channel = AssignOfferChannel::PARTNER;

$application = 'PARTNER';

$offerApi = $client->getOfferApi();
$apiResponse = $offerApi->revokePartnerOffer(
    $languageCode,
    $userAuthorizationToken,
    $clientAuthorizationToken,
    $countryCode,
    $consumerUuid,
    $partnerReferenceId,
    $xCorrelationId,
    $channel,
    $application
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Offer:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request as certain mandatory parameters were not provided by the client in the request. | [`CommonErrorException`](../../doc/models/common-error-exception.md) |
| 401 | Unauthorized request, Missing Authorization header, or expired authorization token. | [`CommonErrorException`](../../doc/models/common-error-exception.md) |
| 404 | Offer/Customer does not exist. | [`CommonErrorException`](../../doc/models/common-error-exception.md) |
| 422 | All offer assignment based error what it caused by the "Offer" | [`CommonErrorException`](../../doc/models/common-error-exception.md) |
| 429 | Rate limit hit. See Retry-After header for a minimum amount of delay, but note that there is no guarantee<br>that subsequent request won't be limited. | `ApiException` |
| 500 | Internal server error | `ApiException` |

