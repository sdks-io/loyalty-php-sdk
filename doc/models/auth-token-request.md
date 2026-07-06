
# Auth Token Request

*This model accepts additional fields of type array.*

## Structure

`AuthTokenRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `digest` | `?string` | Optional | - | getDigest(): ?string | setDigest(?string digest): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\AuthTokenRequestBuilder;
use LoyaltyApIsLib\ApiHelper;

$authTokenRequest = AuthTokenRequestBuilder::init()
    ->digest('Aaaaaaaaaaaaaa')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

