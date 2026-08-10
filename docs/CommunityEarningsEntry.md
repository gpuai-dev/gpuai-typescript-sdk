
# CommunityEarningsEntry


## Properties

Name | Type
------------ | -------------
`ledgerId` | string
`machineId` | string
`instanceId` | string
`amountCents` | number
`accruedAt` | Date
`paid` | boolean

## Example

```typescript
import type { CommunityEarningsEntry } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "ledgerId": null,
  "machineId": null,
  "instanceId": null,
  "amountCents": null,
  "accruedAt": null,
  "paid": null,
} satisfies CommunityEarningsEntry

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CommunityEarningsEntry
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


