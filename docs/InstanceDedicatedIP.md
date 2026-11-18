
# InstanceDedicatedIP

The instance\'s dedicated public IPv4 add-on. Present only on instances launched with `dedicated_ip`, and only on deployments where the add-on is enabled.

## Properties

Name | Type
------------ | -------------
`address` | string
`ports` | Array&lt;number&gt;
`status` | string
`suspendReason` | string
`hourlyFee` | number
`transferPricePerGb` | number
`transferGb` | number
`chargedUsd` | number

## Example

```typescript
import type { InstanceDedicatedIP } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "address": 203.0.113.7,
  "ports": [80, 443],
  "status": null,
  "suspendReason": null,
  "hourlyFee": null,
  "transferPricePerGb": null,
  "transferGb": null,
  "chargedUsd": null,
} satisfies InstanceDedicatedIP

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as InstanceDedicatedIP
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


