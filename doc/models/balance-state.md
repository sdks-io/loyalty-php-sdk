
# Balance State

State of the points balance amount.

## Enumeration

`BalanceState`

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
| `TOTAL` |
| `LAST` |

## Example

```php
use LoyaltyApIsLib\Models\BalanceState;

$balanceState = BalanceState::RESERVED;
```

