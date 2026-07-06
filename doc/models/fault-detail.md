
# Fault Detail

*This model accepts additional fields of type array.*

## Structure

`FaultDetail`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `errorcode` | `?string` | Optional | The error code. | getErrorcode(): ?string | setErrorcode(?string errorcode): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\FaultDetailBuilder;
use LoyaltyApIsLib\ApiHelper;

$faultDetail = FaultDetailBuilder::init()
    ->errorcode('The request contains bad syntax or cannot be fulfilled.')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

