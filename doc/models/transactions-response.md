
# Transactions Response

*This model accepts additional fields of type array.*

## Structure

`TransactionsResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `totalResults` | `int` | Required | Total no of resource which will be sent back across all pages | getTotalResults(): int | setTotalResults(int totalResults): void |
| `nextPage` | `string` | Required | API URI which must be used to retrieve the next page of resources | getNextPage(): string | setNextPage(string nextPage): void |
| `previousPage` | `string` | Required | API URI which must be used to retrieve the previous page of resources | getPreviousPage(): string | setPreviousPage(string previousPage): void |
| `totalSaved` | `float` | Required | Total amount saved so far | getTotalSaved(): float | setTotalSaved(float totalSaved): void |
| `transactions` | [`Transaction[]`](../../doc/models/transaction.md) | Required | Transactions list | getTransactions(): array | setTransactions(array transactions): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\TransactionsResponseBuilder;
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

$transactionsResponse = TransactionsResponseBuilder::init(
    80,
    '.../nextpage',
    '.../previouspage',
    227.3,
    [
        TransactionBuilder::init(
            194,
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
            94.62,
            120.32,
            122.62,
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
            ->build()
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

