
# Error Info

*This model accepts additional fields of type array.*

## Structure

`ErrorInfo`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `user` | [`ErrorPresenter`](../../doc/models/error-presenter.md) | Required | - | getUser(): ErrorPresenter | setUser(ErrorPresenter user): void |
| `developer` | [`?ErrorPresenter`](../../doc/models/error-presenter.md) | Optional | - | getDeveloper(): ?ErrorPresenter | setDeveloper(?ErrorPresenter developer): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\ErrorInfoBuilder;
use LoyaltyApIsLib\Models\Builders\ErrorPresenterBuilder;
use LoyaltyApIsLib\ApiHelper;

$errorInfo = ErrorInfoBuilder::init(
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
    ->build();
```

