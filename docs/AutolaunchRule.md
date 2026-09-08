
# AutolaunchRule

A standing, pre-approved purchase order. It carries no upstream supplier identity, no org id, and no identifier of the API key that consented — the consenting principal is recorded in storage for the fire-time re-check, and a credential identifier has no business in a rule listing. 

## Properties

Name | Type
------------ | -------------
`id` | string
`gpuModel` | string
`region` | string
`capacityClass` | string
`conditionKind` | string
`threshold` | number
`maxPricePerHour` | number
`maxRuntimeHours` | number
`maxTotalUsd` | number
`spec` | { [key: string]: any; }
`state` | string
`attemptsThisEdge` | number
`lastFailureReason` | string
`launchedInstanceId` | string
`createdBySurface` | string
`enabled` | boolean
`createdAt` | Date
`updatedAt` | Date

## Example

```typescript
import type { AutolaunchRule } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "gpuModel": null,
  "region": null,
  "capacityClass": null,
  "conditionKind": null,
  "threshold": null,
  "maxPricePerHour": null,
  "maxRuntimeHours": null,
  "maxTotalUsd": null,
  "spec": null,
  "state": null,
  "attemptsThisEdge": null,
  "lastFailureReason": null,
  "launchedInstanceId": null,
  "createdBySurface": null,
  "enabled": null,
  "createdAt": null,
  "updatedAt": null,
} satisfies AutolaunchRule

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as AutolaunchRule
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


