
# CommunityMachineRegistration


## Properties

Name | Type
------------ | -------------
`machine` | [CommunityMachine](CommunityMachine.md)
`enrollmentToken` | string

## Example

```typescript
import type { CommunityMachineRegistration } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "machine": null,
  "enrollmentToken": null,
} satisfies CommunityMachineRegistration

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CommunityMachineRegistration
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


