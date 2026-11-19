# OperationsApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**cancelOperation**](OperationsApi.md#canceloperation) | **POST** /operations/{id}/cancel | Cancel a launch that has not created its instance yet |
| [**getOperation**](OperationsApi.md#getoperation) | **GET** /operations/{id} | Get an async operation status |



## cancelOperation

> Operation cancelOperation(id)

Cancel a launch that has not created its instance yet

Cancels an instance.create operation that is still pending or in_progress and has no resource_id yet. Nothing is created or billed for a cancelled launch; if the supplier finishes creating the machine after the cancel, it is terminated right away. Cancelling an operation that already finished returns it unchanged, so the call is safe to repeat. Scoped like GET /operations/{id}: only the key that started the operation can cancel it. Requires the &#x60;instances:write&#x60; scope.

### Example

```ts
import {
  Configuration,
  OperationsApi,
} from '@gpuai/sdk';
import type { CancelOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new OperationsApi(config);

  const body = {
    // string
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies CancelOperationRequest;

  try {
    const data = await api.cancelOperation(body);
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

[**Operation**](Operation.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The operation, &#x60;cancelled&#x60; unless it had already finished. |  -  |
| **404** | &#x60;not_found&#x60;. No operation with this id for this key. |  -  |
| **409** | &#x60;validation_failed&#x60;. The operation is not a launch, or the launch already created its instance. The detail names the instance to delete instead. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getOperation

> Operation getOperation(id)

Get an async operation status

### Example

```ts
import {
  Configuration,
  OperationsApi,
} from '@gpuai/sdk';
import type { GetOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new OperationsApi(config);

  const body = {
    // string
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies GetOperationRequest;

  try {
    const data = await api.getOperation(body);
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

[**Operation**](Operation.md)

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

