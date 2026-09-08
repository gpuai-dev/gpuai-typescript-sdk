
# MarketHistoryPoint

One bucket of a price/stock series.  The nullability of `price_per_gpu_hour` and `available_count` is the contract, not a convenience: a real 0 is a bucket we sampled and found sold out, and null is a bucket we never successfully sampled. A client that coerces null to 0 will report GPU.ai\'s own polling outages as supplier stockouts, and must not interpolate across a null. 

## Properties

Name | Type
------------ | -------------
`bucketTs` | Date
`pricePerGpuHour` | number
`availableCount` | number
`nodePricePerHour` | number
`gpuCount` | number

## Example

```typescript
import type { MarketHistoryPoint } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "bucketTs": null,
  "pricePerGpuHour": null,
  "availableCount": null,
  "nodePricePerHour": null,
  "gpuCount": null,
} satisfies MarketHistoryPoint

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as MarketHistoryPoint
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


