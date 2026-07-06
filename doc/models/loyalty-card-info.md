
# Loyalty Card Info

*This model accepts additional fields of type array.*

## Structure

`LoyaltyCardInfo`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `loyaltyCard` | `?string` | Optional | Loyalty card of the transaction. | getLoyaltyCard(): ?string | setLoyaltyCard(?string loyaltyCard): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\LoyaltyCardInfoBuilder;
use LoyaltyApIsLib\ApiHelper;

$loyaltyCardInfo = LoyaltyCardInfoBuilder::init()
    ->loyaltyCard('1234567890123456789')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

