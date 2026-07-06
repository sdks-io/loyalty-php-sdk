
# Redeemed Item Product

*This model accepts additional fields of type array.*

## Structure

`RedeemedItemProduct`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `string` | Required | Unique Id of the product | getId(): string | setId(string id): void |
| `name` | `string` | Required | Name of the product | getName(): string | setName(string name): void |
| `productType` | [`string(ProductType)`](../../doc/models/product-type.md) | Required | Indicating the Type of the product (Fuel, CR, CC, PARTNER, OTHER, GREEN_ENERGY). | getProductType(): string | setProductType(string productType): void |
| `reasonForRedemption` | `?string` | Optional | Reason for redemption of points as mentioned by the partner. reasonForRedemption to be populated only for redeemedItems (not for saleItems) when productType = PARTNER. | getReasonForRedemption(): ?string | setReasonForRedemption(?string reasonForRedemption): void |
| `productCode` | `?string` | Optional | Product code of gift item (euroShell Forward Code). To be populated with 3 digit Euroshell product code. | getProductCode(): ?string | setProductCode(?string productCode): void |
| `productDescription` | `?string` | Optional | - | getProductDescription(): ?string | setProductDescription(?string productDescription): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\RedeemedItemProductBuilder;
use LoyaltyApIsLib\Models\ProductType;
use LoyaltyApIsLib\ApiHelper;

$redeemedItemProduct = RedeemedItemProductBuilder::init(
    '31AS2434',
    'Ferrari Umbrella',
    ProductType::PARTNER
)
    ->reasonForRedemption('Burgers')
    ->productCode('productCode4')
    ->productDescription('productDescription0')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

