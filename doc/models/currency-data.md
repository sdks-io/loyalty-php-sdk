
# Currency Data

currencyData is only filled, where there is possible non-same currency cross-border transaction

*This model accepts additional fields of type array.*

## Structure

`CurrencyData`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `code` | `string` | Required | Currency code | getCode(): string | setCode(string code): void |
| `symbol` | `string` | Required | Currency symbol | getSymbol(): string | setSymbol(string symbol): void |
| `isSuffix` | `bool` | Required | Currency format (is the symbol after the value) | getIsSuffix(): bool | setIsSuffix(bool isSuffix): void |
| `hasSpace` | `bool` | Required | Currency format (is there a space between the symbol and the value) | getHasSpace(): bool | setHasSpace(bool hasSpace): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\CurrencyDataBuilder;
use LoyaltyApIsLib\ApiHelper;

$currencyData = CurrencyDataBuilder::init(
    'USD',
    '$',
    false,
    false
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

