
# Bad Request Error

Request is missing a parameter so the server cannot proceed with the request.

## Structure

`BadRequestError`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `fault` | [`?Fault`](../../doc/models/fault.md) | Optional | - | getFault(): ?Fault | setFault(?Fault fault): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\BadRequestErrorBuilder;
use LoyaltyApIsLib\Models\Builders\FaultBuilder;
use LoyaltyApIsLib\Models\Builders\FaultDetailBuilder;
use LoyaltyApIsLib\ApiHelper;

$badRequestError = BadRequestErrorBuilder::init()
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

