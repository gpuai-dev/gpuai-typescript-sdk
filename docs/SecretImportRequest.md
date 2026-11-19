
# SecretImportRequest


## Properties

Name | Type
------------ | -------------
`secrets` | [Array&lt;SecretImportItem&gt;](SecretImportItem.md)
`overwrite` | boolean

## Example

```typescript
import type { SecretImportRequest } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "secrets": null,
  "overwrite": null,
} satisfies SecretImportRequest

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as SecretImportRequest
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


