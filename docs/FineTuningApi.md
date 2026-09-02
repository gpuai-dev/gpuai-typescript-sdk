# FineTuningApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**cancelFineTuningJob**](FineTuningApi.md#cancelfinetuningjob) | **POST** /fine_tuning/jobs/{id}/cancel | Cancel a fine-tuning job (OpenAI-compatible) |
| [**createFile**](FineTuningApi.md#createfile) | **POST** /files | Upload a fine-tuning dataset file (OpenAI-compatible) |
| [**createFineTuningJob**](FineTuningApi.md#createfinetuningjoboperation) | **POST** /fine_tuning/jobs | Create a managed fine-tuning job (OpenAI-compatible) |
| [**getFineTuningJob**](FineTuningApi.md#getfinetuningjob) | **GET** /fine_tuning/jobs/{id} | Retrieve a fine-tuning job (OpenAI-compatible) |
| [**listFineTuningJobEvents**](FineTuningApi.md#listfinetuningjobevents) | **GET** /fine_tuning/jobs/{id}/events | List fine-tuning job events (OpenAI-compatible) |
| [**listFineTuningJobs**](FineTuningApi.md#listfinetuningjobs) | **GET** /fine_tuning/jobs | List fine-tuning jobs (OpenAI-compatible) |
| [**retrieveFile**](FineTuningApi.md#retrievefile) | **GET** /files/{id} | Retrieve a file (OpenAI-compatible) |



## cancelFineTuningJob

> FineTuningJob cancelFineTuningJob(id)

Cancel a fine-tuning job (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  FineTuningApi,
} from '@gpuai/sdk';
import type { CancelFineTuningJobRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FineTuningApi(config);

  const body = {
    // string
    id: id_example,
  } satisfies CancelFineTuningJobRequest;

  try {
    const data = await api.cancelFineTuningJob(body);
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
| **id** | `string` |  | [Defaults to `undefined`] |

### Return type

[**FineTuningJob**](FineTuningJob.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The cancelled fine-tuning job. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createFile

> FileObject createFile(purpose, file)

Upload a fine-tuning dataset file (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  FineTuningApi,
} from '@gpuai/sdk';
import type { CreateFileRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FineTuningApi(config);

  const body = {
    // string
    purpose: purpose_example,
    // Blob | A JSONL chat-format training dataset.
    file: BINARY_DATA_HERE,
  } satisfies CreateFileRequest;

  try {
    const data = await api.createFile(body);
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
| **purpose** | `fine-tune` |  | [Defaults to `undefined`] [Enum: fine-tune] |
| **file** | `Blob` | A JSONL chat-format training dataset. | [Defaults to `undefined`] |

### Return type

[**FileObject**](FileObject.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The uploaded file object. |  -  |
| **400** | Invalid request (OpenAI error envelope). |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **500** | Internal server error (OpenAI error envelope). |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createFineTuningJob

> FineTuningJob createFineTuningJob(createFineTuningJobRequest)

Create a managed fine-tuning job (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  FineTuningApi,
} from '@gpuai/sdk';
import type { CreateFineTuningJobOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FineTuningApi(config);

  const body = {
    // CreateFineTuningJobRequest
    createFineTuningJobRequest: ...,
  } satisfies CreateFineTuningJobOperationRequest;

  try {
    const data = await api.createFineTuningJob(body);
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
| **createFineTuningJobRequest** | [CreateFineTuningJobRequest](CreateFineTuningJobRequest.md) |  | |

### Return type

[**FineTuningJob**](FineTuningJob.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The created fine-tuning job. |  -  |
| **400** | Invalid request (OpenAI error envelope). |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **402** | Insufficient balance (OpenAI error envelope, SERV-06). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **422** | Request validation failed (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **500** | Internal server error (OpenAI error envelope). |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getFineTuningJob

> FineTuningJob getFineTuningJob(id)

Retrieve a fine-tuning job (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  FineTuningApi,
} from '@gpuai/sdk';
import type { GetFineTuningJobRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FineTuningApi(config);

  const body = {
    // string
    id: id_example,
  } satisfies GetFineTuningJobRequest;

  try {
    const data = await api.getFineTuningJob(body);
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
| **id** | `string` |  | [Defaults to `undefined`] |

### Return type

[**FineTuningJob**](FineTuningJob.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The fine-tuning job. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listFineTuningJobEvents

> FineTuningJobEventList listFineTuningJobEvents(id, after, limit)

List fine-tuning job events (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  FineTuningApi,
} from '@gpuai/sdk';
import type { ListFineTuningJobEventsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FineTuningApi(config);

  const body = {
    // string
    id: id_example,
    // string (optional)
    after: after_example,
    // number (optional)
    limit: 56,
  } satisfies ListFineTuningJobEventsRequest;

  try {
    const data = await api.listFineTuningJobEvents(body);
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
| **id** | `string` |  | [Defaults to `undefined`] |
| **after** | `string` |  | [Optional] [Defaults to `undefined`] |
| **limit** | `number` |  | [Optional] [Defaults to `20`] |

### Return type

[**FineTuningJobEventList**](FineTuningJobEventList.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | A page of fine-tuning job events. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listFineTuningJobs

> FineTuningJobList listFineTuningJobs(after, limit)

List fine-tuning jobs (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  FineTuningApi,
} from '@gpuai/sdk';
import type { ListFineTuningJobsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FineTuningApi(config);

  const body = {
    // string (optional)
    after: after_example,
    // number (optional)
    limit: 56,
  } satisfies ListFineTuningJobsRequest;

  try {
    const data = await api.listFineTuningJobs(body);
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
| **after** | `string` |  | [Optional] [Defaults to `undefined`] |
| **limit** | `number` |  | [Optional] [Defaults to `20`] |

### Return type

[**FineTuningJobList**](FineTuningJobList.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | A page of fine-tuning jobs. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## retrieveFile

> FileObject retrieveFile(id)

Retrieve a file (OpenAI-compatible)

Returns the metadata for one of your uploaded files. The lookup is scoped to the organization the API key belongs to: a file id that does not exist and one that belongs to another organization both return the same 404, so this route cannot be used to probe for other tenants\&#39; ids.  Use it to check that a &#x60;training_file&#x60; is present and usable BEFORE creating a fine-tuning job — the create path performs the identical ownership check, so a file this route returns is a file that create will accept.

### Example

```ts
import {
  Configuration,
  FineTuningApi,
} from '@gpuai/sdk';
import type { RetrieveFileRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new FineTuningApi(config);

  const body = {
    // string | The file id returned by the upload, e.g. `file-9f2c1a...`.
    id: id_example,
  } satisfies RetrieveFileRequest;

  try {
    const data = await api.retrieveFile(body);
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
| **id** | `string` | The file id returned by the upload, e.g. &#x60;file-9f2c1a...&#x60;. | [Defaults to `undefined`] |

### Return type

[**FileObject**](FileObject.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The file object. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **500** | Internal server error (OpenAI error envelope). |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

