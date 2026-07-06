# Profile Management

```php
$profileManagementApi = $client->getProfileManagementApi();
```

## Class Name

`ProfileManagementApi`


# Access Code

This endpoint allows get the Access Code from /api/v2/auth/accessCode endpoint. Use the *accessToken* obtained using /api/v2/auth/exchangeAccessCode as Bearer in the Authorization header.

:information_source: **Note** This endpoint does not require authentication.

```php
function accessCode(string $xSsoMarket, array $authorization): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `xSsoMarket` | `string` | Header, Required | A combination of [language code](https://www.iso.org/standard/22109.html) (lower case) and [country code](https://www.iso.org/iso-3166-country-codes.html) (upper case), separated by a hyphen. For example: **en-TH**. |
| `authorization` | `array` | Header, Required | The input value is **Bearer {{accessToken}}**. The value of *accessToken* is retrieved from the /auth/exchangeAccessCode endpoint. |

## Response Type

**200**: **OK**. The response includes accessCode and its expiration time of 30 seconds.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AccessCodeResponse`](../../doc/models/access-code-response.md).

## Example Usage

```php
$xSsoMarket = 'en-TH';

$authorization = ApiHelper::deserialize('"Bearer clna3pz3600ih1vo6pus1w36b"');

$profileManagementApi = $client->getProfileManagementApi();
$apiResponse = $profileManagementApi->accessCode(
    $xSsoMarket,
    $authorization
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AccessCodeResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 401 | Unauthorized | `ApiException` |
| 500 | Any unexpected error | [`JsonApiErrorException`](../../doc/models/json-api-error-exception.md) |

