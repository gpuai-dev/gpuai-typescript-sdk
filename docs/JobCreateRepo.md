
# JobCreateRepo

A git repository cloned into `/workspace/repo`, the working directory of the command or script. Only where the deployment runs a default image. For a private repository, store a token as the organization secret `GIT_TOKEN` and name it in `secrets`. 

## Properties

Name | Type
------------ | -------------
`url` | string
`ref` | string

## Example

```typescript
import type { JobCreateRepo } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "url": null,
  "ref": null,
} satisfies JobCreateRepo

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as JobCreateRepo
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


