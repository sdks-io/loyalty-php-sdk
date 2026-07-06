
# Redemption Response Item

*This model accepts additional fields of type array.*

## Structure

`RedemptionResponseItem`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `itemId` | `?string` | Optional | Unique Item ID for the transaction from the partner. Used to identify the catalogue item in the Shell Loyalty Platform. Each Partner will have one or more items set up in the Shell Loyalty Platform. | getItemId(): ?string | setItemId(?string itemId): void |
| `quantity` | `?int` | Optional | The quantity of the items required. | getQuantity(): ?int | setQuantity(?int quantity): void |
| `points` | `?int` | Optional | The number of points that will be redemmed from the Shell Loyalty Platform. | getPoints(): ?int | setPoints(?int points): void |
| `reasonForRedemption` | `?string` | Optional | The reason for the points redemption. This attribute will be shown in the Transaction History feture. | getReasonForRedemption(): ?string | setReasonForRedemption(?string reasonForRedemption): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\RedemptionResponseItemBuilder;
use LoyaltyApIsLib\ApiHelper;

$redemptionResponseItem = RedemptionResponseItemBuilder::init()
    ->itemId('1005')
    ->quantity(2)
    ->points(50)
    ->reasonForRedemption('ChesseBurger')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

