
# WatchRuleUpdate

Partial update. An absent key keeps the stored value; an explicit null on region, capacity_class or webhook_endpoint_override_id clears it. The merged rule is re-validated as a whole. 

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
import type { WatchRuleUpdate } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "gpuModel": null,
  "region": null,
  "capacityClass": null,
  "conditionKind": null,
  "threshold": null,
  "webhookEndpointOverrideId": null,
  "enabled": null,
} satisfies WatchRuleUpdate

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as WatchRuleUpdate
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


