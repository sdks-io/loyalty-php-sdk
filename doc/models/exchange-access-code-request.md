
# Exchange Access Code Request

*This model accepts additional fields of type array.*

## Structure

`ExchangeAccessCodeRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accessCode` | `?string` | Optional | AccessCode provided by Shell after it redirects the user to the partner's URL. | getAccessCode(): ?string | setAccessCode(?string accessCode): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\ExchangeAccessCodeRequestBuilder;
use LoyaltyApIsLib\ApiHelper;

$exchangeAccessCodeRequest = ExchangeAccessCodeRequestBuilder::init()
    ->accessCode('AAAAAAAAAAAAA')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

