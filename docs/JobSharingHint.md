
# JobSharingHint

Advisory only, and present only when it applies. A job carries it when it succeeded with a whole GPU it did not allow to be shared, ran at least a minute with no out-of-memory exit or eviction, and its peak GPU memory, measured from per-process accounting (`memory_source` `process`), was at most half of the GPU\'s memory. Sharing stays opt-in; the hint never changes how a job is placed. 

## Properties

Name | Type
------------ | -------------
`message` | string
`peakMemoryMb` | number
`gpuMemoryTotalMb` | number

## Example

```typescript
import type { JobSharingHint } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "message": null,
  "peakMemoryMb": null,
  "gpuMemoryTotalMb": null,
} satisfies JobSharingHint

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobSharingHint
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


