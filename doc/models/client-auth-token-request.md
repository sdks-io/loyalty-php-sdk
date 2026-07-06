
# Client Auth Token Request

## Structure

`ClientAuthTokenRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `clientId` | `string` | Required | Client ID provided by Shell | getClientId(): string | setClientId(string clientId): void |
| `clientSecret` | `string` | Required | Client Secret provided by Shell | getClientSecret(): string | setClientSecret(string clientSecret): void |
| `grantType` | `string` | Required | Grant type value for access<br><br>**Constraints**: *Maximum Length*: `20` | getGrantType(): string | setGrantType(string grantType): void |

## Example

```php
use LoyaltyApIsLib\Models\Builders\ClientAuthTokenRequestBuilder;

$clientAuthTokenRequest = ClientAuthTokenRequestBuilder::init(
    'twuwywTYUHAH6AHHJ',
    'yuahaYThdvdowoUUU7wjsjMM',
    'client_credentials'
)->build();
```

