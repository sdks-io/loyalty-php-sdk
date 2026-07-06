
# Custom Header Signature



Documentation for accessing and setting credentials for PrivateBasicToken.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| Public Basic Token | `string` | - | `publicBasicToken` | `getPublicBasicToken()` |



**Note:** Auth credentials can be set using `PrivateBasicTokenCredentialsBuilder::init()` in `privateBasicTokenCredentials` method in the client builder and accessed through `getPrivateBasicTokenCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```php
use LoyaltyApIsLib\Authentication\PrivateBasicTokenCredentialsBuilder;
use LoyaltyApIsLib\LoyaltyApIsClientBuilder;

$client = LoyaltyApIsClientBuilder::init()
    ->privateBasicTokenCredentials(
        PrivateBasicTokenCredentialsBuilder::init(
            'Public Basic Token'
        )
    )
    ->build();
```


