
# CreateFunctionVersionRequest


## Properties

Name | Type
------------ | -------------
`contentHash` | string
`bundleSha256` | string
`bundleBytes` | number
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
`secrets` | Array&lt;string&gt;

## Example

```typescript
import type { CreateFunctionVersionRequest } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "contentHash": null,
  "bundleSha256": null,
  "bundleBytes": null,
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
  "secrets": null,
} satisfies CreateFunctionVersionRequest

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateFunctionVersionRequest
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


