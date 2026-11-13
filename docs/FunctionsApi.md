# FunctionsApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**activateFunctionVersion**](FunctionsApi.md#activatefunctionversion) | **POST** /functions/{id}/versions/{version_id}/activate | Confirm a version\&#39;s upload and make it current |
| [**cancelFunctionRun**](FunctionsApi.md#cancelfunctionrun) | **POST** /functions/{id}/runs/{run_id}/cancel | Cancel a run |
| [**createFunction**](FunctionsApi.md#createfunctionoperation) | **POST** /functions | Get or create a function by name |
| [**createFunctionRun**](FunctionsApi.md#createfunctionrunoperation) | **POST** /functions/{id}/runs | Call a function |
| [**createFunctionVersion**](FunctionsApi.md#createfunctionversionoperation) | **POST** /functions/{id}/versions | Register a version of a function |
| [**deleteFunction**](FunctionsApi.md#deletefunction) | **DELETE** /functions/{id} | Delete a function |
| [**getFunction**](FunctionsApi.md#getfunction) | **GET** /functions/{id} | Get a function |
| [**getFunctionRun**](FunctionsApi.md#getfunctionrun) | **GET** /functions/{id}/runs/{run_id} | Get a run |
| [**getFunctionRunLogs**](FunctionsApi.md#getfunctionrunlogs) | **GET** /functions/{id}/runs/{run_id}/logs | Read a run\&#39;s output |
| [**listFunctionRuns**](FunctionsApi.md#listfunctionruns) | **GET** /functions/{id}/runs | List a function\&#39;s runs |
| [**listFunctions**](FunctionsApi.md#listfunctions) | **GET** /functions | List functions |



## activateFunctionVersion

> FunctionVersion activateFunctionVersion(id, versionId, idempotencyKey)

Confirm a version\&#39;s upload and make it current

Reads the uploaded bundle back, checks it against the declared size and SHA-256 (422 on a mismatch or a missing upload), and makes the version the one the function\&#39;s next call runs. Safe to repeat. Requires the &#x60;functions:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { ActivateFunctionVersionRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
    // string | The version id.
    versionId: versionId_example,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies ActivateFunctionVersionRequest;

  try {
    const data = await api.activateFunctionVersion(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |
| **versionId** | `string` | The version id. | [Defaults to `undefined`] |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**FunctionVersion**](FunctionVersion.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The version is ready. |  -  |
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## cancelFunctionRun

> FunctionRun cancelFunctionRun(id, runId, idempotencyKey)

Cancel a run

A queued run is cancelled at once; a running one is stopped on its machine within seconds, and the machine stays ready for the next call. Cancelling a finished run changes nothing and returns it, so the request is safe to repeat. Requires the &#x60;functions:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { CancelFunctionRunRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
    // string | The run id.
    runId: runId_example,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CancelFunctionRunRequest;

  try {
    const data = await api.cancelFunctionRun(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |
| **runId** | `string` | The run id. | [Defaults to `undefined`] |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**FunctionRun**](FunctionRun.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The run after the request. |  -  |
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createFunction

> Function createFunction(createFunctionRequest, idempotencyKey)

Get or create a function by name

Returns the organization\&#39;s function with this name, creating it on first use (201) or returning the existing one (200). Creating a function starts no machine and costs nothing. Requires the &#x60;functions:write&#x60; scope. The key must belong to a user, because the function\&#39;s machines are launched as that user.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { CreateFunctionOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // CreateFunctionRequest
    createFunctionRequest: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CreateFunctionOperationRequest;

  try {
    const data = await api.createFunction(body);
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
| **createFunctionRequest** | [CreateFunctionRequest](CreateFunctionRequest.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**Function**](Function.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The function already existed. |  -  |
| **201** | Created. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createFunctionRun

> FunctionRun createFunctionRun(id, createFunctionRunRequest, idempotencyKey)

Call a function

Queues one call and returns at once (202). A warm machine takes it within moments; otherwise a machine is started for it, up to the function\&#39;s &#x60;max_concurrency&#x60;, beyond which calls wait in the queue. Read the run with &#x60;wait&#x60; for the outcome. Send an &#x60;Idempotency-Key&#x60; so a retried request does not run the function twice. Calling a function can start a billed machine: an organization with no balance is refused with 402, and the organization\&#39;s spending limits apply when the machine is requested. Requires the &#x60;functions:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { CreateFunctionRunOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
    // CreateFunctionRunRequest
    createFunctionRunRequest: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CreateFunctionRunOperationRequest;

  try {
    const data = await api.createFunctionRun(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |
| **createFunctionRunRequest** | [CreateFunctionRunRequest](CreateFunctionRunRequest.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**FunctionRun**](FunctionRun.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | The call is queued. |  -  |
| **402** | The organization has no balance. |  -  |
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createFunctionVersion

> FunctionVersion createFunctionVersion(id, createFunctionVersionRequest, idempotencyKey)

Register a version of a function

Declares one version of the function: the digest of its pickled code, its Python dependencies and its settings. Idempotent on &#x60;content_hash&#x60;: the same hash returns the existing version (200) instead of a new one (201). A version whose code is not uploaded yet carries an &#x60;upload&#x60; URL; PUT the bundle there, then activate the version. Requires the &#x60;functions:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { CreateFunctionVersionOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
    // CreateFunctionVersionRequest
    createFunctionVersionRequest: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CreateFunctionVersionOperationRequest;

  try {
    const data = await api.createFunctionVersion(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |
| **createFunctionVersionRequest** | [CreateFunctionVersionRequest](CreateFunctionVersionRequest.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**FunctionVersion**](FunctionVersion.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | A version with this content hash already existed. |  -  |
| **201** | Created. |  -  |
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteFunction

> deleteFunction(id)

Delete a function

The function stops taking calls, its queued calls are cancelled, a call that is executing is stopped, and its machines are released, which ends their billing. The name can be reused afterwards. Requires the &#x60;functions:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { DeleteFunctionRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
  } satisfies DeleteFunctionRequest;

  try {
    const data = await api.deleteFunction(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |

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
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getFunction

> Function getFunction(id)

Get a function

Requires the &#x60;functions:read&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { GetFunctionRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
  } satisfies GetFunctionRequest;

  try {
    const data = await api.getFunction(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |

### Return type

[**Function**](Function.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getFunctionRun

> FunctionRun getFunctionRun(id, runId, wait, includeResult)

Get a run

Returns one call. With &#x60;wait&#x60;, the request is held until the run finishes or the wait elapses, so a caller blocks on one request instead of polling. Requires the &#x60;functions:read&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { GetFunctionRunRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
    // string | The run id.
    runId: runId_example,
    // number | Seconds to hold the request while the run is not finished. (optional)
    wait: 56,
    // boolean | Include the pickled return value of a succeeded run. (optional)
    includeResult: true,
  } satisfies GetFunctionRunRequest;

  try {
    const data = await api.getFunctionRun(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |
| **runId** | `string` | The run id. | [Defaults to `undefined`] |
| **wait** | `number` | Seconds to hold the request while the run is not finished. | [Optional] [Defaults to `undefined`] |
| **includeResult** | `boolean` | Include the pickled return value of a succeeded run. | [Optional] [Defaults to `undefined`] |

### Return type

[**FunctionRun**](FunctionRun.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getFunctionRunLogs

> FunctionRunLogs getFunctionRunLogs(id, runId, after, limit, wait)

Read a run\&#39;s output

Returns the run\&#39;s stdout and stderr after &#x60;after&#x60;, oldest first. With &#x60;wait&#x60;, the request is held until there is new output or the run finishes, which is how a client follows a live run. Up to 4 MB of output is kept per run. Requires the &#x60;functions:read&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { GetFunctionRunLogsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
    // string | The run id.
    runId: runId_example,
    // number | Return chunks after this cursor. Omit to read from the start. (optional)
    after: 789,
    // number (optional)
    limit: 56,
    // number | Seconds to hold the request while there is nothing new. (optional)
    wait: 56,
  } satisfies GetFunctionRunLogsRequest;

  try {
    const data = await api.getFunctionRunLogs(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |
| **runId** | `string` | The run id. | [Defaults to `undefined`] |
| **after** | `number` | Return chunks after this cursor. Omit to read from the start. | [Optional] [Defaults to `undefined`] |
| **limit** | `number` |  | [Optional] [Defaults to `1000`] |
| **wait** | `number` | Seconds to hold the request while there is nothing new. | [Optional] [Defaults to `undefined`] |

### Return type

[**FunctionRunLogs**](FunctionRunLogs.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listFunctionRuns

> FunctionRunList listFunctionRuns(id, cursor, limit)

List a function\&#39;s runs

Newest first. Requires the &#x60;functions:read&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { ListFunctionRunsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  const body = {
    // string | The function id.
    id: id_example,
    // string (optional)
    cursor: cursor_example,
    // number (optional)
    limit: 56,
  } satisfies ListFunctionRunsRequest;

  try {
    const data = await api.listFunctionRuns(body);
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
| **id** | `string` | The function id. | [Defaults to `undefined`] |
| **cursor** | `string` |  | [Optional] [Defaults to `undefined`] |
| **limit** | `number` |  | [Optional] [Defaults to `50`] |

### Return type

[**FunctionRunList**](FunctionRunList.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | No such function, version or run in the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listFunctions

> FunctionList listFunctions()

List functions

Returns the organization\&#39;s functions, newest first, each with the settings of its current version, what its machines are doing and what it cost in the last 24 hours. Requires the &#x60;functions:read&#x60; scope.

### Example

```ts
import {
  Configuration,
  FunctionsApi,
} from '@gpuai/sdk';
import type { ListFunctionsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FunctionsApi(config);

  try {
    const data = await api.listFunctions();
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

[**FunctionList**](FunctionList.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

