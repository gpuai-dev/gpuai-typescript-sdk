
# SupplierMachineView

The supplier-facing projection of a community machine. `occupied` replaces the renting customer\'s instance id (never exposed to the supplier); `online` is the server-derived 60s-heartbeat liveness.

## Properties

Name | Type
------------ | -------------
`machineId` | string
`gpuType` | string
`gpuCount` | number
`vramPerGpuGb` | number
`pricePerHour` | number
`region` | string
`tier` | string
`status` | string
`verificationStatus` | string
`online` | boolean
`lastHeartbeatAt` | Date
`firstHeartbeatAt` | Date
`occupied` | boolean
`reliabilityScore` | number
`delistReason` | string
`suspendReason` | string
`agentVersion` | string
`createdAt` | Date

## Example

```typescript
import type { SupplierMachineView } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "machineId": null,
  "gpuType": null,
  "gpuCount": null,
  "vramPerGpuGb": null,
  "pricePerHour": null,
  "region": null,
  "tier": null,
  "status": null,
  "verificationStatus": null,
  "online": null,
  "lastHeartbeatAt": null,
  "firstHeartbeatAt": null,
  "occupied": null,
  "reliabilityScore": null,
  "delistReason": null,
  "suspendReason": null,
  "agentVersion": null,
  "createdAt": null,
} satisfies SupplierMachineView

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as SupplierMachineView
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


