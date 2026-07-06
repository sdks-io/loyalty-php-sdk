
# Offer Base

*This model accepts additional fields of type array.*

## Structure

`OfferBase`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `offerId` | `int` | Required | Offer ID provided upon offer configuration | getOfferId(): int | setOfferId(int offerId): void |
| `referenceId` | `string` | Required | Unique Reference ID for the transaction from the partner. Used to identify duplicate requests.<br><br>**Constraints**: *Maximum Length*: `128` | getReferenceId(): string | setReferenceId(string referenceId): void |
| `title` | `string` | Required | Title of the partner's offer, given upon configuration<br><br>**Constraints**: *Maximum Length*: `4000` | getTitle(): string | setTitle(string title): void |
| `description` | `string` | Required | Description of the partner's offer, set up upon offer configuration<br><br>**Constraints**: *Maximum Length*: `4000` | getDescription(): string | setDescription(string description): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\OfferBaseBuilder;
use LoyaltyApIsLib\ApiHelper;

$offerBase = OfferBaseBuilder::init(
    5231933,
    'as3df5131fas3f54f92h5df',
    'Partner\'s offer title',
    'Buy 1 get 2'
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

