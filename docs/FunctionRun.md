
# FunctionRun

One call of a function.

## Properties

Name | Type
------------ | -------------
`id` | string
`functionId` | string
`versionId` | string
`status` | string
`cancelRequested` | boolean
`coldStart` | boolean
`instanceId` | string
`createdAt` | Date
`startedAt` | Date
`finishedAt` | Date
`durationMs` | number
`costUsd` | number
`pricePerHour` | number
`error` | [FunctionRunError](FunctionRunError.md)
`result` | string

## Example

```typescript
import type { FunctionRun } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "functionId": null,
  "versionId": null,
  "status": null,
  "cancelRequested": null,
  "coldStart": null,
  "instanceId": null,
  "createdAt": null,
  "startedAt": null,
  "finishedAt": null,
  "durationMs": null,
  "costUsd": null,
  "pricePerHour": null,
  "error": null,
  "result": null,
} satisfies FunctionRun

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as FunctionRun
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


