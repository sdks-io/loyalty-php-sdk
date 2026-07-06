
# Offer Assignment

*This model accepts additional fields of type array.*

## Structure

`OfferAssignment`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `referenceId` | `string` | Required | Unique Reference ID for the transaction from the partner. Used to identify duplicate requests.<br><br>**Constraints**: *Maximum Length*: `128` | getReferenceId(): string | setReferenceId(string referenceId): void |
| `consumerUuid` | `string` | Required | SSO uuid of the user signed in with Shell credentials<br>Format: 32 hexadecimal digits grouped the following way: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx | getConsumerUuid(): string | setConsumerUuid(string consumerUuid): void |
| `offerId` | `string` | Required | Offer identifier shared by Shell.<br>Format: string(30)<br><br>**Constraints**: *Maximum Length*: `30` | getOfferId(): string | setOfferId(string offerId): void |
| `validFrom` | `?DateTime` | Optional | Offer validity start date in JSON recommended format: "yyyy-MM-ddTHH:mm:ssZ".<br><br>The date format must follow ISO_8601. If 'Z' is written immediately after the time, it is considered UTC.<br><br>Time offset from UTC can be appended instead of 'Z' using plus or minus signs. Negative UTC offsets describe a time zone west of UTC�00:00, where the civil time is behind (or earlier) than UTC. Positive UTC offsets describe a time zone east of UTC�00:00, where the civil time is ahead (or later) than UTC | getValidFrom(): ?\DateTime | setValidFrom(?\DateTime validFrom): void |
| `validityPeriod` | `?float` | Optional | Offer validity period (Number of days)<br>If validityPeriod is greater than zero, validTo will be ignored.<br>The offer will be valid till:<br>validfrom + validityperiod<br>If the resulting valid to date would be during the day, then its validity is modified to last until midnight in the timezone of the validFrom date.<br>E.g. If valiFrom is "2021-03-08T17:12:55Z+01:00" (Central European time) and validtyPeriod is 3 then the offer will be valid till "2021-03-11T23:59:59Z+01:00" (Central European Time)<br><br>**Constraints**: `>= 0`, `<= 999999` | getValidityPeriod(): ?float | setValidityPeriod(?float validityPeriod): void |
| `validTo` | `?DateTime` | Optional | Offer validity end date in JSON recommended format: "yyyy-MM-ddTHH:mm:ssZ".<br>Field value is ignored if validityPeriod is bigger than zero.<br><br>The date format must follow ISO_8601. If 'Z' is written immediately after the time, it is considered UTC.<br><br>Time offset from UTC can be appended instead of 'Z' using plus or minus signs. Negative UTC offsets describe a time zone west of UTC�00:00, where the civil time is behind (or earlier) than UTC. Positive UTC offsets describe a time zone east of UTC�00:00, where the civil time is ahead (or later) than UTC | getValidTo(): ?\DateTime | setValidTo(?\DateTime validTo): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\OfferAssignmentBuilder;
use LoyaltyApIsLib\Utils\DateTimeHelper;
use LoyaltyApIsLib\ApiHelper;

$offerAssignment = OfferAssignmentBuilder::init(
    'as3df5131fas3f54f92h5df',
    'cee1157e-cac0-4fc6-b92b-68a13b456b43',
    'offerId1234'
)
    ->validFrom(DateTimeHelper::fromRfc3339DateTime('2021-03-08T17:12:55Z'))
    ->validityPeriod(31)
    ->validTo(DateTimeHelper::fromRfc3339DateTime('2021-03-08T17:12:55Z'))
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

