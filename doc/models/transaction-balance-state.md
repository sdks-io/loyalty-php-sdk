
# Transaction Balance State

State of the amount

## Enumeration

`TransactionBalanceState`

## Fields

| Name |
|  --- |
| `AVAILABLE` |
| `EXPIRING` |
| `RESERVED` |
| `TARGET` |
| `BOOST` |
| `CHANGE` |
| `TOTAL_SPENT` |
| `EARNED` |
| `REDEEMED` |

## Example

```php
use LoyaltyApIsLib\Models\TransactionBalanceState;

$transactionBalanceState = TransactionBalanceState::REDEEMED;
```

