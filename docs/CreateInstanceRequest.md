
# CreateInstanceRequest


## Properties

Name | Type
------------ | -------------
`gpuType` | string
`gpuCount` | number
`region` | string
`tier` | string
`sshKeyIds` | Array&lt;string&gt;
`name` | string
`maxPricePerHour` | number
`templateId` | string
`environment` | string
`offeringId` | string
`diskGb` | number
`env` | { [key: string]: string; }

## Example

```typescript
import type { CreateInstanceRequest } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "gpuType": null,
  "gpuCount": null,
  "region": null,
  "tier": null,
  "sshKeyIds": null,
  "name": null,
  "maxPricePerHour": null,
  "templateId": null,
  "environment": certified:pytorch@2.13,
  "offeringId": null,
  "diskGb": 200,
  "env": null,
} satisfies CreateInstanceRequest

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateInstanceRequest
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


