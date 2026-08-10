
# FileObject

An uploaded file object. The storage location is an internal detail and is intentionally absent from this schema (privacy-by-omission, D6).

## Properties

Name | Type
------------ | -------------
`id` | string
`object` | string
`bytes` | number
`createdAt` | number
`filename` | string
`purpose` | string

## Example

```typescript
import type { FileObject } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "object": null,
  "bytes": null,
  "createdAt": null,
  "filename": null,
  "purpose": null,
} satisfies FileObject

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as FileObject
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


