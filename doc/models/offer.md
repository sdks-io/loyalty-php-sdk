
# Offer

*This model accepts additional fields of type array.*

## Structure

`Offer`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `offerId` | `int` | Required | Offer ID provided upon offer configuration | getOfferId(): int | setOfferId(int offerId): void |
| `referenceId` | `string` | Required | Unique Reference ID for the transaction from the partner. Used to identify duplicate requests.<br><br>**Constraints**: *Maximum Length*: `128` | getReferenceId(): string | setReferenceId(string referenceId): void |
| `title` | `string` | Required | Title of the partner's offer, given upon configuration<br><br>**Constraints**: *Maximum Length*: `4000` | getTitle(): string | setTitle(string title): void |
| `description` | `string` | Required | Description of the partner's offer, set up upon offer configuration<br><br>**Constraints**: *Maximum Length*: `4000` | getDescription(): string | setDescription(string description): void |
| `validFrom` | `DateTime` | Required | Offer validity start date in JSON recommended format: "yyyy-MM-ddTHH:mm:ssZ".<br><br>The date format must follow ISO_8601. If 'Z' is written immediately after the time, it is considered UTC.<br><br>Time offset from UTC can be appended instead of 'Z' using plus or minus signs. Negative UTC offsets describe a time zone west of UTC�00:00, where the civil time is behind (or earlier) than UTC. Positive UTC offsets describe a time zone east of UTC�00:00, where the civil time is ahead (or later) than UTC | getValidFrom(): \DateTime | setValidFrom(\DateTime validFrom): void |
| `validTo` | `?DateTime` | Optional | Offer validity end date in JSON recommended format: "yyyy-MM-ddTHH:mm:ssZ".<br><br>The date format must follow ISO_8601. If 'Z' is written immediately after the time, it is considered UTC.<br><br>Time offset from UTC can be appended instead of 'Z' using plus or minus signs. Negative UTC offsets describe a time zone west of UTC�00:00, where the civil time is behind (or earlier) than UTC. Positive UTC offsets describe a time zone east of UTC�00:00, where the civil time is ahead (or later) than UTC<br><br>Nullable field value, in case of the offer has infinite valid to. | getValidTo(): ?\DateTime | setValidTo(?\DateTime validTo): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\OfferBuilder;
use LoyaltyApIsLib\Utils\DateTimeHelper;
use LoyaltyApIsLib\ApiHelper;

$offer = OfferBuilder::init(
    5231933,
    'as3df5131fas3f54f92h5df',
    'Partner\'s offer title',
    'Buy 1 get 2',
    DateTimeHelper::fromRfc3339DateTimeRequired('2021-03-08T17:12:55Z')
)
    ->validTo(DateTimeHelper::fromRfc3339DateTime('2021-03-08T17:12:55Z'))
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

