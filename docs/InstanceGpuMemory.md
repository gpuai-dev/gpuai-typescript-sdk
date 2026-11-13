
# InstanceGpuMemory

The highest GPU memory use seen on an instance since launch, from the telemetry every instance reports about every two minutes. On an instance with several GPUs it is the busiest GPU. Absent on an instance until its first sample arrives. 

## Properties

Name | Type
------------ | -------------
`peakUsedMb` | number
`totalMb` | number
`samples` | number
`lastSampleAt` | Date

## Example

```typescript
import type { InstanceGpuMemory } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "peakUsedMb": null,
  "totalMb": null,
  "samples": null,
  "lastSampleAt": null,
} satisfies InstanceGpuMemory

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as InstanceGpuMemory
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


