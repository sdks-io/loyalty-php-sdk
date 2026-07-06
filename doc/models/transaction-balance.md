
# Transaction Balance

*This model accepts additional fields of type array.*

## Structure

`TransactionBalance`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `currencyType` | [`string(TransactionCurrencyType)`](../../doc/models/transaction-currency-type.md) | Required | Type of balance | getCurrencyType(): string | setCurrencyType(string currencyType): void |
| `amounts` | [`TransactionBalanceAmount[]`](../../doc/models/transaction-balance-amount.md) | Required | - | getAmounts(): array | setAmounts(array amounts): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\TransactionBalanceBuilder;
use LoyaltyApIsLib\Models\TransactionCurrencyType;
use LoyaltyApIsLib\Models\Builders\TransactionBalanceAmountBuilder;
use LoyaltyApIsLib\Models\TransactionBalanceState;
use LoyaltyApIsLib\ApiHelper;

$transactionBalance = TransactionBalanceBuilder::init(
    TransactionCurrencyType::AIRMILES,
    [
        TransactionBalanceAmountBuilder::init(
            104.18,
            TransactionBalanceState::AVAILABLE
        )
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

