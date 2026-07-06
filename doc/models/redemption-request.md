
# Redemption Request

*This model accepts additional fields of type array.*

## Structure

`RedemptionRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `uuid` | `string` | Required | The SSO uuid of the user signed in with Shell credentials.<br>Format: 32 hexadecimal digits grouped the following way: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx<br>See: https://www.wikiwand.com/en/Universally_unique_identifier#/Format | getUuid(): string | setUuid(string uuid): void |
| `referenceId` | `string` | Required | A unique ID for the transaction from the partner. Used to identify duplicate requests.<br><br>**Constraints**: *Maximum Length*: `128` | getReferenceId(): string | setReferenceId(string referenceId): void |
| `redemptionReqArray` | [`RedemptionItem[]`](../../doc/models/redemption-item.md) | Required | Specifies the number of points to be redeemed from the user's point balance and the reason for redemption, which will also be shown to the user. Mutiple redemption items can be submitted in a single API request. | getRedemptionReqArray(): array | setRedemptionReqArray(array redemptionReqArray): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\RedemptionRequestBuilder;
use LoyaltyApIsLib\Models\Builders\RedemptionItemBuilder;
use LoyaltyApIsLib\ApiHelper;

$redemptionRequest = RedemptionRequestBuilder::init(
    'cee1157e-cac0-4fc6-b92b-68a13b456b43',
    'as3df5131fas3f54f92h5df',
    [
        RedemptionItemBuilder::init(
            '1005',
            50,
            'Cheeseburger'
        )
            ->quantity(2)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build(),
        RedemptionItemBuilder::init(
            '1006',
            20,
            'Chips'
        )
            ->quantity(1)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build(),
        RedemptionItemBuilder::init(
            '1007',
            10,
            'Ice Cream'
        )
            ->quantity(220)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

