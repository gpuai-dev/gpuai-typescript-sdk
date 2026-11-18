
# OfferingAlternative

A live catalog row a launch whose pinned offering was gone could take instead. Same fields and meaning as the matching GET /pricing row.

## Properties

Name | Type
------------ | -------------
`offeringId` | string
`gpuType` | string
`gpuCount` | number
`region` | string
`tier` | string
`pricePerHour` | number
`available` | number

## Example

```typescript
import type { OfferingAlternative } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "offeringId": null,
  "gpuType": null,
  "gpuCount": null,
  "region": null,
  "tier": null,
  "pricePerHour": null,
  "available": null,
} satisfies OfferingAlternative

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as OfferingAlternative
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


