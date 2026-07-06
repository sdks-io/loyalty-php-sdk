# Transaction

```php
$transactionApi = $client->getTransactionApi();
```

## Class Name

`TransactionApi`


# Get Transactions L

This API is used to fetch and retrieve the list of transactions of a customer.

Example cURL request:

curl --location 'https://api-test.shell.com/loyalty/v1/consumers/transactionsL?language_code=pl-PL' \
--header 'country-code: PL' \
--header 'user-authorization-token: Bearer clk6qsn0z000o1rpactbsyu93' \
--header 'client-authorization-token: Bearer fmVQg8M2F2NGeI3RE18G8R8luKTk' \
--header 'language: en' \
--header 'application: PARTNER' \
--header 'channel: PARTNER' \
--header 'consumerUUID: bd68f27f-80f7-440a-b096-f65155161345'

```php
function getTransactionsL(
    string $countryCode,
    string $consumerUuid,
    string $userAuthorizationToken,
    string $application,
    string $languageCode,
    ?string $language = 'en',
    ?array $channel = PARTNER,
    ?int $page = null,
    ?int $limit = null,
    ?int $offset = null,
    ?int $pageSize = null,
    ?string $transactionType = null,
    ?string $fromDateTime = null,
    ?string $toDateTime = null,
    ?bool $filterByPartnerCode = null
): ApiResponse
```

## Authentication

This endpoint requires [client-authorization-token](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `countryCode` | `string` | Header, Required | This represents the ISO 3166-1 standard Alpha-2 code of the Country, which is the first two characters of the country code. |
| `consumerUuid` | `string` | Header, Required | This is the consumer's or customer's unique SSO UUID. |
| `userAuthorizationToken` | `string` | Header, Required | This is the consumer's SSO access, which you retrieved from */auth/exchangeAccessCode* endpoint prefixed by Bearer. |
| `application` | `string` | Header, Required | This is the calling application. |
| `languageCode` | `string` | Query, Required | This is a concatenation of language in lower case as per ISO 639-1 , “-” and country code as per ISO 3166-1 alpha-2. For example: en-GB. |
| `language` | `?string` | Header, Optional | This is the language in ISO 639-1 2 letter code format.<br><br>**Default**: `'en'` |
| `channel` | `?array` | Header, Optional | Channel.<br><br>**Default**: `PARTNER` |
| `page` | `?int` | Query, Optional | The page number, which needs to be retrieved. |
| `limit` | `?int` | Query, Optional | The maximum number of resources to be sent across all pages. |
| `offset` | `?int` | Query, Optional | This is used to skip a certain number of resources at the start of each page. |
| `pageSize` | `?int` | Query, Optional | This is the maximum number of resources to be sent in each page of the response. |
| `transactionType` | [`?string(TransactionTypeFilter)`](../../doc/models/transaction-type-filter.md) | Query, Optional | This is the type of the transaction. If the parameter is empty, it means that “ALL” queries. |
| `fromDateTime` | `?string` | Query, Optional | This is the datetime from which the transaction details are required. |
| `toDateTime` | `?string` | Query, Optional | This is the datetime until which the transaction details are required. |
| `filterByPartnerCode` | `?bool` | Query, Optional | This is used to filter the transactions based on partnerCode. If true, return the transactions related to partnerCode. If false, return all transactions. |

## Response Type

**200**: Returns the list of transactions.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TransactionsResponse`](../../doc/models/transactions-response.md).

## Example Usage

```php
$countryCode = 'GB';

$consumerUuid = '14ab7978-38c6-476c-be2d-7512287067fb';

$userAuthorizationToken = 'Bearer asdfhalsdfheywuiryafhk';

$application = 'PARTNER';

$languageCode = 'language_code8';

$language = 'en';

$channel = ApiHelper::deserialize('"PARTNER"');

$page = 2;

$limit = 10;

$offset = 5;

$pageSize = 20;

$transactionType = TransactionTypeFilter::EARN;

$fromDateTime = '01/07/2022 00:00:00';

$toDateTime = '01/20/2022 23:59:59';

$filterByPartnerCode = true;

$transactionApi = $client->getTransactionApi();
$apiResponse = $transactionApi->getTransactionsL(
    $countryCode,
    $consumerUuid,
    $userAuthorizationToken,
    $application,
    $languageCode,
    $language,
    $channel,
    $page,
    $limit,
    $offset,
    $pageSize,
    $transactionType,
    $fromDateTime,
    $toDateTime,
    $filterByPartnerCode
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TransactionsResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "totalResults": 0,
  "nextPage": ".../nextpage",
  "previousPage": ".../previouspage",
  "totalSaved": 0,
  "transactions": [
    {
      "transactionDateTime": 0,
      "transactionDateTimeStamp": "2022-01-21T12:35:15Z",
      "siteData": {
        "countryCode": "GB",
        "siteId": "23St34",
        "name": "Shell Liphook North",
        "postcode": "GU30 7TT",
        "city": "Liphook",
        "address": "A3 T North"
      },
      "loyalty": {
        "loyaltyCard": "1234567890123456789"
      },
      "transactionId": "8435166weew2332w",
      "partnerCode": "GB10CMLP_RAC",
      "partnerName": "RAC",
      "partnerLogo": "https://www.shell.co.uk/1234.jpg",
      "referenceId": "abcde12345xyz",
      "totalAmount": 0,
      "totalDiscountAmount": 0,
      "totalDiscountedFullAmount": 0,
      "totalVatAmount": 0,
      "balances": [
        {
          "currencyType": "AIRMILES",
          "amounts": [
            {
              "amount": 0,
              "state": "AVAILABLE"
            }
          ]
        }
      ],
      "currencyCode": "GBP",
      "saleItems": [
        {
          "description": "Not in use",
          "amount": 0,
          "detailType": "REDEMPTION",
          "discountAmount": 0,
          "offerInfos": [
            {
              "discountValue": 0,
              "loyaltyOfferAmount": 0,
              "loyaltyOfferCode": "string",
              "loyaltyOfferDescription": "string",
              "loyaltyOfferID": "1234567890123",
              "loyaltyOfferType": "string",
              "loyaltySchemeCode": "string",
              "reason": "10% Off on fuel"
            }
          ],
          "offerLang": {
            "id": "31AS2434",
            "title": "10% OFF of Ferrari Umbrella",
            "description": "Description of 10% OFF of Ferrari Umbrella",
            "customText": "Custom text"
          },
          "originalAmount": 0,
          "originalNetAmount": 0,
          "productData": {
            "id": "31AS2434",
            "name": "Ferrari Umbrella",
            "productType": "PARTNER",
            "productCode": "string",
            "productDescription": "string",
            "additionalProductDescription": "King Guest Room"
          },
          "quantity": 0,
          "vatAmount": 0,
          "vatRate": 0,
          "voucherItems": [
            {
              "code": "test123",
              "expiryDate": 0,
              "expiryDateTimestamp": "2022-01-30T12:35:15Z"
            }
          ],
          "vouchers": [
            "string"
          ],
          "unitPrice": 0,
          "unitMeasure": "LITRE",
          "EV": {
            "chargePointSerialId": "string",
            "chargePointConnectorTypeCd": "string",
            "chargePointConnectorTypeDesc": "string",
            "startDateTime": "2022-08-24T12:35:15Z",
            "endDateTime": "2022-08-24T12:54:15Z",
            "duration": 0
          },
          "points": 50
        }
      ],
      "redeemedItems": [
        {
          "description": "string",
          "amount": 0,
          "detailType": "REDEMPTION",
          "discountAmount": 0,
          "offerInfos": [
            {
              "discountValue": 0,
              "loyaltyOfferAmount": 0,
              "loyaltyOfferCode": "string",
              "loyaltyOfferDescription": "string",
              "loyaltyOfferID": "1234567890123",
              "loyaltyOfferType": "string",
              "loyaltySchemeCode": "string",
              "reason": "10% Off on fuel"
            }
          ],
          "offerLang": {
            "id": "31AS2434",
            "title": "10% OFF of Ferrari Umbrella",
            "description": "Description of 10% OFF of Ferrari Umbrella",
            "customText": "Custom text"
          },
          "originalAmount": 0,
          "productData": {
            "id": "31AS2434",
            "name": "Ferrari Umbrella",
            "productType": "PARTNER",
            "reasonForRedemption": "Burgers",
            "productCode": "string",
            "productDescription": "string"
          },
          "quantity": 0,
          "vatAmount": 0,
          "vatRate": 0,
          "points": 0,
          "vouchers": [
            "string"
          ],
          "voucherItems": [
            {
              "code": "test123",
              "expiryDate": 0,
              "expiryDateTimestamp": "2022-01-30T12:35:15Z"
            }
          ]
        }
      ],
      "transactionVouchers": [
        {
          "detailType": "REDEMPTION",
          "code": "5000000100071",
          "name": "Ferrari Umbrella",
          "amount": 0,
          "quantity": 0
        }
      ],
      "receiptNumber": "18a6sdf8a63448612",
      "pointsToCash": {
        "pointsRedeemed": 0,
        "totalAmount": 0,
        "pointsToCashMOP": true
      },
      "companyId": 0,
      "isPartnerRedemption": true,
      "currencyData": {
        "code": "USD",
        "symbol": "$",
        "isSuffix": true,
        "hasSpace": true
      }
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request - The request was not valid. This code is returned when the server has attempted to process the request, but some aspect of the request is not valid, for example an incorrectly formatted resource or an attempt to deploy an invalid event project to the event runtime. Information about the request is provided in the response body and includes an error code and error message. | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |
| 401 | Unauthorized request, Missing Authorization header, or expired authorization token etc. It is returned from the application server<br>when application security is enabled, and authorization information was missing from the request. | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |
| 404 | Not Found. | [`ResourceNotFoundErrorException`](../../doc/models/resource-not-found-error-exception.md) |
| 422 | 'Unprocessable Entity (WebDAV). If you are receiving an HTTP 422 - Unprocessable Entity error, there are several possibilities for why it might be occurring: <br><br> -You are sending in a payload that is not valid JSON <br><br> -You are sending HTTP headers, such as Content-Type or Accept, which specify a value other than application/json <br><br> -The request may be valid JSON, but there is something wrong with the content. | `ApiException` |
| 429 | Rate limit hit. See Retry-After header for a minimum amount of delay, but note that there is no guarantee<br>that subsequent request won't be limited. | `ApiException` |
| 500 | Internal server error. | `ApiException` |

