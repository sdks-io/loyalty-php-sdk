
# Redemption Item

*This model accepts additional fields of type array.*

## Structure

`RedemptionItem`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `itemId` | `string` | Required | The itemID identifies the catalogue item in the loyalty system. Shell will set these up and share the IDs with the partner. | getItemId(): string | setItemId(string itemId): void |
| `quantity` | `?int` | Optional | Number of items redeemed on the user's behalf. If the quantity is not specified, the system will assume a default quantity of 1. This is not used for the calculation of points, but only for displaying to the user.<br><br>**Default**: `1` | getQuantity(): ?int | setQuantity(?int quantity): void |
| `points` | `int` | Required | Total number of points to be redeemed from the Shell Loyalty Platform for this item. | getPoints(): int | setPoints(int points): void |
| `reasonForRedemption` | `string` | Required | Reason for the points redemption. This attribute will be shown to the customer via app/web channel under Transaction History.<br><br>**Constraints**: *Maximum Length*: `65` | getReasonForRedemption(): string | setReasonForRedemption(string reasonForRedemption): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\RedemptionItemBuilder;
use LoyaltyApIsLib\ApiHelper;

$redemptionItem = RedemptionItemBuilder::init(
    '1001',
    12,
    'burger'
)
    ->quantity(5)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

