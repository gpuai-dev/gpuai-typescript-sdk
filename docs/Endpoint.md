
# Endpoint


## Properties

Name | Type
------------ | -------------
`id` | string
`name` | string
`model` | string
`gpuType` | string
`status` | string
`url` | string
`minReplicas` | number
`maxReplicas` | number
`idleTimeout` | number
`targetConcurrency` | number
`maxPricePerHour` | number
`hfTokenSecret` | string
`replicas` | [EndpointReplicaCounts](EndpointReplicaCounts.md)
`requestCount` | number
`lastRequestAt` | Date
`lastError` | string
`createdAt` | Date
`machines` | [Array&lt;EndpointMachine&gt;](EndpointMachine.md)

## Example

```typescript
import type { Endpoint } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "name": null,
  "model": null,
  "gpuType": null,
  "status": null,
  "url": https://api.gpu.ai/v1/endpoints/3f1c2a7e-0000-4000-8000-000000000000/openai/v1,
  "minReplicas": null,
  "maxReplicas": null,
  "idleTimeout": null,
  "targetConcurrency": null,
  "maxPricePerHour": null,
  "hfTokenSecret": null,
  "replicas": null,
  "requestCount": null,
  "lastRequestAt": null,
  "lastError": null,
  "createdAt": null,
  "machines": null,
} satisfies Endpoint

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Endpoint
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


