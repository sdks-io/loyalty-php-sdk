
# Offer Language

*This model accepts additional fields of type array.*

## Structure

`OfferLanguage`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `string` | Required | Unique Id of the offer | getId(): string | setId(string id): void |
| `title` | `string` | Required | Title of the offer | getTitle(): string | setTitle(string title): void |
| `description` | `string` | Required | Description of the offer | getDescription(): string | setDescription(string description): void |
| `customText` | `string` | Required | Custom text of the offer | getCustomText(): string | setCustomText(string customText): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\OfferLanguageBuilder;
use LoyaltyApIsLib\ApiHelper;

$offerLanguage = OfferLanguageBuilder::init(
    '31AS2434',
    '10% OFF of Ferrari Umbrella',
    'Description of 10% OFF of Ferrari Umbrella',
    'Custom text'
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

