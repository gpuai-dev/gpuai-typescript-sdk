
# FineTuningJobList


## Properties

Name | Type
------------ | -------------
`object` | string
`data` | [Array&lt;FineTuningJob&gt;](FineTuningJob.md)
`hasMore` | boolean

## Example

```typescript
import type { FineTuningJobList } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "object": null,
  "data": null,
  "hasMore": null,
} satisfies FineTuningJobList

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as FineTuningJobList
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


