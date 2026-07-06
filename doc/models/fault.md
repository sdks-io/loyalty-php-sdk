
# Fault

*This model accepts additional fields of type array.*

## Structure

`Fault`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `faultstring` | `?string` | Optional | The description of the error. | getFaultstring(): ?string | setFaultstring(?string faultstring): void |
| `detail` | [`?FaultDetail`](../../doc/models/fault-detail.md) | Optional | - | getDetail(): ?FaultDetail | setDetail(?FaultDetail detail): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\FaultBuilder;
use LoyaltyApIsLib\Models\Builders\FaultDetailBuilder;
use LoyaltyApIsLib\ApiHelper;

$fault = FaultBuilder::init()
    ->faultstring('Bad Request')
    ->detail(
        FaultDetailBuilder::init()
            ->errorcode('errorcode6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

