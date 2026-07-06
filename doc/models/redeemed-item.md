
# Redeemed Item

*This model accepts additional fields of type array.*

## Structure

`RedeemedItem`

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
| `productData` | [`RedeemedItemProduct`](../../doc/models/redeemed-item-product.md) | Required | - | getProductData(): RedeemedItemProduct | setProductData(RedeemedItemProduct productData): void |
| `quantity` | `float` | Required | Quantity of product | getQuantity(): float | setQuantity(float quantity): void |
| `vatAmount` | `?float` | Optional | Value added tax | getVatAmount(): ?float | setVatAmount(?float vatAmount): void |
| `vatRate` | `?float` | Optional | VAT rate of sales line | getVatRate(): ?float | setVatRate(?float vatRate): void |
| `points` | `?int` | Optional | Number of points redeemed. Applicable for redeemedItems and not for saleItems | getPoints(): ?int | setPoints(?int points): void |
| `vouchers` | `?(string[])` | Optional | List of vouchers | getVouchers(): ?array | setVouchers(?array vouchers): void |
| `voucherItems` | [`?(VoucherItem[])`](../../doc/models/voucher-item.md) | Optional | - | getVoucherItems(): ?array | setVoucherItems(?array voucherItems): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\RedeemedItemBuilder;
use LoyaltyApIsLib\Models\TransactionDetailType;
use LoyaltyApIsLib\Models\Builders\OfferInfoBuilder;
use LoyaltyApIsLib\ApiHelper;
use LoyaltyApIsLib\Models\Builders\RedeemedItemProductBuilder;
use LoyaltyApIsLib\Models\ProductType;
use LoyaltyApIsLib\Models\Builders\OfferLanguageBuilder;

$redeemedItem = RedeemedItemBuilder::init(
    172.08,
    TransactionDetailType::REDEMPTION,
    45.58,
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
    32.5,
    RedeemedItemProductBuilder::init(
        '31AS2434',
        'Ferrari Umbrella',
        ProductType::PARTNER
    )
        ->reasonForRedemption('Burgers')
        ->productCode('productCode4')
        ->productDescription('productDescription0')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    122.02
)
    ->description('description6')
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
    ->vatAmount(154.38)
    ->vatRate(139.42)
    ->points(122)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

