
# AutolaunchRuleCreate


## Properties

Name | Type
------------ | -------------
`gpuModel` | string
`region` | string
`capacityClass` | string
`conditionKind` | string
`threshold` | number
`maxPricePerHour` | number
`maxRuntimeHours` | number
`spec` | { [key: string]: any; }
`acknowledgedMaxTotalUsd` | number

## Example

```typescript
import type { AutolaunchRuleCreate } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "gpuModel": null,
  "region": null,
  "capacityClass": null,
  "conditionKind": null,
  "threshold": null,
  "maxPricePerHour": null,
  "maxRuntimeHours": null,
  "spec": null,
  "acknowledgedMaxTotalUsd": null,
} satisfies AutolaunchRuleCreate

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as AutolaunchRuleCreate
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


