
# CommunityMachine

A self-declared Community Cloud machine. Spec fields are optional and unverified until Phase 57. The enrollment token hash is never serialized.

## Properties

Name | Type
------------ | -------------
`machineId` | string
`supplierId` | string
`gpuType` | string
`gpuCount` | number
`vramPerGpuGb` | number
`pricePerHour` | number
`region` | string
`tier` | string
`status` | string
`verificationStatus` | string
`lastHeartbeatAt` | Date
`createdAt` | Date

## Example

```typescript
import type { CommunityMachine } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "machineId": null,
  "supplierId": null,
  "gpuType": null,
  "gpuCount": null,
  "vramPerGpuGb": null,
  "pricePerHour": null,
  "region": null,
  "tier": null,
  "status": null,
  "verificationStatus": null,
  "lastHeartbeatAt": null,
  "createdAt": null,
} satisfies CommunityMachine

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CommunityMachine
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


