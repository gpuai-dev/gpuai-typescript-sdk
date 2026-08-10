
# OperationResult

Terminal-success payload. Carries the per-instance web-access credential — app_url for template deploys, terminal_url for instances provisioned with the browser web console, and the shared basic-auth login for both. The credential is also re-readable via connection.app_user/app_password on the org-scoped instance reads.

## Properties

Name | Type
------------ | -------------
`appUrl` | string
`terminalUrl` | string
`appBasicAuthUser` | string
`appBasicAuthPass` | string

## Example

```typescript
import type { OperationResult } from '@gpuai/sdk'

// TODO: Update the object below with actual values
const example = {
  "appUrl": null,
  "terminalUrl": null,
  "appBasicAuthUser": null,
  "appBasicAuthPass": null,
} satisfies OperationResult

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as OperationResult
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


