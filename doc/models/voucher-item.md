
# Voucher Item

*This model accepts additional fields of type array.*

## Structure

`VoucherItem`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `code` | `string` | Required | Voucher code | getCode(): string | setCode(string code): void |
| `expiryDate` | `int` | Required | Expiry date as Unix epoch (UTC), as requested by MobGen. | getExpiryDate(): int | setExpiryDate(int expiryDate): void |
| `expiryDateTimestamp` | `DateTime` | Required | Expiry date in JSON recommended format: “yyyy-MM-ddTHH:mm:ssZ” | getExpiryDateTimestamp(): \DateTime | setExpiryDateTimestamp(\DateTime expiryDateTimestamp): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\VoucherItemBuilder;
use LoyaltyApIsLib\Utils\DateTimeHelper;
use LoyaltyApIsLib\ApiHelper;

$voucherItem = VoucherItemBuilder::init(
    'test123',
    166,
    DateTimeHelper::fromRfc3339DateTimeRequired('2022-01-30T12:35:15Z')
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

