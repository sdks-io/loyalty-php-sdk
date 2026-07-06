
# Transaction Voucher

*This model accepts additional fields of type array.*

## Structure

`TransactionVoucher`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `detailType` | [`string(TransactionDetailType)`](../../doc/models/transaction-detail-type.md) | Required | Indicates the Type of the transaction detail row (award, redemption, transfer, voucher, refund or central award). | getDetailType(): string | setDetailType(string detailType): void |
| `code` | `string` | Required | Unique code of the voucher | getCode(): string | setCode(string code): void |
| `name` | `string` | Required | Name of the voucher | getName(): string | setName(string name): void |
| `amount` | `float` | Required | Sum amount of the voucher | getAmount(): float | setAmount(float amount): void |
| `quantity` | `float` | Required | Quantity of vouchers | getQuantity(): float | setQuantity(float quantity): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\TransactionVoucherBuilder;
use LoyaltyApIsLib\Models\TransactionDetailType;
use LoyaltyApIsLib\ApiHelper;

$transactionVoucher = TransactionVoucherBuilder::init(
    TransactionDetailType::REDEMPTION,
    '5000000100071',
    'Ferrari Umbrella',
    171.58,
    121.52
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

