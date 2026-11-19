# SecretsApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createSecret**](SecretsApi.md#createsecret) | **POST** /secrets | Create a secret |
| [**deleteSecret**](SecretsApi.md#deletesecret) | **DELETE** /secrets/{name} | Delete a secret |
| [**getSecret**](SecretsApi.md#getsecret) | **GET** /secrets/{name} | Get a secret\&#39;s metadata |
| [**importSecrets**](SecretsApi.md#importsecrets) | **POST** /secrets/import | Import secrets |
| [**listSecrets**](SecretsApi.md#listsecrets) | **GET** /secrets | List secrets |
| [**putSecret**](SecretsApi.md#putsecret) | **PUT** /secrets/{name} | Create or replace a secret |



## createSecret

> Secret createSecret(secretCreate)

Create a secret

Stores a new secret. The value crosses the wire on create, update and import only, is envelope encrypted at rest, and is never returned. The name is the environment variable the value is delivered as: a letter or underscore, then letters, digits and underscores, 128 characters at most; names starting with GPUAI_ and names the machine itself needs (PATH, HOME, LD_PRELOAD and similar) are refused. Values are at most 32 KB. Returns 409 &#x60;name_taken&#x60; when the name exists (use PUT to replace a value) and 422 &#x60;validation_failed&#x60; for a bad name or value. Every create, update, delete and use is recorded in the organization\&#39;s audit log, without the value. Requires the &#x60;instances:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  SecretsApi,
} from '@gpuai/sdk';
import type { CreateSecretRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new SecretsApi(config);

  const body = {
    // SecretCreate
    secretCreate: ...,
  } satisfies CreateSecretRequest;

  try {
    const data = await api.createSecret(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **secretCreate** | [SecretCreate](SecretCreate.md) |  | |

### Return type

[**Secret**](Secret.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created (metadata only; no value). |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteSecret

> deleteSecret(name)

Delete a secret

Deletes the secret. Machines already running keep the value they were given; nothing started later can receive it, and a function version or job that still names it fails its next run. Requires the &#x60;instances:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  SecretsApi,
} from '@gpuai/sdk';
import type { DeleteSecretRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new SecretsApi(config);

  const body = {
    // string | The secret\'s name.
    name: name_example,
  } satisfies DeleteSecretRequest;

  try {
    const data = await api.deleteSecret(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **name** | `string` | The secret\&#39;s name. | [Defaults to `undefined`] |

### Return type

`void` (Empty response body)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Deleted. |  -  |
| **404** | Error response (RFC 7807) |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getSecret

> Secret getSecret(name)

Get a secret\&#39;s metadata

Returns one secret\&#39;s metadata. The value is never returned. Requires the &#x60;instances:read&#x60; scope. 404 &#x60;not_found&#x60; when the organization has no secret with this name.

### Example

```ts
import {
  Configuration,
  SecretsApi,
} from '@gpuai/sdk';
import type { GetSecretRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new SecretsApi(config);

  const body = {
    // string | The secret\'s name.
    name: name_example,
  } satisfies GetSecretRequest;

  try {
    const data = await api.getSecret(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **name** | `string` | The secret\&#39;s name. | [Defaults to `undefined`] |

### Return type

[**Secret**](Secret.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The secret (no value). |  -  |
| **404** | Error response (RFC 7807) |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## importSecrets

> SecretImportResult importSecrets(secretImportRequest)

Import secrets

Creates or updates many secrets at once, for example the output of &#x60;infisical export&#x60; or a .env file parsed by the client (the &#x60;gpu secrets import&#x60; command parses dotenv and Infisical JSON locally and sends this request). Every item is validated before any is written. With &#x60;overwrite&#x60; false, existing secrets are left untouched and listed under &#x60;skipped&#x60;. At most 200 items. Requires the &#x60;instances:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  SecretsApi,
} from '@gpuai/sdk';
import type { ImportSecretsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new SecretsApi(config);

  const body = {
    // SecretImportRequest
    secretImportRequest: ...,
  } satisfies ImportSecretsRequest;

  try {
    const data = await api.importSecrets(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **secretImportRequest** | [SecretImportRequest](SecretImportRequest.md) |  | |

### Return type

[**SecretImportResult**](SecretImportResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | What the import did, by name. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listSecrets

> SecretList listSecrets()

List secrets

Lists the organization\&#39;s secrets by name with their metadata. Values are never returned by any read. Requires the &#x60;instances:read&#x60; scope. Returns 503 &#x60;secrets_unavailable&#x60; when secrets are switched on but no encryption key is configured, and 404 when the feature is off.

### Example

```ts
import {
  Configuration,
  SecretsApi,
} from '@gpuai/sdk';
import type { ListSecretsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new SecretsApi(config);

  try {
    const data = await api.listSecrets();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**SecretList**](SecretList.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The organization\&#39;s secrets (no values). |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## putSecret

> Secret putSecret(name, secretPut)

Create or replace a secret

Sets the secret\&#39;s value, creating the secret when it does not exist (201) or replacing the value and bumping its version when it does (200). Omit &#x60;description&#x60; to keep the current one. Machines already running keep the value they were given; launches and calls from now on get the new one. Requires the &#x60;instances:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  SecretsApi,
} from '@gpuai/sdk';
import type { PutSecretRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new SecretsApi(config);

  const body = {
    // string | The secret\'s name.
    name: name_example,
    // SecretPut
    secretPut: ...,
  } satisfies PutSecretRequest;

  try {
    const data = await api.putSecret(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **name** | `string` | The secret\&#39;s name. | [Defaults to `undefined`] |
| **secretPut** | [SecretPut](SecretPut.md) |  | |

### Return type

[**Secret**](Secret.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Value replaced (metadata only). |  -  |
| **201** | Created (metadata only). |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

