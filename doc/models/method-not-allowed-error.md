
# Method Not Allowed Error

An error response.

## Structure

`MethodNotAllowedError`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `fault` | [`?Fault`](../../doc/models/fault.md) | Optional | - | getFault(): ?Fault | setFault(?Fault fault): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\MethodNotAllowedErrorBuilder;
use LoyaltyApIsLib\Models\Builders\FaultBuilder;
use LoyaltyApIsLib\Models\Builders\FaultDetailBuilder;
use LoyaltyApIsLib\ApiHelper;

$methodNotAllowedError = MethodNotAllowedErrorBuilder::init()
    ->fault(
        FaultBuilder::init()
            ->faultstring('faultstring2')
            ->detail(
                FaultDetailBuilder::init()
                    ->errorcode('errorcode6')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            )
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->build();
```

