
# FunctionReplicaCounts

How many machines a function has in each state.

## Properties

Name | Type
------------ | -------------
`starting` | number
`warm` | number
`running` | number

## Example

```typescript
import type { FunctionReplicaCounts } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "starting": null,
  "warm": null,
  "running": null,
} satisfies FunctionReplicaCounts

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as FunctionReplicaCounts
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


