
# JobAttempt

One run of a job.

## Properties

Name | Type
------------ | -------------
`attempt` | number
`reservationMb` | number
`wholeGpu` | boolean
`predictionSource` | string
`outcome` | string
`reason` | string
`exitCode` | number
`peakMemoryMb` | number
`predictedComputePct` | number
`utilMeanPct` | number
`busyPct` | number
`computeSource` | string
`memorySource` | string
`sharingMode` | string
`migProfile` | string
`resumed` | boolean
`startedAt` | Date
`endedAt` | Date

## Example

```typescript
import type { JobAttempt } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "attempt": null,
  "reservationMb": null,
  "wholeGpu": null,
  "predictionSource": null,
  "outcome": null,
  "reason": null,
  "exitCode": null,
  "peakMemoryMb": null,
  "predictedComputePct": null,
  "utilMeanPct": null,
  "busyPct": null,
  "computeSource": null,
  "memorySource": null,
  "sharingMode": null,
  "migProfile": null,
  "resumed": null,
  "startedAt": null,
  "endedAt": null,
} satisfies JobAttempt

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobAttempt
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


