
# Access Code Response

*This model accepts additional fields of type array.*

## Structure

`AccessCodeResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accessCode` | `?string` | Optional | AccessCode provided by Shell after it redirects the user to the partner's URL. | getAccessCode(): ?string | setAccessCode(?string accessCode): void |
| `expiresIn` | `?int` | Optional | Indicates the number of seconds until the accessCode expires | getExpiresIn(): ?int | setExpiresIn(?int expiresIn): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\AccessCodeResponseBuilder;
use LoyaltyApIsLib\ApiHelper;

$accessCodeResponse = AccessCodeResponseBuilder::init()
    ->accessCode('AAAAAAAAAAAAA')
    ->expiresIn(30)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

