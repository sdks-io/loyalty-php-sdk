
# Custom Header Signature



Documentation for accessing and setting credentials for customerHeader.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| Authorization-Token | `string` | The partner's API key | `authorizationToken` | `getAuthorizationToken()` |



**Note:** Auth credentials can be set using `CustomerHeaderCredentialsBuilder::init()` in `customerHeaderCredentials` method in the client builder and accessed through `getCustomerHeaderCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```php
use LoyaltyApIsLib\Authentication\CustomerHeaderCredentialsBuilder;
use LoyaltyApIsLib\LoyaltyApIsClientBuilder;

$client = LoyaltyApIsClientBuilder::init()
    ->customerHeaderCredentials(
        CustomerHeaderCredentialsBuilder::init(
            'Authorization-Token'
        )
    )
    ->build();
```


