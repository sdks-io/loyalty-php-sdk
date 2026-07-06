
# Json Api Error Exception

*This model accepts additional fields of type array.*

## Structure

`JsonApiErrorException`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `jsonapi` | [`?JsonApiVersion`](../../doc/models/json-api-version.md) | Optional | - | getJsonapi(): ?JsonApiVersion | setJsonapi(?JsonApiVersion jsonapi): void |
| `errors` | [`?(ErrorItem[])`](../../doc/models/error-item.md) | Optional | - | getErrors(): ?array | setErrors(?array errors): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

