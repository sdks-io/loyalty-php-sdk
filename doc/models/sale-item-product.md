
# Sale Item Product

*This model accepts additional fields of type array.*

## Structure

`SaleItemProduct`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `string` | Required | Unique Id of the product | getId(): string | setId(string id): void |
| `name` | `string` | Required | Name of the product | getName(): string | setName(string name): void |
| `productType` | [`string(ProductType)`](../../doc/models/product-type.md) | Required | Indicating the Type of the product (Fuel, CR, CC, PARTNER, OTHER, GREEN_ENERGY). | getProductType(): string | setProductType(string productType): void |
| `productCode` | `?string` | Optional | Product code of gift item (euroShell Forward Code). To be populated with 3 digit Euroshell product code. | getProductCode(): ?string | setProductCode(?string productCode): void |
| `productDescription` | `?string` | Optional | - | getProductDescription(): ?string | setProductDescription(?string productDescription): void |
| `additionalProductDescription` | `?string` | Optional | Customer name of the product provided by the partner<br><br>**Constraints**: *Maximum Length*: `100` | getAdditionalProductDescription(): ?string | setAdditionalProductDescription(?string additionalProductDescription): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\SaleItemProductBuilder;
use LoyaltyApIsLib\Models\ProductType;
use LoyaltyApIsLib\ApiHelper;

$saleItemProduct = SaleItemProductBuilder::init(
    '31AS2434',
    'Ferrari Umbrella',
    ProductType::PARTNER
)
    ->productCode('productCode4')
    ->productDescription('productDescription0')
    ->additionalProductDescription('King Guest Room')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

