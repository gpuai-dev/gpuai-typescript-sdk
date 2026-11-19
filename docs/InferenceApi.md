# InferenceApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**cancelVideo**](InferenceApi.md#cancelvideo) | **POST** /videos/{id}/cancel | Cancel a video generation job |
| [**createChatCompletion**](InferenceApi.md#createchatcompletion) | **POST** /chat/completions | Create a chat completion (OpenAI-compatible) |
| [**createEmbeddings**](InferenceApi.md#createembeddings) | **POST** /embeddings | Create embeddings (OpenAI-compatible) |
| [**createImage**](InferenceApi.md#createimage) | **POST** /images/generations | Create image (OpenAI-compatible) |
| [**createVideo**](InferenceApi.md#createvideo) | **POST** /videos | Create a video generation job (async) |
| [**getDataRetention**](InferenceApi.md#getdataretention) | **GET** /organization/data-retention | Get the org zero data retention setting |
| [**getModel**](InferenceApi.md#getmodel) | **GET** /models/{id} | Get a specific model (OpenAI-compatible) |
| [**getVideo**](InferenceApi.md#getvideo) | **GET** /videos/{id} | Get a video generation job |
| [**getVideoContent**](InferenceApi.md#getvideocontent) | **GET** /videos/{id}/content | Download a completed video artifact |
| [**listModels**](InferenceApi.md#listmodels) | **GET** /models | List available models (OpenAI-compatible) |
| [**listVideos**](InferenceApi.md#listvideos) | **GET** /videos | List video generation jobs |
| [**updateDataRetention**](InferenceApi.md#updatedataretentionoperation) | **PUT** /organization/data-retention | Turn zero data retention on or off for the org |



## cancelVideo

> VideoJob cancelVideo(id)

Cancel a video generation job

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { CancelVideoRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // string
    id: id_example,
  } satisfies CancelVideoRequest;

  try {
    const data = await api.cancelVideo(body);
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

[**VideoJob**](VideoJob.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | A video generation job object. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **409** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createChatCompletion

> ChatCompletionResponse createChatCompletion(chatCompletionRequest, xGPUAIZeroDataRetention)

Create a chat completion (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { CreateChatCompletionRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // ChatCompletionRequest
    chatCompletionRequest: ...,
    // 'true' | 'false' | Send `true` to require zero data retention for this request even when the org setting is off. It can only tighten routing: `false` never relaxes an org with zero data retention on. Responses routed under zero data retention echo this header with `true`. A model without a zero-data-retention host returns 400 `zero_data_retention_unavailable`; a value other than true/false returns 400 `invalid_header`. (optional)
    xGPUAIZeroDataRetention: xGPUAIZeroDataRetention_example,
  } satisfies CreateChatCompletionRequest;

  try {
    const data = await api.createChatCompletion(body);
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
| **chatCompletionRequest** | [ChatCompletionRequest](ChatCompletionRequest.md) |  | |
| **xGPUAIZeroDataRetention** | `true`, `false` | Send &#x60;true&#x60; to require zero data retention for this request even when the org setting is off. It can only tighten routing: &#x60;false&#x60; never relaxes an org with zero data retention on. Responses routed under zero data retention echo this header with &#x60;true&#x60;. A model without a zero-data-retention host returns 400 &#x60;zero_data_retention_unavailable&#x60;; a value other than true/false returns 400 &#x60;invalid_header&#x60;. | [Optional] [Defaults to `undefined`] [Enum: true, false] |

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
| **200** | Successful response. application/json for non-streaming requests; text/event-stream for streaming requests (stream&#x3D;true).  |  -  |
| **400** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **402** | Insufficient balance (OpenAI error envelope, SERV-06). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **422** | Request validation failed (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **500** | Internal server error (OpenAI error envelope). |  -  |
| **503** | Upstream provider unavailable (OpenAI error envelope). Retry-After header may indicate seconds to wait. Code &#x60;data_retention_check_failed&#x60; means the org zero data retention setting could not be read, so the request was not sent; retry shortly. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createEmbeddings

> EmbeddingsResponse createEmbeddings(embeddingsRequest, xGPUAIZeroDataRetention)

Create embeddings (OpenAI-compatible)

Synchronous text embeddings. Accepts a single string or an array of up to 2048 strings, bounded so the response stays under 64 MiB (about 680 inputs at 4096 dimensions; fewer at a larger &#x60;dimensions&#x60; value) — over-limit requests are rejected with 400 before any processing. Returns one float vector per input, in request order. Billed on the upstream\&#39;s reported prompt tokens at the model\&#39;s listed input rate, rounded up to the next whole cent per request; an embeddings call emits no completion tokens, so &#x60;usage&#x60; carries &#x60;prompt_tokens&#x60; and &#x60;total_tokens&#x60; only. &#x60;encoding_format&#x60; accepts only &#x60;float&#x60; — a value of &#x60;base64&#x60; is rejected with &#x60;unsupported_parameter&#x60;. A chat model id on this route returns 404 &#x60;model_not_found&#x60;: the id is valid, but not on this surface.

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { CreateEmbeddingsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // EmbeddingsRequest
    embeddingsRequest: ...,
    // 'true' | 'false' | Send `true` to require zero data retention for this request even when the org setting is off. It can only tighten routing: `false` never relaxes an org with zero data retention on. Responses routed under zero data retention echo this header with `true`. A model without a zero-data-retention host returns 400 `zero_data_retention_unavailable`; a value other than true/false returns 400 `invalid_header`. (optional)
    xGPUAIZeroDataRetention: xGPUAIZeroDataRetention_example,
  } satisfies CreateEmbeddingsRequest;

  try {
    const data = await api.createEmbeddings(body);
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
| **embeddingsRequest** | [EmbeddingsRequest](EmbeddingsRequest.md) |  | |
| **xGPUAIZeroDataRetention** | `true`, `false` | Send &#x60;true&#x60; to require zero data retention for this request even when the org setting is off. It can only tighten routing: &#x60;false&#x60; never relaxes an org with zero data retention on. Responses routed under zero data retention echo this header with &#x60;true&#x60;. A model without a zero-data-retention host returns 400 &#x60;zero_data_retention_unavailable&#x60;; a value other than true/false returns 400 &#x60;invalid_header&#x60;. | [Optional] [Defaults to `undefined`] [Enum: true, false] |

### Return type

[**EmbeddingsResponse**](EmbeddingsResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One embedding vector per input, in request order. |  -  |
| **400** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **402** | Insufficient balance (OpenAI error envelope, SERV-06). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **413** | Request body too large (OpenAI error envelope, code request_too_large). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **500** | Internal server error (OpenAI error envelope). |  -  |
| **502** | The upstream answered but its response could not be used (OpenAI error envelope): code upstream_response_too_large when the vector payload exceeded the per-request size limit, or upstream_error for a malformed / misaligned response. Not retryable as-is for upstream_response_too_large — send fewer inputs. |  -  |
| **503** | Upstream provider unavailable (OpenAI error envelope). Retry-After header may indicate seconds to wait. Code &#x60;data_retention_check_failed&#x60; means the org zero data retention setting could not be read, so the request was not sent; retry shortly. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **504** | Upstream provider exceeded the synchronous per-attempt deadline (OpenAI error envelope). 504 semantic — distinct from 503 OpenAIUpstreamUnavailable which signals a connection or routing failure rather than a timeout.  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createImage

> ImagesResponse createImage(imagesGenerationsRequest, idempotencyKey, xGPUAIZeroDataRetention)

Create image (OpenAI-compatible)

Synchronous text-to-image generation. Returns base64-encoded images only (&#x60;response_format&#x60; is restricted to &#x60;b64_json&#x60;); a value of &#x60;url&#x60; is rejected with &#x60;invalid_request_error&#x60; until S3-backed URL delivery lands. Pass an &#x60;Idempotency-Key&#x60; header to make a retried request replay the original response without a second charge.

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { CreateImageRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // ImagesGenerationsRequest
    imagesGenerationsRequest: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
    // 'true' | 'false' | Send `true` to require zero data retention for this request even when the org setting is off. It can only tighten routing: `false` never relaxes an org with zero data retention on. Responses routed under zero data retention echo this header with `true`. A model without a zero-data-retention host returns 400 `zero_data_retention_unavailable`; a value other than true/false returns 400 `invalid_header`. (optional)
    xGPUAIZeroDataRetention: xGPUAIZeroDataRetention_example,
  } satisfies CreateImageRequest;

  try {
    const data = await api.createImage(body);
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
| **imagesGenerationsRequest** | [ImagesGenerationsRequest](ImagesGenerationsRequest.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |
| **xGPUAIZeroDataRetention** | `true`, `false` | Send &#x60;true&#x60; to require zero data retention for this request even when the org setting is off. It can only tighten routing: &#x60;false&#x60; never relaxes an org with zero data retention on. Responses routed under zero data retention echo this header with &#x60;true&#x60;. A model without a zero-data-retention host returns 400 &#x60;zero_data_retention_unavailable&#x60;; a value other than true/false returns 400 &#x60;invalid_header&#x60;. | [Optional] [Defaults to `undefined`] [Enum: true, false] |

### Return type

[**ImagesResponse**](ImagesResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OpenAI-shaped image generation response (b64_json only). |  -  |
| **400** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **402** | Insufficient balance (OpenAI error envelope, SERV-06). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **422** | Request validation failed (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **500** | Internal server error (OpenAI error envelope). |  -  |
| **503** | Upstream provider unavailable (OpenAI error envelope). Retry-After header may indicate seconds to wait. Code &#x60;data_retention_check_failed&#x60; means the org zero data retention setting could not be read, so the request was not sent; retry shortly. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **504** | Upstream provider exceeded the synchronous per-attempt deadline (OpenAI error envelope). 504 semantic — distinct from 503 OpenAIUpstreamUnavailable which signals a connection or routing failure rather than a timeout.  |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createVideo

> VideoJob createVideo(videoCreateRequest, idempotencyKey)

Create a video generation job (async)

Submit an asynchronous text-to-video generation job. Returns a job object with status &#x60;queued&#x60;; poll GET /videos/{id} until &#x60;completed&#x60;, then stream the result from GET /videos/{id}/content. Pass an &#x60;Idempotency-Key&#x60; header to make a retried request replay the original response without a second charge.

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { CreateVideoRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // VideoCreateRequest
    videoCreateRequest: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CreateVideoRequest;

  try {
    const data = await api.createVideo(body);
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
| **videoCreateRequest** | [VideoCreateRequest](VideoCreateRequest.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**VideoJob**](VideoJob.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | A video generation job object. |  -  |
| **400** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **402** | Insufficient balance (OpenAI error envelope, SERV-06). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **500** | Internal server error (OpenAI error envelope). |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getDataRetention

> DataRetention getDataRetention()

Get the org zero data retention setting

Returns whether zero data retention (ZDR) is on for the organization. When it is on, chat, embeddings and image requests route only to model hosts that keep no prompt or output content, a model without one returns 400 &#x60;zero_data_retention_unavailable&#x60;, and video generation is refused. Requires the &#x60;serverless:read&#x60; scope. The organization is taken from the authenticated API key. 

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { GetDataRetentionRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  try {
    const data = await api.getDataRetention();
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

[**DataRetention**](DataRetention.md)

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


## getModel

> Model getModel(id)

Get a specific model (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { GetModelRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // string
    id: id_example,
  } satisfies GetModelRequest;

  try {
    const data = await api.getModel(body);
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

[**Model**](Model.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OpenAI-shaped single model. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getVideo

> VideoJob getVideo(id)

Get a video generation job

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { GetVideoRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // string
    id: id_example,
  } satisfies GetVideoRequest;

  try {
    const data = await api.getVideo(body);
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

[**VideoJob**](VideoJob.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | A video generation job object. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getVideoContent

> Blob getVideoContent(id)

Download a completed video artifact

Streams the generated MP4 for a completed job. Returns 410 Gone once the artifact has expired (24h retention).

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { GetVideoContentRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // string
    id: id_example,
  } satisfies GetVideoContentRequest;

  try {
    const data = await api.getVideoContent(body);
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

**Blob**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `video/mp4`, `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The generated video stream. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **404** | Model or resource not found (OpenAI error envelope). |  -  |
| **410** | The requested artifact has expired and is no longer available (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listModels

> ModelList listModels(modality)

List available models (OpenAI-compatible)

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { ListModelsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // 'chat' | 'image' | 'video' | 'embedding' (optional)
    modality: modality_example,
  } satisfies ListModelsRequest;

  try {
    const data = await api.listModels(body);
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
| **modality** | `chat`, `image`, `video`, `embedding` |  | [Optional] [Defaults to `undefined`] [Enum: chat, image, video, embedding] |

### Return type

[**ModelList**](ModelList.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OpenAI-shaped model list. |  -  |
| **400** | Invalid request (OpenAI error envelope). On inference routes this includes &#x60;zero_data_retention_unavailable&#x60; when zero data retention is required and the model has no zero-data-retention host. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listVideos

> VideoList listVideos(after, limit)

List video generation jobs

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { ListVideosRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // string (optional)
    after: after_example,
    // number (optional)
    limit: 56,
  } satisfies ListVideosRequest;

  try {
    const data = await api.listVideos(body);
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
| **limit** | `number` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**VideoList**](VideoList.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | A page of video generation jobs. |  -  |
| **401** | Missing or invalid API key (OpenAI error envelope). |  -  |
| **403** | API key lacks the required scope (OpenAI error envelope). |  -  |
| **429** | Rate limit exceeded (OpenAI error envelope). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## updateDataRetention

> DataRetention updateDataRetention(updateDataRetentionRequest)

Turn zero data retention on or off for the org

Sets the organization\&#39;s zero data retention (ZDR) setting. Takes effect from the next inference request. Requires the &#x60;serverless:write&#x60; scope AND org-admin privileges (a non-admin member gets 403). &#x60;zero_data_retention&#x60; is required (422 when missing). 

### Example

```ts
import {
  Configuration,
  InferenceApi,
} from '@gpuai/sdk';
import type { UpdateDataRetentionOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InferenceApi(config);

  const body = {
    // UpdateDataRetentionRequest
    updateDataRetentionRequest: ...,
  } satisfies UpdateDataRetentionOperationRequest;

  try {
    const data = await api.updateDataRetention(body);
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
| **updateDataRetentionRequest** | [UpdateDataRetentionRequest](UpdateDataRetentionRequest.md) |  | |

### Return type

[**DataRetention**](DataRetention.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **403** | Error response (RFC 7807) |  -  |
| **422** | Error response (RFC 7807) |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

