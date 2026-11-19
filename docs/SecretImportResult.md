
# SecretImportResult


## Properties

Name | Type
------------ | -------------
`created` | Array&lt;string&gt;
`updated` | Array&lt;string&gt;
`skipped` | Array&lt;string&gt;

## Example

```typescript
import type { SecretImportResult } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "created": null,
  "updated": null,
  "skipped": null,
} satisfies SecretImportResult

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as SecretImportResult
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


