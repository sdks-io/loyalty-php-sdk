
# Site Data

*This model accepts additional fields of type array.*

## Structure

`SiteData`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `countryCode` | `string` | Required | Two character ISO 3166-1 alpha-2 country code | getCountryCode(): string | setCountryCode(string countryCode): void |
| `siteId` | `string` | Required | Unique Id of the site | getSiteId(): string | setSiteId(string siteId): void |
| `name` | `string` | Required | Name of the site | getName(): string | setName(string name): void |
| `postcode` | `?string` | Optional | Postcode of the site | getPostcode(): ?string | setPostcode(?string postcode): void |
| `city` | `?string` | Optional | City of the site | getCity(): ?string | setCity(?string city): void |
| `address` | `?string` | Optional | Address of the site | getAddress(): ?string | setAddress(?string address): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\SiteDataBuilder;
use LoyaltyApIsLib\ApiHelper;

$siteData = SiteDataBuilder::init(
    'GB',
    '23St34',
    'Shell Liphook North'
)
    ->postcode('GU30 7TT')
    ->city('Liphook')
    ->address('A3 T North')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

