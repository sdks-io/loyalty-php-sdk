
# Consumers Balances 422 Error Exception

*This model accepts additional fields of type array.*

## Structure

`ConsumersBalances422ErrorException`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `errorCode` | `int` | Required | - | getErrorCode(): int | setErrorCode(int errorCode): void |
| `message` | `string` | Required | - | getMessage(): string | setMessage(string message): void |
| `error` | `array` | Required | - | getError(): array | setError(array error): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

