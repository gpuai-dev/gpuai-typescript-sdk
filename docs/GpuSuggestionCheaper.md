
# GpuSuggestionCheaper

The suggested GPU model and what it would save.

## Properties

Name | Type
------------ | -------------
`gpuType` | string
`gpuName` | string
`vramGb` | number
`pricePerHour` | number
`savingPerHour` | number
`savingPct` | number

## Example

```typescript
import type { GpuSuggestionCheaper } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "gpuType": null,
  "gpuName": null,
  "vramGb": null,
  "pricePerHour": null,
  "savingPerHour": null,
  "savingPct": null,
} satisfies GpuSuggestionCheaper

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as GpuSuggestionCheaper
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


