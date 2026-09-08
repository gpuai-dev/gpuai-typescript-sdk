
# WatchRuleCreate


## Properties

Name | Type
------------ | -------------
`gpuModel` | string
`region` | string
`capacityClass` | string
`conditionKind` | string
`threshold` | number
`webhookEndpointOverrideId` | string
`enabled` | boolean

## Example

```typescript
import type { WatchRuleCreate } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "gpuModel": null,
  "region": null,
  "capacityClass": null,
  "conditionKind": null,
  "threshold": null,
  "webhookEndpointOverrideId": null,
  "enabled": null,
} satisfies WatchRuleCreate

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as WatchRuleCreate
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


