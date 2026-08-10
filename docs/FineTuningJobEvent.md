
# FineTuningJobEvent


## Properties

Name | Type
------------ | -------------
`id` | string
`object` | string
`createdAt` | number
`level` | string
`message` | string
`type` | string
`data` | { [key: string]: any; }

## Example

```typescript
import type { FineTuningJobEvent } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "object": null,
  "createdAt": null,
  "level": null,
  "message": null,
  "type": null,
  "data": null,
} satisfies FineTuningJobEvent

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as FineTuningJobEvent
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


