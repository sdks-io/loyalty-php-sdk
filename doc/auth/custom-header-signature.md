
# Custom Header Signature



Documentation for accessing and setting credentials for PublicBasicToken.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| Public Basic Token | `string` | - | `publicBasicToken` | `getPublicBasicToken()` |



**Note:** Auth credentials can be set using `PublicBasicTokenCredentialsBuilder::init()` in `publicBasicTokenCredentials` method in the client builder and accessed through `getPublicBasicTokenCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```php
use LoyaltyApIsLib\Authentication\PublicBasicTokenCredentialsBuilder;
use LoyaltyApIsLib\LoyaltyApIsClientBuilder;

$client = LoyaltyApIsClientBuilder::init()
    ->publicBasicTokenCredentials(
        PublicBasicTokenCredentialsBuilder::init(
            'Public Basic Token'
        )
    )
    ->build();
```


