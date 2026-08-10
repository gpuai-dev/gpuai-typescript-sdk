
# FineTuningJob

The fine-tuning job object. `status` is the COLLAPSED public enum (the rich internal states are hidden). `result_files` are freshly-presigned, short-lived download URLs regenerated per read. No backing-provider identity is present (D6).

## Properties

Name | Type
------------ | -------------
`id` | string
`object` | string
`model` | string
`createdAt` | number
`finishedAt` | number
`fineTunedModel` | string
`status` | string
`trainingFile` | string
`resultFiles` | Array&lt;string&gt;
`error` | [FineTuningJobError](FineTuningJobError.md)
`method` | [FineTuningJobMethod](FineTuningJobMethod.md)
`seed` | number
`suffix` | string
`metadata` | { [key: string]: any; }

## Example

```typescript
import type { FineTuningJob } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "object": null,
  "model": null,
  "createdAt": null,
  "finishedAt": null,
  "fineTunedModel": null,
  "status": null,
  "trainingFile": null,
  "resultFiles": null,
  "error": null,
  "method": null,
  "seed": null,
  "suffix": null,
  "metadata": null,
} satisfies FineTuningJob

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as FineTuningJob
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


