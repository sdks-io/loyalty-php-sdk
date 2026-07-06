
# Json Api Version

*This model accepts additional fields of type array.*

## Structure

`JsonApiVersion`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `version` | `?string` | Optional | - | getVersion(): ?string | setVersion(?string version): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\JsonApiVersionBuilder;
use LoyaltyApIsLib\ApiHelper;

$jsonApiVersion = JsonApiVersionBuilder::init()
    ->version('version6')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

