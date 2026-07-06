
# M200 User Partners

*This model accepts additional fields of type array.*

## Structure

`M200UserPartners`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `uuid` | `string` | Required | - | getUuid(): string | setUuid(string uuid): void |
| `userStatus` | `string` | Required | - | getUserStatus(): string | setUserStatus(string userStatus): void |
| `market` | `array` | Required | - | getMarket(): array | setMarket(array market): void |
| `accessToken` | `string` | Required | - | getAccessToken(): string | setAccessToken(string accessToken): void |
| `refreshToken` | `string` | Required | - | getRefreshToken(): string | setRefreshToken(string refreshToken): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\M200UserPartnersBuilder;
use LoyaltyApIsLib\ApiHelper;

$m200UserPartners = M200UserPartnersBuilder::init(
    'bb0dffbe‑95c8‑442f‑b15e‑53b8cf0a3d99',
    'UNVERIFIED',
    ApiHelper::deserialize('{"code":"en‑GB","country":"GB"}'),
    'ACCESS_TOKEN',
    'REFRESH_TOKEN'
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

