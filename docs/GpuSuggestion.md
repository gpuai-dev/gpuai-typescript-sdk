
# GpuSuggestion

Whether a lower-priced GPU model would have fit an instance\'s observed peak GPU memory. It names GPU models and prices only. 

## Properties

Name | Type
------------ | -------------
`status` | string
`peakUsedMb` | number
`requiredMb` | number
`samples` | number
`observedMinutes` | number
`current` | [GpuSuggestionGpu](GpuSuggestionGpu.md)
`suggestion` | [GpuSuggestionCheaper](GpuSuggestionCheaper.md)

## Example

```typescript
import type { GpuSuggestion } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "status": null,
  "peakUsedMb": null,
  "requiredMb": null,
  "samples": null,
  "observedMinutes": null,
  "current": null,
  "suggestion": null,
} satisfies GpuSuggestion

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as GpuSuggestion
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


