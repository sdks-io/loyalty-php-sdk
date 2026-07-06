
# Error Response Exception

*This model accepts additional fields of type array.*

## Structure

`ErrorResponseException`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `errorCode` | `float` | Required | HTTP error code | getErrorCode(): float | setErrorCode(float errorCode): void |
| `message` | `string` | Required | HTTP error status message | getMessage(): string | setMessage(string message): void |
| `error` | [`ErrorInfo`](../../doc/models/error-info.md) | Required | - | getError(): ErrorInfo | setError(ErrorInfo error): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

