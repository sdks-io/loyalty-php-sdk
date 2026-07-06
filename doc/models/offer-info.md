
# Offer Info

*This model accepts additional fields of type array.*

## Structure

`OfferInfo`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `discountValue` | `float` | Required | Discount value of the offer | getDiscountValue(): float | setDiscountValue(float discountValue): void |
| `loyaltyOfferAmount` | `?int` | Optional | Total amount of points awarded for the given product code. | getLoyaltyOfferAmount(): ?int | setLoyaltyOfferAmount(?int loyaltyOfferAmount): void |
| `loyaltyOfferCode` | `?string` | Optional | Unique ID of the voucher/coupon. | getLoyaltyOfferCode(): ?string | setLoyaltyOfferCode(?string loyaltyOfferCode): void |
| `loyaltyOfferDescription` | `?string` | Optional | Name of loyalty offer | getLoyaltyOfferDescription(): ?string | setLoyaltyOfferDescription(?string loyaltyOfferDescription): void |
| `loyaltyOfferId` | `string` | Required | Loyalty Offer ID | getLoyaltyOfferId(): string | setLoyaltyOfferId(string loyaltyOfferId): void |
| `loyaltyOfferType` | `?string` | Optional | Loyalty offer type | getLoyaltyOfferType(): ?string | setLoyaltyOfferType(?string loyaltyOfferType): void |
| `loyaltySchemeCode` | `?string` | Optional | Loyalty Scheme code | getLoyaltySchemeCode(): ?string | setLoyaltySchemeCode(?string loyaltySchemeCode): void |
| `reason` | `string` | Required | Offer/reward name | getReason(): string | setReason(string reason): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\OfferInfoBuilder;
use LoyaltyApIsLib\ApiHelper;

$offerInfo = OfferInfoBuilder::init(
    14.12,
    '1234567890123',
    '10% Off on fuel'
)
    ->loyaltyOfferAmount(58)
    ->loyaltyOfferCode('loyaltyOfferCode8')
    ->loyaltyOfferDescription('loyaltyOfferDescription6')
    ->loyaltyOfferType('loyaltyOfferType4')
    ->loyaltySchemeCode('loyaltySchemeCode8')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

