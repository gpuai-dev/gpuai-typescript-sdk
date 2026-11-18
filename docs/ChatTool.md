
# ChatTool


## Properties

Name | Type
------------ | -------------
`type` | string
`_function` | [ChatToolFunction](ChatToolFunction.md)

## Example

```typescript
import type { ChatTool } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "type": null,
  "_function": null,
} satisfies ChatTool

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ChatTool
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


