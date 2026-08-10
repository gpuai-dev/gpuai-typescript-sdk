
# CreateFineTuningJobRequestGpuai


## Properties

Name | Type
------------ | -------------
`maxBudgetUsd` | number
`gpuPreference` | string

## Example

```typescript
import type { CreateFineTuningJobRequestGpuai } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "maxBudgetUsd": null,
  "gpuPreference": null,
} satisfies CreateFineTuningJobRequestGpuai

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateFineTuningJobRequestGpuai
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


