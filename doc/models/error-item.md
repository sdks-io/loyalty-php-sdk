
# Error Item

*This model accepts additional fields of type array.*

## Structure

`ErrorItem`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `status` | `?int` | Optional | - | getStatus(): ?int | setStatus(?int status): void |
| `title` | `?string` | Optional | - | getTitle(): ?string | setTitle(?string title): void |
| `source` | [`?ErrorSource`](../../doc/models/error-source.md) | Optional | - | getSource(): ?ErrorSource | setSource(?ErrorSource source): void |
| `detail` | `?string` | Optional | - | getDetail(): ?string | setDetail(?string detail): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\ErrorItemBuilder;
use LoyaltyApIsLib\Models\Builders\ErrorSourceBuilder;
use LoyaltyApIsLib\ApiHelper;

$errorItem = ErrorItemBuilder::init()
    ->status(222)
    ->title('title4')
    ->source(
        ErrorSourceBuilder::init()
            ->pointer('pointer6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->detail('detail4')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

