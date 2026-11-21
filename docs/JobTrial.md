
# JobTrial


## Properties

Name | Type
------------ | -------------
`enabled` | boolean
`eligible` | boolean
`reason` | string
`capCents` | number
`creditedCents` | number
`remainingCents` | number
`message` | string
`funding` | string
`maxPricePerHour` | number
`maxRuntimeSeconds` | number

## Example

```typescript
import type { JobTrial } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "enabled": null,
  "eligible": null,
  "reason": null,
  "capCents": null,
  "creditedCents": null,
  "remainingCents": null,
  "message": null,
  "funding": null,
  "maxPricePerHour": null,
  "maxRuntimeSeconds": null,
} satisfies JobTrial

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobTrial
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


