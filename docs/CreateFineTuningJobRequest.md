
# CreateFineTuningJobRequest

Request body for POST /fine_tuning/jobs. The `method` object carries the Axolotl LoRA/QLoRA hyperparameters; `gpuai` is a native extension for the optional budget cap and GPU preference. The backing training environment (image, GPU provider) is an internal orchestration detail and is intentionally absent from this schema (privacy-by-omission, D6).

## Properties

Name | Type
------------ | -------------
`model` | string
`trainingFile` | string
`suffix` | string
`seed` | number
`method` | [CreateFineTuningJobRequestMethod](CreateFineTuningJobRequestMethod.md)
`gpuai` | [CreateFineTuningJobRequestGpuai](CreateFineTuningJobRequestGpuai.md)

## Example

```typescript
import type { CreateFineTuningJobRequest } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "model": null,
  "trainingFile": null,
  "suffix": null,
  "seed": null,
  "method": null,
  "gpuai": null,
} satisfies CreateFineTuningJobRequest

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateFineTuningJobRequest
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


