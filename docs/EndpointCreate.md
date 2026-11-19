
# EndpointCreate


## Properties

Name | Type
------------ | -------------
`name` | string
`model` | string
`gpuType` | string
`minReplicas` | number
`maxReplicas` | number
`idleTimeout` | number
`targetConcurrency` | number
`maxPricePerHour` | number
`hfTokenSecret` | string

## Example

```typescript
import type { EndpointCreate } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "name": qwen-small,
  "model": Qwen/Qwen2.5-0.5B-Instruct,
  "gpuType": rtx_4090,
  "minReplicas": null,
  "maxReplicas": null,
  "idleTimeout": null,
  "targetConcurrency": null,
  "maxPricePerHour": null,
  "hfTokenSecret": null,
} satisfies EndpointCreate

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as EndpointCreate
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


