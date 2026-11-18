
# ChatResponseFormat

Structured outputs. {\"type\":\"json_object\"} (JSON mode) or {\"type\":\"json_schema\",\"json_schema\":{...}}; \"text\" is the default. Only models whose /v1/models entry has supports_structured_outputs: true accept json_object / json_schema.

## Properties

Name | Type
------------ | -------------
`type` | string
`jsonSchema` | [ChatJSONSchemaFormat](ChatJSONSchemaFormat.md)

## Example

```typescript
import type { ChatResponseFormat } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "type": null,
  "jsonSchema": null,
} satisfies ChatResponseFormat

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ChatResponseFormat
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


