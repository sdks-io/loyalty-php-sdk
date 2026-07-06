
# Balance Amount Detail

*This model accepts additional fields of type array.*

## Structure

`BalanceAmountDetail`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `amount` | `float` | Required | Current value of specified balance. | getAmount(): float | setAmount(float amount): void |
| `state` | [`string(BalanceState)`](../../doc/models/balance-state.md) | Required | State of the points balance amount.<br><br>**Constraints**: *Minimum Length*: `1` | getState(): string | setState(string state): void |
| `dateTime` | `DateTime` | Required | Expiration Date in JSON recommended format: “yyyy-MM-ddTHH:mm:ssZ” Nullable. | getDateTime(): \DateTime | setDateTime(\DateTime dateTime): void |
| `dateTimestamp` | `int` | Required | Date as Unix epoch (UTC). | getDateTimestamp(): int | setDateTimestamp(int dateTimestamp): void |
| `cashAmount` | `?float` | Optional | Point to cash exchange amnount. | getCashAmount(): ?float | setCashAmount(?float cashAmount): void |
| `period` | `?int` | Optional | Period of expiration, minimum value is 1. Seralized only when it’s not null.<br><br>**Constraints**: `>= 1` | getPeriod(): ?int | setPeriod(?int period): void |
| `position` | `?(int[])` | Optional | The list of numbers describes an index of boost’s position in qualifying visit, Seralized only when it’s not null and not empty.<br><br>**Constraints**: *Unique Items Required* | getPosition(): ?array | setPosition(?array position): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\BalanceAmountDetailBuilder;
use LoyaltyApIsLib\Models\BalanceState;
use LoyaltyApIsLib\Utils\DateTimeHelper;
use LoyaltyApIsLib\ApiHelper;

$balanceAmountDetail = BalanceAmountDetailBuilder::init(
    5,
    BalanceState::AVAILABLE,
    DateTimeHelper::fromRfc3339DateTimeRequired('2022-02-25T15:16:29Z'),
    1645802189000
)
    ->cashAmount(7.5)
    ->period(1)
    ->position(
        [
            237,
            238,
            239
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

