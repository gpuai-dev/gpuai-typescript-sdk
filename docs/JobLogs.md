
# JobLogs


## Properties

Name | Type
------------ | -------------
`data` | [Array&lt;JobLogChunk&gt;](JobLogChunk.md)
`nextAfter` | number

## Example

```typescript
import type { JobLogs } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "data": null,
  "nextAfter": null,
} satisfies JobLogs

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobLogs
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


