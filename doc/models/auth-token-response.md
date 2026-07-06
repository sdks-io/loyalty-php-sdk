
# Auth Token Response

*This model accepts additional fields of type array.*

## Structure

`AuthTokenResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `token` | `?string` | Optional | Your Basic public token which needs to be used in the auth/ExchangeAccessCode. | getToken(): ?string | setToken(?string token): void |
| `tokenType` | `?string` | Optional | Type of the token. | getTokenType(): ?string | setTokenType(?string tokenType): void |
| `expiresIn` | `?string` | Optional | With value **unlimited** it means this token will never expire | getExpiresIn(): ?string | setExpiresIn(?string expiresIn): void |
| `owner` | `?string` | Optional | States the name of the partner to which the digest used belongs | getOwner(): ?string | setOwner(?string owner): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\AuthTokenResponseBuilder;
use LoyaltyApIsLib\ApiHelper;

$authTokenResponse = AuthTokenResponseBuilder::init()
    ->token('AhshsisaahshsuewenJJJJNFFTA')
    ->tokenType('Basic')
    ->expiresIn('unlimited')
    ->owner('partner_abc')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

