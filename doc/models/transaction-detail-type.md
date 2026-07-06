
# Transaction Detail Type

Indicates the Type of the transaction detail row (award, redemption, transfer, voucher, refund or central award).

## Enumeration

`TransactionDetailType`

## Fields

| Name |
|  --- |
| `AWARD` |
| `REDEMPTION` |
| `TRANSFER` |
| `REFUND` |
| `CENTRAL_AWARD` |
| `VOUCHER` |

## Example

```php
use LoyaltyApIsLib\Models\TransactionDetailType;

$transactionDetailType = TransactionDetailType::TRANSFER;
```

