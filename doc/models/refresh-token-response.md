
# Refresh Token Response

*This model accepts additional fields of type array.*

## Structure

`RefreshTokenResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accessToken` | `string` | Required | - | getAccessToken(): string | setAccessToken(string accessToken): void |
| `refreshToken` | `string` | Required | - | getRefreshToken(): string | setRefreshToken(string refreshToken): void |
| `expiresIn` | `int` | Required | Indicates the number of seconds until the new access token provided in the pair expires | getExpiresIn(): int | setExpiresIn(int expiresIn): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\RefreshTokenResponseBuilder;
use LoyaltyApIsLib\ApiHelper;

$refreshTokenResponse = RefreshTokenResponseBuilder::init(
    'accessToken2',
    'refreshToken2',
    84
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

