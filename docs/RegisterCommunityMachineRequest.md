
# RegisterCommunityMachineRequest

All fields optional; an empty body registers a zero-spec placeholder in pending_verification.

## Properties

Name | Type
------------ | -------------
`gpuType` | string
`gpuCount` | number
`vramPerGpuGb` | number
`pricePerHour` | number
`region` | string
`tier` | string

## Example

```typescript
import type { RegisterCommunityMachineRequest } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "gpuType": null,
  "gpuCount": null,
  "vramPerGpuGb": null,
  "pricePerHour": null,
  "region": null,
  "tier": null,
} satisfies RegisterCommunityMachineRequest

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as RegisterCommunityMachineRequest
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


