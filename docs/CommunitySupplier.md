
# CommunitySupplier

One organization\'s Community Cloud supplier profile (ONBD-01).

## Properties

Name | Type
------------ | -------------
`supplierId` | string
`orgId` | string
`status` | string
`createdAt` | Date
`updatedAt` | Date

## Example

```typescript
import type { CommunitySupplier } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "supplierId": null,
  "orgId": null,
  "status": null,
  "createdAt": null,
  "updatedAt": null,
} satisfies CommunitySupplier

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CommunitySupplier
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


