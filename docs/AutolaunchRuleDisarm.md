
# AutolaunchRuleDisarm

The entire PATCH surface. `enabled` must be present and must be false. Any other key is refused rather than accepted-and-ignored, because a PATCH carrying a new ceiling that returned 200 would leave the caller believing the cap had moved. 

## Properties

Name | Type
------------ | -------------
`enabled` | boolean

## Example

```typescript
import type { AutolaunchRuleDisarm } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "enabled": null,
} satisfies AutolaunchRuleDisarm

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as AutolaunchRuleDisarm
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


