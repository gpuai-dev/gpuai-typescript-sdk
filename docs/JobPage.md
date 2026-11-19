
# JobPage


## Properties

Name | Type
------------ | -------------
`data` | [Array&lt;Job&gt;](Job.md)
`nextCursor` | string

## Example

```typescript
import type { JobPage } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "data": null,
  "nextCursor": null,
} satisfies JobPage

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobPage
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


