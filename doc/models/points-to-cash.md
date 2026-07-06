
# Points to Cash

*This model accepts additional fields of type array.*

## Structure

`PointsToCash`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `pointsRedeemed` | `?float` | Optional | The points used for converting it to cash | getPointsRedeemed(): ?float | setPointsRedeemed(?float pointsRedeemed): void |
| `totalAmount` | `?float` | Optional | Total amount in cash used | getTotalAmount(): ?float | setTotalAmount(?float totalAmount): void |
| `pointsToCashMop` | `?bool` | Optional | Indication if the p2c was used as a method of payment | getPointsToCashMop(): ?bool | setPointsToCashMop(?bool pointsToCashMop): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\PointsToCashBuilder;
use LoyaltyApIsLib\ApiHelper;

$pointsToCash = PointsToCashBuilder::init()
    ->pointsRedeemed(88.32)
    ->totalAmount(108.04)
    ->pointsToCashMop(true)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

