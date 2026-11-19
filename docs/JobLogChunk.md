
# JobLogChunk


## Properties

Name | Type
------------ | -------------
`id` | number
`attempt` | number
`text` | string
`createdAt` | Date

## Example

```typescript
import type { JobLogChunk } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "attempt": null,
  "text": null,
  "createdAt": null,
} satisfies JobLogChunk

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobLogChunk
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


