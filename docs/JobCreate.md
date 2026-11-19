
# JobCreate


## Properties

Name | Type
------------ | -------------
`name` | string
`image` | string
`command` | Array&lt;string&gt;
`env` | { [key: string]: string; }
`gpuType` | string
`minVramGb` | number
`memoryHintMb` | number
`computeHintPct` | number
`timeoutSeconds` | number
`maxWaitSeconds` | number
`allowSharing` | boolean
`allowRestart` | boolean
`isolation` | string
`checkpointPath` | string
`maxRetries` | number
`maxPricePerHour` | number
`secrets` | Array&lt;string&gt;

## Example

```typescript
import type { JobCreate } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "name": null,
  "image": null,
  "command": null,
  "env": null,
  "gpuType": null,
  "minVramGb": null,
  "memoryHintMb": null,
  "computeHintPct": null,
  "timeoutSeconds": null,
  "maxWaitSeconds": null,
  "allowSharing": null,
  "allowRestart": null,
  "isolation": null,
  "checkpointPath": null,
  "maxRetries": null,
  "maxPricePerHour": null,
  "secrets": null,
} satisfies JobCreate

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobCreate
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


