# EndpointsApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createEndpoint**](EndpointsApi.md#createendpoint) | **POST** /endpoints | Create a model endpoint |
| [**createEndpointChatCompletion**](EndpointsApi.md#createendpointchatcompletion) | **POST** /endpoints/{id}/openai/v1/chat/completions | Chat completion on a model endpoint (OpenAI-compatible) |
| [**createEndpointCompletion**](EndpointsApi.md#createendpointcompletion) | **POST** /endpoints/{id}/openai/v1/completions | Text completion on a model endpoint (OpenAI-compatible) |
| [**deleteEndpoint**](EndpointsApi.md#deleteendpoint) | **DELETE** /endpoints/{id} | Delete a model endpoint |
| [**getEndpoint**](EndpointsApi.md#getendpoint) | **GET** /endpoints/{id} | Get a model endpoint |
| [**listEndpointModels**](EndpointsApi.md#listendpointmodels) | **GET** /endpoints/{id}/openai/v1/models | List the model an endpoint serves (OpenAI-compatible) |
| [**listEndpoints**](EndpointsApi.md#listendpoints) | **GET** /endpoints | List model endpoints |



## createEndpoint

> Endpoint createEndpoint(endpointCreate)

Create a model endpoint

Creates an OpenAI-compatible endpoint serving a Hugging Face model with vLLM on the chosen GPU type. Nothing starts until the first request arrives, unless &#x60;min_replicas&#x60; keeps machines warm. Each machine is billed for the time it exists, like an instance, through the same balance. For a gated model, store a Hugging Face token as a secret and name it in &#x60;hf_token_secret&#x60;; it reaches the machines as HF_TOKEN. Returns 422 &#x60;validation_failed&#x60; for a bad field, 409 &#x60;name_taken&#x60; for a duplicate name, and 409 &#x60;limit_reached&#x60; at the per-organization cap. Requires the &#x60;functions:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  EndpointsApi,
} from '@gpuai/sdk';
import type { CreateEndpointRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new EndpointsApi(config);

  const body = {
    // EndpointCreate
    endpointCreate: ...,
  } satisfies CreateEndpointRequest;

  try {
    const data = await api.createEndpoint(body);
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
| **endpointCreate** | [EndpointCreate](EndpointCreate.md) |  | |

### Return type

[**Endpoint**](Endpoint.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createEndpointChatCompletion

> ChatCompletionResponse createEndpointChatCompletion(id, chatCompletionRequest)

Chat completion on a model endpoint (OpenAI-compatible)

The OpenAI chat completions route of one endpoint: point an OpenAI client\&#39;s base_url at the endpoint\&#39;s &#x60;url&#x60; and use a GPU.ai API key with the &#x60;functions:write&#x60; scope. The request\&#39;s &#x60;model&#x60; is replaced with the endpoint\&#39;s model, so any value works. Set &#x60;\&quot;stream\&quot;: true&#x60; for Server-Sent Events, passed through as vLLM produces them. When no machine is ready the request waits while one starts (a cold start takes minutes: machine, image and model download); if none is ready in time the answer is 503 &#x60;endpoint_starting&#x60; with Retry-After. 402 &#x60;insufficient_quota&#x60; when the balance is empty. Errors use the OpenAI error envelope.

### Example

```ts
import {
  Configuration,
  EndpointsApi,
} from '@gpuai/sdk';
import type { CreateEndpointChatCompletionRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new EndpointsApi(config);

  const body = {
    // string | The endpoint\'s id.
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
    // ChatCompletionRequest
    chatCompletionRequest: ...,
  } satisfies CreateEndpointChatCompletionRequest;

  try {
    const data = await api.createEndpointChatCompletion(body);
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
| **id** | `string` | The endpoint\&#39;s id. | [Defaults to `undefined`] |
| **chatCompletionRequest** | [ChatCompletionRequest](ChatCompletionRequest.md) |  | |

### Return type

[**ChatCompletionResponse**](ChatCompletionResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `text/event-stream`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | application/json for non-streaming requests; text/event-stream when stream&#x3D;true.  |  -  |
| **400** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **402** | Insufficient balance (OpenAI error envelope, SERV-06). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **502** | Internal server error (OpenAI error envelope). |  -  |
| **503** | Upstream provider unavailable (OpenAI error envelope). Retry-After header may indicate seconds to wait. Code &#x60;data_retention_check_failed&#x60; means the org zero data retention setting could not be read, so the request was not sent; retry shortly. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createEndpointCompletion

> { [key: string]: any; } createEndpointCompletion(id, requestBody)

Text completion on a model endpoint (OpenAI-compatible)

The OpenAI completions route of one endpoint, with the same auth, model rewrite, streaming, cold start and error behavior as chat completions.

### Example

```ts
import {
  Configuration,
  EndpointsApi,
} from '@gpuai/sdk';
import type { CreateEndpointCompletionRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new EndpointsApi(config);

  const body = {
    // string | The endpoint\'s id.
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
    // { [key: string]: any | null; }
    requestBody: Object,
  } satisfies CreateEndpointCompletionRequest;

  try {
    const data = await api.createEndpointCompletion(body);
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
| **id** | `string` | The endpoint\&#39;s id. | [Defaults to `undefined`] |
| **requestBody** | `{ [key: string]: any | null; }` |  | |

### Return type

**{ [key: string]: any; }**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `text/event-stream`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | application/json for non-streaming requests; text/event-stream when stream&#x3D;true.  |  -  |
| **400** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **402** | Insufficient balance (OpenAI error envelope, SERV-06). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **502** | Internal server error (OpenAI error envelope). |  -  |
| **503** | Upstream provider unavailable (OpenAI error envelope). Retry-After header may indicate seconds to wait. Code &#x60;data_retention_check_failed&#x60; means the org zero data retention setting could not be read, so the request was not sent; retry shortly. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteEndpoint

> deleteEndpoint(id)

Delete a model endpoint

Deletes the endpoint. Its machines are released within seconds and stop billing when terminated. Requires the &#x60;functions:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  EndpointsApi,
} from '@gpuai/sdk';
import type { DeleteEndpointRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new EndpointsApi(config);

  const body = {
    // string | The endpoint\'s id.
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies DeleteEndpointRequest;

  try {
    const data = await api.deleteEndpoint(body);
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
| **id** | `string` | The endpoint\&#39;s id. | [Defaults to `undefined`] |

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


## getEndpoint

> Endpoint getEndpoint(id)

Get a model endpoint

Returns one endpoint with its recent machines (newest first), each with its price, ready and terminated times, and why it was released. Requires the &#x60;functions:read&#x60; scope.

### Example

```ts
import {
  Configuration,
  EndpointsApi,
} from '@gpuai/sdk';
import type { GetEndpointRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new EndpointsApi(config);

  const body = {
    // string | The endpoint\'s id.
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies GetEndpointRequest;

  try {
    const data = await api.getEndpoint(body);
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
| **id** | `string` | The endpoint\&#39;s id. | [Defaults to `undefined`] |

### Return type

[**Endpoint**](Endpoint.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The endpoint. |  -  |
| **404** | Error response (RFC 7807) |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listEndpointModels

> { [key: string]: any; } listEndpointModels(id)

List the model an endpoint serves (OpenAI-compatible)

The OpenAI models route of one endpoint: the one model it serves. Can trigger a cold start like any other request.

### Example

```ts
import {
  Configuration,
  EndpointsApi,
} from '@gpuai/sdk';
import type { ListEndpointModelsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new EndpointsApi(config);

  const body = {
    // string | The endpoint\'s id.
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies ListEndpointModelsRequest;

  try {
    const data = await api.listEndpointModels(body);
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
| **id** | `string` | The endpoint\&#39;s id. | [Defaults to `undefined`] |

### Return type

**{ [key: string]: any; }**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | An OpenAI model list. |  -  |
| **400** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **402** | Insufficient balance (OpenAI error envelope, SERV-06). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **502** | Internal server error (OpenAI error envelope). |  -  |
| **503** | Upstream provider unavailable (OpenAI error envelope). Retry-After header may indicate seconds to wait. Code &#x60;data_retention_check_failed&#x60; means the org zero data retention setting could not be read, so the request was not sent; retry shortly. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listEndpoints

> EndpointList listEndpoints()

List model endpoints

Lists the organization\&#39;s live model endpoints with their status, URL and machine counts. Requires the &#x60;functions:read&#x60; scope.

### Example

```ts
import {
  Configuration,
  EndpointsApi,
} from '@gpuai/sdk';
import type { ListEndpointsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new EndpointsApi(config);

  try {
    const data = await api.listEndpoints();
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

[**EndpointList**](EndpointList.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The organization\&#39;s endpoints. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

