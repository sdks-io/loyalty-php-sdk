
# OAuth 2 Bearer token



Documentation for accessing and setting credentials for PublicBearerToken.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| AccessToken | `string` | The OAuth 2.0 Access Token to use for API requests. | `accessToken` | `getAccessToken()` |



**Note:** Auth credentials can be set using `PublicBearerTokenCredentialsBuilder::init()` in `publicBearerTokenCredentials` method in the client builder and accessed through `getPublicBearerTokenCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```php
use LoyaltyApIsLib\Authentication\PublicBearerTokenCredentialsBuilder;
use LoyaltyApIsLib\LoyaltyApIsClientBuilder;

$client = LoyaltyApIsClientBuilder::init()
    ->publicBearerTokenCredentials(
        PublicBearerTokenCredentialsBuilder::init(
            'AccessToken'
        )
    )
    ->build();
```


