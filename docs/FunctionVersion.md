
# FunctionVersion


## Properties

Name | Type
------------ | -------------
`id` | string
`functionId` | string
`status` | string
`contentHash` | string
`upload` | [FunctionUpload](FunctionUpload.md)
`pythonVersion` | string
`cloudpickleVersion` | string
`pip` | Array&lt;string&gt;
`gpu` | string
`gpuCount` | number
`minVramGb` | number
`regions` | Array&lt;string&gt;
`maxPricePerHour` | number
`timeout` | number
`idleTimeout` | number
`maxConcurrency` | number
`createdAt` | Date

## Example

```typescript
import type { FunctionVersion } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "functionId": null,
  "status": null,
  "contentHash": null,
  "upload": null,
  "pythonVersion": null,
  "cloudpickleVersion": null,
  "pip": null,
  "gpu": null,
  "gpuCount": null,
  "minVramGb": null,
  "regions": null,
  "maxPricePerHour": null,
  "timeout": null,
  "idleTimeout": null,
  "maxConcurrency": null,
  "createdAt": null,
} satisfies FunctionVersion

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as FunctionVersion
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


