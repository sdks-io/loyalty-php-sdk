
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.SIT`** |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](../doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](../doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| publicBearerTokenCredentials | [`PublicBearerTokenCredentials`](auth/oauth-2-bearer-token.md) | The Credentials Setter for OAuth 2 Bearer token |
| publicBasicTokenCredentials | [`PublicBasicTokenCredentials`](auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |
| privateBasicTokenCredentials | [`PrivateBasicTokenCredentials`](auth/custom-header-signature-1.md) | The Credentials Setter for Custom Header Signature |
| clientAuthorizationTokenCredentials | [`ClientAuthorizationTokenCredentials`](auth/oauth-2-client-credentials-grant.md) | The Credentials Setter for OAuth 2 Client Credentials Grant |
| customerHeaderCredentials | [`CustomerHeaderCredentials`](auth/custom-header-signature-2.md) | The Credentials Setter for Custom Header Signature |

The API client can be initialized as follows:

```php
use LoyaltyApIsLib\Logging\LoggingConfigurationBuilder;
use LoyaltyApIsLib\Logging\RequestLoggingConfigurationBuilder;
use LoyaltyApIsLib\Logging\ResponseLoggingConfigurationBuilder;
use Psr\Log\LogLevel;
use LoyaltyApIsLib\Environment;
use LoyaltyApIsLib\Authentication\PublicBearerTokenCredentialsBuilder;
use LoyaltyApIsLib\Authentication\PublicBasicTokenCredentialsBuilder;
use LoyaltyApIsLib\Authentication\PrivateBasicTokenCredentialsBuilder;
use LoyaltyApIsLib\Authentication\ClientAuthorizationTokenCredentialsBuilder;
use LoyaltyApIsLib\Authentication\CustomerHeaderCredentialsBuilder;
use LoyaltyApIsLib\LoyaltyApIsClientBuilder;

$client = LoyaltyApIsClientBuilder::init()
    ->publicBearerTokenCredentials(
        PublicBearerTokenCredentialsBuilder::init(
            'AccessToken'
        )
    )
    ->publicBasicTokenCredentials(
        PublicBasicTokenCredentialsBuilder::init(
            'Public Basic Token'
        )
    )
    ->privateBasicTokenCredentials(
        PrivateBasicTokenCredentialsBuilder::init(
            'Public Basic Token'
        )
    )
    ->clientAuthorizationTokenCredentials(
        ClientAuthorizationTokenCredentialsBuilder::init(
            'OAuthClientId',
            'OAuthClientSecret'
        )
    )
    ->customerHeaderCredentials(
        CustomerHeaderCredentialsBuilder::init(
            'Authorization-Token'
        )
    )
    ->environment(Environment::SIT)
    ->loggingConfiguration(
        LoggingConfigurationBuilder::init()
            ->level(LogLevel::INFO)
            ->requestConfiguration(RequestLoggingConfigurationBuilder::init()->body(true))
            ->responseConfiguration(ResponseLoggingConfigurationBuilder::init()->headers(true))
    )
    ->build();
```

## Loyalty APIs Client

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

## Apis

| Name | Description |
|  --- | --- |
| getAuthorizationApi() | Gets AuthorizationApi |
| getProfileManagementApi() | Gets ProfileManagementApi |
| getOfferApi() | Gets OfferApi |
| getBalancesApi() | Gets BalancesApi |
| getRedemptionApi() | Gets RedemptionApi |
| getTransactionApi() | Gets TransactionApi |
| getOauthAuthorizationApi() | Gets OauthAuthorizationApi |

