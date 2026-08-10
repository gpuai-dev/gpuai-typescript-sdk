
# Template

A deployable application template. The container image (registry path) and start command are internal orchestration details and are intentionally absent from this schema (TMPL-13 defense-by-omission).

## Properties

Name | Type
------------ | -------------
`id` | string
`displayName` | string
`category` | string
`kind` | string
`status` | string
`containerDiskGb` | number
`minVramGb` | number
`minGpuCount` | number
`ports` | [Array&lt;TemplatePortsInner&gt;](TemplatePortsInner.md)
`env` | [Array&lt;TemplateEnvInner&gt;](TemplateEnvInner.md)
`docsUrl` | string
`description` | string
`includes` | Array&lt;string&gt;

## Example

```typescript
import type { Template } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": null,
  "displayName": null,
  "category": null,
  "kind": null,
  "status": null,
  "containerDiskGb": null,
  "minVramGb": null,
  "minGpuCount": null,
  "ports": null,
  "env": null,
  "docsUrl": null,
  "description": null,
  "includes": null,
} satisfies Template

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Template
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


