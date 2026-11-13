
# InvoiceList


## Properties

Name | Type
------------ | -------------
`invoices` | [Array&lt;Invoice&gt;](Invoice.md)
`hasMore` | boolean
`nextCursor` | string

## Example

```typescript
import type { InvoiceList } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "invoices": null,
  "hasMore": null,
  "nextCursor": null,
} satisfies InvoiceList

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as InvoiceList
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


