
# WatchRule

A rule that notifies when the market moves on a GPU model. It carries no upstream supplier identity of any kind, and no delivery address — those are properties of the resource, not of a particular response. 

## Properties

Name | Type
------------ | -------------
`id` | string
`gpuModel` | string
`region` | string
`capacityClass` | string
`conditionKind` | string
`threshold` | number
`state` | string
`lastFiredAt` | Date
`quietUntil` | Date
`webhookEndpointOverrideId` | string
`enabled` | boolean
`deactivatedReason` | string
`createdAt` | Date
`updatedAt` | Date

## Example

```typescript
import type { WatchRule } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "gpuModel": null,
  "region": null,
  "capacityClass": null,
  "conditionKind": null,
  "threshold": null,
  "state": null,
  "lastFiredAt": null,
  "quietUntil": null,
  "webhookEndpointOverrideId": null,
  "enabled": null,
  "deactivatedReason": null,
  "createdAt": null,
  "updatedAt": null,
} satisfies WatchRule

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as WatchRule
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


