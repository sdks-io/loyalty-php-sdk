
# Sale Item

*This model accepts additional fields of type array.*

## Structure

`SaleItem`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `description` | `?string` | Optional | Description - currently not in use | getDescription(): ?string | setDescription(?string description): void |
| `amount` | `float` | Required | Total amount | getAmount(): float | setAmount(float amount): void |
| `detailType` | [`string(TransactionDetailType)`](../../doc/models/transaction-detail-type.md) | Required | Indicates the Type of the transaction detail row (award, redemption, transfer, voucher, refund or central award). | getDetailType(): string | setDetailType(string detailType): void |
| `discountAmount` | `float` | Required | Discount amount of sales line | getDiscountAmount(): float | setDiscountAmount(float discountAmount): void |
| `offerInfos` | [`OfferInfo[]`](../../doc/models/offer-info.md) | Required | - | getOfferInfos(): array | setOfferInfos(array offerInfos): void |
| `offerLang` | [`?OfferLanguage`](../../doc/models/offer-language.md) | Optional | - | getOfferLang(): ?OfferLanguage | setOfferLang(?OfferLanguage offerLang): void |
| `originalAmount` | `float` | Required | Original amount of sales line | getOriginalAmount(): float | setOriginalAmount(float originalAmount): void |
| `originalNetAmount` | `?float` | Optional | Original amount excluding VAT | getOriginalNetAmount(): ?float | setOriginalNetAmount(?float originalNetAmount): void |
| `productData` | [`SaleItemProduct`](../../doc/models/sale-item-product.md) | Required | - | getProductData(): SaleItemProduct | setProductData(SaleItemProduct productData): void |
| `quantity` | `float` | Required | Quantity of product | getQuantity(): float | setQuantity(float quantity): void |
| `vatAmount` | `?float` | Optional | Value added tax | getVatAmount(): ?float | setVatAmount(?float vatAmount): void |
| `vatRate` | `?float` | Optional | VAT rate of sales line | getVatRate(): ?float | setVatRate(?float vatRate): void |
| `voucherItems` | [`?(VoucherItem[])`](../../doc/models/voucher-item.md) | Optional | - | getVoucherItems(): ?array | setVoucherItems(?array voucherItems): void |
| `vouchers` | `?(string[])` | Optional | List of vouchers | getVouchers(): ?array | setVouchers(?array vouchers): void |
| `unitPrice` | `?float` | Optional | Unit price of sale item | getUnitPrice(): ?float | setUnitPrice(?float unitPrice): void |
| `unitMeasure` | [`?string(UnitMeasure)`](../../doc/models/unit-measure.md) | Optional | Unit of measure | getUnitMeasure(): ?string | setUnitMeasure(?string unitMeasure): void |
| `ev` | [`?EvChargingDetails`](../../doc/models/ev-charging-details.md) | Optional | - | getEv(): ?EvChargingDetails | setEv(?EvChargingDetails ev): void |
| `points` | `?int` | Optional | Points earned in a transaction | getPoints(): ?int | setPoints(?int points): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\SaleItemBuilder;
use LoyaltyApIsLib\Models\TransactionDetailType;
use LoyaltyApIsLib\Models\Builders\OfferInfoBuilder;
use LoyaltyApIsLib\ApiHelper;
use LoyaltyApIsLib\Models\Builders\SaleItemProductBuilder;
use LoyaltyApIsLib\Models\ProductType;
use LoyaltyApIsLib\Models\Builders\OfferLanguageBuilder;
use LoyaltyApIsLib\Models\UnitMeasure;

$saleItem = SaleItemBuilder::init(
    61.72,
    TransactionDetailType::REDEMPTION,
    191.22,
    [
        OfferInfoBuilder::init(
            53.28,
            '1234567890123',
            '10% Off on fuel'
        )
            ->loyaltyOfferAmount(134)
            ->loyaltyOfferCode('loyaltyOfferCode2')
            ->loyaltyOfferDescription('loyaltyOfferDescription2')
            ->loyaltyOfferType('loyaltyOfferType0')
            ->loyaltySchemeCode('loyaltySchemeCode4')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    178.14,
    SaleItemProductBuilder::init(
        '31AS2434',
        'Ferrari Umbrella',
        ProductType::PARTNER
    )
        ->productCode('productCode4')
        ->productDescription('productDescription0')
        ->additionalProductDescription('King Guest Room')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    11.66
)
    ->description('Not in use')
    ->offerLang(
        OfferLanguageBuilder::init(
            'id8',
            'title6',
            'description2',
            'customText2'
        )
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->originalNetAmount(81.9)
    ->vatAmount(8.74)
    ->vatRate(29.06)
    ->unitMeasure(UnitMeasure::LITRE)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

