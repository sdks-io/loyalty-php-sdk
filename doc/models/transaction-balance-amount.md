
# Transaction Balance Amount

*This model accepts additional fields of type array.*

## Structure

`TransactionBalanceAmount`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `amount` | `float` | Required | Current value of specified balance | getAmount(): float | setAmount(float amount): void |
| `state` | [`string(TransactionBalanceState)`](../../doc/models/transaction-balance-state.md) | Required | State of the amount | getState(): string | setState(string state): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\TransactionBalanceAmountBuilder;
use LoyaltyApIsLib\Models\TransactionBalanceState;
use LoyaltyApIsLib\ApiHelper;

$transactionBalanceAmount = TransactionBalanceAmountBuilder::init(
    25.56,
    TransactionBalanceState::AVAILABLE
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

