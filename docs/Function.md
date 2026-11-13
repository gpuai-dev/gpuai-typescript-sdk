
# Function

A Python function registered with GPU.ai. The settings are those of its current version and are null until the first version is uploaded.

## Properties

Name | Type
------------ | -------------
`id` | string
`name` | string
`status` | string
`currentVersionId` | string
`gpu` | string
`gpuCount` | number
`minVramGb` | number
`regions` | Array&lt;string&gt;
`maxPricePerHour` | number
`pythonVersion` | string
`pip` | Array&lt;string&gt;
`timeout` | number
`idleTimeout` | number
`maxConcurrency` | number
`replicas` | [FunctionReplicaCounts](FunctionReplicaCounts.md)
`runsQueued` | number
`runs24h` | number
`runCost24hUsd` | number
`machineCost24hUsd` | number
`lastRunAt` | Date
`createdAt` | Date

## Example

```typescript
import type { Function } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "name": null,
  "status": null,
  "currentVersionId": null,
  "gpu": null,
  "gpuCount": null,
  "minVramGb": null,
  "regions": null,
  "maxPricePerHour": null,
  "pythonVersion": null,
  "pip": null,
  "timeout": null,
  "idleTimeout": null,
  "maxConcurrency": null,
  "replicas": null,
  "runsQueued": null,
  "runs24h": null,
  "runCost24hUsd": null,
  "machineCost24hUsd": null,
  "lastRunAt": null,
  "createdAt": null,
} satisfies Function

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Function
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


