
# Error Source

*This model accepts additional fields of type array.*

## Structure

`ErrorSource`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `pointer` | `?string` | Optional | - | getPointer(): ?string | setPointer(?string pointer): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\ErrorSourceBuilder;
use LoyaltyApIsLib\ApiHelper;

$errorSource = ErrorSourceBuilder::init()
    ->pointer('pointer4')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

