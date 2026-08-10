
# TemplateEnvInner


## Properties

Name | Type
------------ | -------------
`key` | string
`_default` | string
`userOverridable` | boolean
`secret` | boolean

## Example

```typescript
import type { TemplateEnvInner } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "key": null,
  "_default": null,
  "userOverridable": null,
  "secret": null,
} satisfies TemplateEnvInner

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as TemplateEnvInner
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


