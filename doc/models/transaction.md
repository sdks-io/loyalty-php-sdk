
# Transaction

*This model accepts additional fields of type array.*

## Structure

`Transaction`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `transactionDateTime` | `int` | Required | Transaction date as Unix epoch (UTC), as requested by MobGen. | getTransactionDateTime(): int | setTransactionDateTime(int transactionDateTime): void |
| `transactionDateTimeStamp` | `?DateTime` | Optional | Transaction date in JSON recommended format: “yyyy-MM-ddTHH:mm:ssZ” | getTransactionDateTimeStamp(): ?\DateTime | setTransactionDateTimeStamp(?\DateTime transactionDateTimeStamp): void |
| `siteData` | [`SiteData`](../../doc/models/site-data.md) | Required | - | getSiteData(): SiteData | setSiteData(SiteData siteData): void |
| `loyalty` | [`LoyaltyCardInfo`](../../doc/models/loyalty-card-info.md) | Required | - | getLoyalty(): LoyaltyCardInfo | setLoyalty(LoyaltyCardInfo loyalty): void |
| `transactionId` | `?string` | Optional | Unique Id of the transaction row. | getTransactionId(): ?string | setTransactionId(?string transactionId): void |
| `partnerCode` | `?string` | Optional | Unique code identifying the partner | getPartnerCode(): ?string | setPartnerCode(?string partnerCode): void |
| `partnerName` | `?string` | Optional | Name of the partner | getPartnerName(): ?string | setPartnerName(?string partnerName): void |
| `partnerLogo` | `?string` | Optional | - | getPartnerLogo(): ?string | setPartnerLogo(?string partnerLogo): void |
| `referenceId` | `?string` | Optional | Reference ID for each transaction. It is unique for each partner and transaction. | getReferenceId(): ?string | setReferenceId(?string referenceId): void |
| `totalAmount` | `float` | Required | Total amount of the transaction. | getTotalAmount(): float | setTotalAmount(float totalAmount): void |
| `totalDiscountAmount` | `float` | Required | Total discount amount of the transaction. | getTotalDiscountAmount(): float | setTotalDiscountAmount(float totalDiscountAmount): void |
| `totalDiscountedFullAmount` | `float` | Required | totalAmount - totalDiscountedFullAmount | getTotalDiscountedFullAmount(): float | setTotalDiscountedFullAmount(float totalDiscountedFullAmount): void |
| `totalVatAmount` | `?float` | Optional | Total amount of VAT | getTotalVatAmount(): ?float | setTotalVatAmount(?float totalVatAmount): void |
| `balances` | [`?(TransactionBalance[])`](../../doc/models/transaction-balance.md) | Optional | - | getBalances(): ?array | setBalances(?array balances): void |
| `currencyCode` | `?string` | Optional | Currency using ISO4217 alpha-3 currency code | getCurrencyCode(): ?string | setCurrencyCode(?string currencyCode): void |
| `saleItems` | [`SaleItem[]`](../../doc/models/sale-item.md) | Required | - | getSaleItems(): array | setSaleItems(array saleItems): void |
| `redeemedItems` | [`RedeemedItem[]`](../../doc/models/redeemed-item.md) | Required | - | getRedeemedItems(): array | setRedeemedItems(array redeemedItems): void |
| `transactionVouchers` | [`TransactionVoucher[]`](../../doc/models/transaction-voucher.md) | Required | - | getTransactionVouchers(): array | setTransactionVouchers(array transactionVouchers): void |
| `receiptNumber` | `?string` | Optional | Unique number of transaction's receipt | getReceiptNumber(): ?string | setReceiptNumber(?string receiptNumber): void |
| `pointsToCash` | [`?PointsToCash`](../../doc/models/points-to-cash.md) | Optional | - | getPointsToCash(): ?PointsToCash | setPointsToCash(?PointsToCash pointsToCash): void |
| `companyId` | `?int` | Optional | Partner identifier | getCompanyId(): ?int | setCompanyId(?int companyId): void |
| `isPartnerRedemption` | `?bool` | Optional | Describes whether the transaction is partner redemption. | getIsPartnerRedemption(): ?bool | setIsPartnerRedemption(?bool isPartnerRedemption): void |
| `currencyData` | [`?CurrencyData`](../../doc/models/currency-data.md) | Optional | currencyData is only filled, where there is possible non-same currency cross-border transaction | getCurrencyData(): ?CurrencyData | setCurrencyData(?CurrencyData currencyData): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\TransactionBuilder;
use LoyaltyApIsLib\Models\Builders\SiteDataBuilder;
use LoyaltyApIsLib\ApiHelper;
use LoyaltyApIsLib\Models\Builders\LoyaltyCardInfoBuilder;
use LoyaltyApIsLib\Models\Builders\SaleItemBuilder;
use LoyaltyApIsLib\Models\TransactionDetailType;
use LoyaltyApIsLib\Models\Builders\OfferInfoBuilder;
use LoyaltyApIsLib\Models\Builders\SaleItemProductBuilder;
use LoyaltyApIsLib\Models\ProductType;
use LoyaltyApIsLib\Models\Builders\OfferLanguageBuilder;
use LoyaltyApIsLib\Utils\DateTimeHelper;
use LoyaltyApIsLib\Models\UnitMeasure;
use LoyaltyApIsLib\Models\Builders\RedeemedItemBuilder;
use LoyaltyApIsLib\Models\Builders\RedeemedItemProductBuilder;
use LoyaltyApIsLib\Models\Builders\TransactionVoucherBuilder;

$transaction = TransactionBuilder::init(
    168,
    SiteDataBuilder::init(
        'GB',
        '23St34',
        'Shell Liphook North'
    )
        ->postcode('GU30 7TT')
        ->city('Liphook')
        ->address('A3 T North')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    LoyaltyCardInfoBuilder::init()
        ->loyaltyCard('1234567890123456789')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    96.12,
    118.82,
    124.12,
    [
        SaleItemBuilder::init(
            33.74,
            TransactionDetailType::REDEMPTION,
            163.24,
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
            150.16,
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
            239.68
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
            ->originalNetAmount(53.92)
            ->vatAmount(36.72)
            ->vatRate(1.08)
            ->unitMeasure(UnitMeasure::LITRE)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    [
        RedeemedItemBuilder::init(
            7.62,
            TransactionDetailType::REDEMPTION,
            137.12,
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
            124.04,
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
            213.56
        )
            ->description('description0')
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
            ->vatAmount(62.84)
            ->vatRate(230.96)
            ->points(60)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    [
        TransactionVoucherBuilder::init(
            TransactionDetailType::REDEMPTION,
            '5000000100071',
            'Ferrari Umbrella',
            8.04,
            213.98
        )
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->transactionDateTimeStamp(DateTimeHelper::fromRfc3339DateTime('2022-01-21T12:35:15Z'))
    ->transactionId('8435166weew2332w')
    ->partnerCode('GB10CMLP_RAC')
    ->partnerName('RAC')
    ->partnerLogo('https://www.shell.co.uk/1234.jpg')
    ->referenceId('abcde12345xyz')
    ->currencyCode('GBP')
    ->receiptNumber('18a6sdf8a63448612')
    ->isPartnerRedemption(true)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

