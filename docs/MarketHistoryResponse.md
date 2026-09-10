
# MarketHistoryResponse

A price/stock series for one (gpu_model, region, capacity_class) key.  Points cover the FULL bucket grid across the requested window, including the buckets we did not sample — a gap therefore has visible width rather than disappearing between two adjacent points. 

## Properties

Name | Type
------------ | -------------
`gpuModel` | string
`region` | string
`capacityClass` | string
`clusterSize` | number
`availableClusterSizes` | Array&lt;number&gt;
`bucketSeconds` | number
`points` | [Array&lt;MarketHistoryPoint&gt;](MarketHistoryPoint.md)

## Example

```typescript
import type { MarketHistoryResponse } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "gpuModel": null,
  "region": null,
  "capacityClass": null,
  "clusterSize": null,
  "availableClusterSizes": null,
  "bucketSeconds": null,
  "points": null,
} satisfies MarketHistoryResponse

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as MarketHistoryResponse
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


