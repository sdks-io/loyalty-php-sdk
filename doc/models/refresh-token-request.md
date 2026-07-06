
# Refresh Token Request

*This model accepts additional fields of type array.*

## Structure

`RefreshTokenRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `refreshToken` | `string` | Required | The refresh token which was provided from the exchangeAccessCode end point. | getRefreshToken(): string | setRefreshToken(string refreshToken): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\RefreshTokenRequestBuilder;
use LoyaltyApIsLib\ApiHelper;

$refreshTokenRequest = RefreshTokenRequestBuilder::init(
    'refreshToken4'
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

