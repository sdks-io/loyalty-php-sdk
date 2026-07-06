
# Customer Balances

*This model accepts additional fields of type array.*

## Structure

`CustomerBalances`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `balances` | [`?(BalanceAmount[])`](../../doc/models/balance-amount.md) | Optional | A list of points balances. Not nullable, an empty array is used instead.<br><br>**Constraints**: *Minimum Items*: `0` | getBalances(): ?array | setBalances(?array balances): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\CustomerBalancesBuilder;
use LoyaltyApIsLib\Models\Builders\BalanceAmountBuilder;
use LoyaltyApIsLib\Models\Builders\BalanceCurrencyAmountBuilder;
use LoyaltyApIsLib\Models\BalanceCurrencyType;
use LoyaltyApIsLib\Models\Builders\BalanceAmountDetailBuilder;
use LoyaltyApIsLib\Models\BalanceState;
use LoyaltyApIsLib\Utils\DateTimeHelper;
use LoyaltyApIsLib\ApiHelper;

$customerBalances = CustomerBalancesBuilder::init()
    ->balances(
        [
            BalanceAmountBuilder::init()
                ->amounts(
                    [
                        BalanceCurrencyAmountBuilder::init(
                            BalanceCurrencyType::STAMP
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
                            ->build(),
                        BalanceCurrencyAmountBuilder::init(
                            BalanceCurrencyType::STAMP
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
                            ->build(),
                        BalanceCurrencyAmountBuilder::init(
                            BalanceCurrencyType::STAMP
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
                            ->build()
                    ]
                )
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            BalanceAmountBuilder::init()
                ->amounts(
                    [
                        BalanceCurrencyAmountBuilder::init(
                            BalanceCurrencyType::STAMP
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
                            ->build(),
                        BalanceCurrencyAmountBuilder::init(
                            BalanceCurrencyType::STAMP
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
                            ->build(),
                        BalanceCurrencyAmountBuilder::init(
                            BalanceCurrencyType::STAMP
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
                            ->build()
                    ]
                )
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

