
# Unprocessable Entity Error Response

*This model accepts additional fields of type array.*

## Structure

`UnprocessableEntityErrorResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `errorCode` | `float` | Required | HTTP error code 422 | getErrorCode(): float | setErrorCode(float errorCode): void |
| `message` | `string` | Required | HTTP error message - Unprocessable entity<br><br>**Constraints**: *Maximum Length*: `500` | getMessage(): string | setMessage(string message): void |
| `error` | [`ErrorInfo`](../../doc/models/error-info.md) | Required | - | getError(): ErrorInfo | setError(ErrorInfo error): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\UnprocessableEntityErrorResponseBuilder;
use LoyaltyApIsLib\Models\Builders\ErrorInfoBuilder;
use LoyaltyApIsLib\Models\Builders\ErrorPresenterBuilder;
use LoyaltyApIsLib\ApiHelper;

$unprocessableEntityErrorResponse = UnprocessableEntityErrorResponseBuilder::init(
    422,
    'Unprocessalbe entity',
    ErrorInfoBuilder::init(
        ErrorPresenterBuilder::init(
            '1002',
            'Error message for 1002'
        )
            ->reason('Reason of 1002')
            ->subject('1002 Subject')
            ->subjectType('Error subject type')
            ->type('Unknow Type')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
        ->developer(
            ErrorPresenterBuilder::init(
                'appErrorCode4',
                'message4'
            )
                ->reason('reason0')
                ->subject('subject8')
                ->subjectType('subjectType6')
                ->type('type6')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        )
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build()
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

