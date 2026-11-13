
# UpdateBillingDetailsRequest


## Properties

Name | Type
------------ | -------------
`legalName` | string
`addressLine1` | string
`addressLine2` | string
`city` | string
`region` | string
`postalCode` | string
`country` | string
`taxIdType` | string
`taxId` | string

## Example

```typescript
import type { UpdateBillingDetailsRequest } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "legalName": null,
  "addressLine1": null,
  "addressLine2": null,
  "city": null,
  "region": null,
  "postalCode": null,
  "country": null,
  "taxIdType": null,
  "taxId": null,
} satisfies UpdateBillingDetailsRequest

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as UpdateBillingDetailsRequest
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


