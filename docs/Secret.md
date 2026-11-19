
# Secret

An organization secret\'s metadata. There is no value field: values are write-only and never returned.

## Properties

Name | Type
------------ | -------------
`name` | string
`description` | string
`version` | number
`createdAt` | Date
`updatedAt` | Date
`lastUsedAt` | Date

## Example

```typescript
import type { Secret } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "name": HF_TOKEN,
  "description": null,
  "version": null,
  "createdAt": null,
  "updatedAt": null,
  "lastUsedAt": null,
} satisfies Secret

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Secret
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


