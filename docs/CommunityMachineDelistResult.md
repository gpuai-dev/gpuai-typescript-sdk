
# CommunityMachineDelistResult

The terminal status a machine reached after a delist. `draining` means it was occupied and the existing rental keeps running (never killed); `delisted` means it was idle and left supply immediately.

## Properties

Name | Type
------------ | -------------
`machineId` | string
`status` | string

## Example

```typescript
import type { CommunityMachineDelistResult } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "machineId": null,
  "status": null,
} satisfies CommunityMachineDelistResult

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CommunityMachineDelistResult
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


