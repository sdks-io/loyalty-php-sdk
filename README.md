
# Getting Started with Loyalty APIs

## Introduction

Loyalty Account Management provides the end points needed in order to generate the user Authorization Tokens which will provide access to the Loyalty APIs and also to update the user profile.

## Install the Package

Run the following command to install the package and automatically add the dependency to your composer.json file:

```bash
composer require "shell/loyalty-sdk:0.0.3"
```

Or add it to the composer.json file manually as given below:

```json
"require": {
    "shell/loyalty-sdk": "0.0.3"
}
```

You can also view the package at:
https://packagist.org/packages/shell/loyalty-sdk#0.0.3

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/README.md#environments) | The API environment. <br> **Default: `Environment.SIT`** |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| publicBearerTokenCredentials | [`PublicBearerTokenCredentials`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/oauth-2-bearer-token.md) | The Credentials Setter for OAuth 2 Bearer token |
| publicBasicTokenCredentials | [`PublicBasicTokenCredentials`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |
| privateBasicTokenCredentials | [`PrivateBasicTokenCredentials`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/custom-header-signature-1.md) | The Credentials Setter for Custom Header Signature |
| clientAuthorizationTokenCredentials | [`ClientAuthorizationTokenCredentials`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/oauth-2-client-credentials-grant.md) | The Credentials Setter for OAuth 2 Client Credentials Grant |
| customerHeaderCredentials | [`CustomerHeaderCredentials`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/custom-header-signature-2.md) | The Credentials Setter for Custom Header Signature |

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

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| SIT | **Default** |
| PRODUCTION | - |
| UAT | - |

## Authorization

This API uses the following authentication schemes.

* [`PublicBearerToken (OAuth 2 Bearer token)`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/oauth-2-bearer-token.md)
* [`PublicBasicToken (Custom Header Signature)`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/custom-header-signature.md)
* [`PrivateBasicToken (Custom Header Signature)`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/custom-header-signature-1.md)
* [`client-authorization-token (OAuth 2 Client Credentials Grant)`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/oauth-2-client-credentials-grant.md)
* [`customerHeader (Custom Header Signature)`](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/auth/custom-header-signature-2.md)

## List of APIs

* [Profile Management](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/controllers/profile-management.md)
* [Authorization](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/controllers/authorization.md)
* [Offer](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/controllers/offer.md)
* [Balances](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/controllers/balances.md)
* [Redemption](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/controllers/redemption.md)
* [Transaction](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/controllers/transaction.md)

## SDK Infrastructure

### Configuration

* [ProxyConfigurationBuilder](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/proxy-configuration-builder.md)
* [LoggingConfigurationBuilder](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/logging-configuration-builder.md)
* [RequestLoggingConfigurationBuilder](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/request-logging-configuration-builder.md)
* [ResponseLoggingConfigurationBuilder](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/response-logging-configuration-builder.md)

### HTTP

* [HttpRequest](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/http-request.md)

### Utilities

* [ApiResponse](https://www.github.com/sdks-io/loyalty-php-sdk/tree/0.0.3/doc/api-response.md)

