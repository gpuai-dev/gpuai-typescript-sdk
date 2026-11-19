
# Job

A batch job. It names no machine: the machines a job runs on are instances of your organization and appear in the instance list. 

## Properties

Name | Type
------------ | -------------
`id` | string
`name` | string
`image` | string
`command` | Array&lt;string&gt;
`envNames` | Array&lt;string&gt;
`secrets` | Array&lt;string&gt;
`gpuType` | string
`minVramGb` | number
`memoryHintMb` | number
`computeHintPct` | number
`timeoutSeconds` | number
`maxWaitSeconds` | number
`allowSharing` | boolean
`allowRestart` | boolean
`isolation` | string
`migProfile` | string
`checkpointPath` | string
`maxRetries` | number
`maxPricePerHour` | number
`status` | string
`statusReason` | string
`cancelRequested` | boolean
`attempt` | number
`retries` | number
`evictions` | number
`oomExits` | number
`reservationMb` | number
`wholeGpu` | boolean
`predictedMb` | number
`predictionSource` | string
`predictedComputePct` | number
`computePredictionSource` | string
`peakMemoryMb` | number
`gpuMemoryTotalMb` | number
`utilMeanPct` | number
`busyPct` | number
`memorySource` | string
`sharingMode` | string
`gpuSeconds` | number
`attributedCostUsd` | number
`exitCode` | number
`createdAt` | Date
`startedAt` | Date
`finishedAt` | Date
`sharingHint` | [JobSharingHint](JobSharingHint.md)
`attempts` | [Array&lt;JobAttempt&gt;](JobAttempt.md)

## Example

```typescript
import type { Job } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "name": null,
  "image": null,
  "command": null,
  "envNames": null,
  "secrets": null,
  "gpuType": null,
  "minVramGb": null,
  "memoryHintMb": null,
  "computeHintPct": null,
  "timeoutSeconds": null,
  "maxWaitSeconds": null,
  "allowSharing": null,
  "allowRestart": null,
  "isolation": null,
  "migProfile": null,
  "checkpointPath": null,
  "maxRetries": null,
  "maxPricePerHour": null,
  "status": null,
  "statusReason": null,
  "cancelRequested": null,
  "attempt": null,
  "retries": null,
  "evictions": null,
  "oomExits": null,
  "reservationMb": null,
  "wholeGpu": null,
  "predictedMb": null,
  "predictionSource": null,
  "predictedComputePct": null,
  "computePredictionSource": null,
  "peakMemoryMb": null,
  "gpuMemoryTotalMb": null,
  "utilMeanPct": null,
  "busyPct": null,
  "memorySource": null,
  "sharingMode": null,
  "gpuSeconds": null,
  "attributedCostUsd": null,
  "exitCode": null,
  "createdAt": null,
  "startedAt": null,
  "finishedAt": null,
  "sharingHint": null,
  "attempts": null,
} satisfies Job

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Job
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


