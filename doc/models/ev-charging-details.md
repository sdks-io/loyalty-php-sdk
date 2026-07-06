
# Ev Charging Details

*This model accepts additional fields of type array.*

## Structure

`EvChargingDetails`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `chargePointSerialId` | `string` | Required | Charging point serial ID | getChargePointSerialId(): string | setChargePointSerialId(string chargePointSerialId): void |
| `chargePointConnectorTypeCd` | `?string` | Optional | Charging point connector type | getChargePointConnectorTypeCd(): ?string | setChargePointConnectorTypeCd(?string chargePointConnectorTypeCd): void |
| `chargePointConnectorTypeDesc` | `?string` | Optional | Charging point connector description | getChargePointConnectorTypeDesc(): ?string | setChargePointConnectorTypeDesc(?string chargePointConnectorTypeDesc): void |
| `startDateTime` | `DateTime` | Required | Date and time at which the transaction started. Format as per ISO 8601 standard. | getStartDateTime(): \DateTime | setStartDateTime(\DateTime startDateTime): void |
| `endDateTime` | `DateTime` | Required | Date and time at which the transaction ended. Format as per ISO 8601 standard. | getEndDateTime(): \DateTime | setEndDateTime(\DateTime endDateTime): void |
| `duration` | `int` | Required | Duration of the transaction in seconds.<br><br>**Default**: `0` | getDuration(): int | setDuration(int duration): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\EvChargingDetailsBuilder;
use LoyaltyApIsLib\Utils\DateTimeHelper;
use LoyaltyApIsLib\ApiHelper;

$evChargingDetails = EvChargingDetailsBuilder::init(
    'chargePointSerialId8',
    DateTimeHelper::fromRfc3339DateTimeRequired('2022-08-24T12:35:15Z'),
    DateTimeHelper::fromRfc3339DateTimeRequired('2022-08-24T12:54:15Z'),
    0
)
    ->chargePointConnectorTypeCd('chargePointConnectorTypeCd6')
    ->chargePointConnectorTypeDesc('chargePointConnectorTypeDesc2')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

