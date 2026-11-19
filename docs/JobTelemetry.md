
# JobTelemetry


## Properties

Name | Type
------------ | -------------
`peakMemoryMb` | number
`reservationMb` | number
`gpuMemoryTotalMb` | number
`points` | [Array&lt;JobTelemetryPoint&gt;](JobTelemetryPoint.md)

## Example

```typescript
import type { JobTelemetry } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "peakMemoryMb": null,
  "reservationMb": null,
  "gpuMemoryTotalMb": null,
  "points": null,
} satisfies JobTelemetry

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobTelemetry
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


