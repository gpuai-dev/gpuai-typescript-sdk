
# JobTelemetryPoint


## Properties

Name | Type
------------ | -------------
`ts` | Date
`attempt` | number
`memoryMb` | number
`gpuMemoryMb` | number
`gpuUtilPct` | number

## Example

```typescript
import type { JobTelemetryPoint } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "ts": null,
  "attempt": null,
  "memoryMb": null,
  "gpuMemoryMb": null,
  "gpuUtilPct": null,
} satisfies JobTelemetryPoint

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobTelemetryPoint
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


