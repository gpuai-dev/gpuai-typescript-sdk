
# DedicatedIPOffer


## Properties

Name | Type
------------ | -------------
`enabled` | boolean
`allowedPorts` | string
`defaultPorts` | Array&lt;number&gt;
`maxPorts` | number
`hourlyFee` | number
`transferPricePerGb` | number
`transferIncludedGb` | number
`transferCapGb` | number
`orgLimit` | number
`orgInUse` | number
`available` | number
`acceptableUse` | string

## Example

```typescript
import type { DedicatedIPOffer } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "enabled": null,
  "allowedPorts": 80,443,
  "defaultPorts": [80, 443],
  "maxPorts": 8,
  "hourlyFee": 0.01,
  "transferPricePerGb": 0.12,
  "transferIncludedGb": 0,
  "transferCapGb": 500,
  "orgLimit": 2,
  "orgInUse": null,
  "available": null,
  "acceptableUse": null,
} satisfies DedicatedIPOffer

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as DedicatedIPOffer
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


