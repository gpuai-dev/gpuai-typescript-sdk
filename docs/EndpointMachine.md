
# EndpointMachine


## Properties

Name | Type
------------ | -------------
`id` | string
`status` | string
`instanceId` | string
`gpuType` | string
`pricePerHour` | number
`readyAt` | Date
`terminatedAt` | Date
`terminateReason` | string
`createdAt` | Date

## Example

```typescript
import type { EndpointMachine } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "status": null,
  "instanceId": null,
  "gpuType": null,
  "pricePerHour": null,
  "readyAt": null,
  "terminatedAt": null,
  "terminateReason": null,
  "createdAt": null,
} satisfies EndpointMachine

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as EndpointMachine
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


