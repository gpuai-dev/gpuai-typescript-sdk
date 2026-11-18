
# DedicatedIPRequest

Requests a dedicated public IPv4 address for the instance. Send an empty object for the default ports (80 and 443).

## Properties

Name | Type
------------ | -------------
`ports` | Array&lt;number&gt;

## Example

```typescript
import type { DedicatedIPRequest } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "ports": [80, 443],
} satisfies DedicatedIPRequest

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as DedicatedIPRequest
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


