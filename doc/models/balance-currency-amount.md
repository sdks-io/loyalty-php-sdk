
# Balance Currency Amount

*This model accepts additional fields of type array.*

## Structure

`BalanceCurrencyAmount`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `currencyType` | [`string(BalanceCurrencyType)`](../../doc/models/balance-currency-type.md) | Required | **Constraints**: *Minimum Length*: `1` | getCurrencyType(): string | setCurrencyType(string currencyType): void |
| `amounts` | [`?(BalanceAmountDetail[])`](../../doc/models/balance-amount-detail.md) | Optional | **Constraints**: *Minimum Items*: `1`, *Unique Items Required* | getAmounts(): ?array | setAmounts(?array amounts): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\BalanceCurrencyAmountBuilder;
use LoyaltyApIsLib\Models\BalanceCurrencyType;
use LoyaltyApIsLib\Models\Builders\BalanceAmountDetailBuilder;
use LoyaltyApIsLib\Models\BalanceState;
use LoyaltyApIsLib\Utils\DateTimeHelper;
use LoyaltyApIsLib\ApiHelper;

$balanceCurrencyAmount = BalanceCurrencyAmountBuilder::init(
    BalanceCurrencyType::POINT
)
    ->amounts(
        [
            BalanceAmountDetailBuilder::init(
                104.18,
                BalanceState::TOTAL_SPENT,
                DateTimeHelper::fromRfc3339DateTimeRequired('2016-03-13T12:52:32.123Z'),
                110
            )
                ->cashAmount(243.86)
                ->period(224)
                ->position(
                    [
                        181,
                        182,
                        183
                    ]
                )
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            BalanceAmountDetailBuilder::init(
                104.18,
                BalanceState::TOTAL_SPENT,
                DateTimeHelper::fromRfc3339DateTimeRequired('2016-03-13T12:52:32.123Z'),
                110
            )
                ->cashAmount(243.86)
                ->period(224)
                ->position(
                    [
                        181,
                        182,
                        183
                    ]
                )
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

