# InstancesApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createInstance**](InstancesApi.md#createinstanceoperation) | **POST** /instances | Create an instance (async — returns 202 + Operation-Id header) |
| [**deleteInstance**](InstancesApi.md#deleteinstance) | **DELETE** /instances/{id} | Terminate an instance (idempotent) |
| [**getDedicatedIpOffer**](InstancesApi.md#getdedicatedipoffer) | **GET** /dedicated-ip | Get the dedicated public IP add-on offer |
| [**getInstance**](InstancesApi.md#getinstance) | **GET** /instances/{id} | Get an instance |
| [**getInstanceGpuSuggestion**](InstancesApi.md#getinstancegpusuggestion) | **GET** /instances/{id}/gpu-suggestion | Suggest a lower-priced GPU for an instance |
| [**listInstances**](InstancesApi.md#listinstances) | **GET** /instances | List instances |
| [**updateInstance**](InstancesApi.md#updateinstanceoperation) | **PATCH** /instances/{id} | Update an instance (rename only in v1) |



## createInstance

> Operation createInstance(createInstanceRequest, idempotencyKey)

Create an instance (async — returns 202 + Operation-Id header)

Running a one-off script or batch work? Submit it as a job instead (POST /jobs): the machine is started for it and shut down a few minutes after it finishes, so nothing bills after the work is done.

### Example

```ts
import {
  Configuration,
  InstancesApi,
} from '@gpuai/sdk';
import type { CreateInstanceOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InstancesApi(config);

  const body = {
    // CreateInstanceRequest
    createInstanceRequest: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CreateInstanceOperationRequest;

  try {
    const data = await api.createInstance(body);
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
| **createInstanceRequest** | [CreateInstanceRequest](CreateInstanceRequest.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**Operation**](Operation.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Accepted; long-running operation |  * Operation-Id - Use GET /operations/{id} to poll <br>  * GPUAI-Hint - Advisory only, and absent on most launches. Sent when the request is a one-off batch run (a custom image with a command and auto_terminate_hours) to point at Jobs (POST /jobs), which start a machine for the work and shut it down a few minutes after it ends. It never changes the launch. <br>  * GPUAI-Balance-Warning -  <br>  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteInstance

> Operation deleteInstance(id, idempotencyKey)

Terminate an instance (idempotent)

Members can terminate only instances they created; organization admins can terminate any instance in the organization.

### Example

```ts
import {
  Configuration,
  InstancesApi,
} from '@gpuai/sdk';
import type { DeleteInstanceRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InstancesApi(config);

  const body = {
    // string
    id: id_example,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies DeleteInstanceRequest;

  try {
    const data = await api.deleteInstance(body);
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
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

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
| **202** | Accepted; termination in progress |  * Operation-Id -  <br>  |
| **403** | Forbidden — members can only terminate instances they created |  -  |
| **404** | Already gone — idempotent terminate (D-07) |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getDedicatedIpOffer

> DedicatedIPOffer getDedicatedIpOffer()

Get the dedicated public IP add-on offer

Describes the dedicated public IPv4 add-on for instances and the caller\&#39;s usage of it. A dedicated IP is a GPU.ai-owned public address (never the supplier\&#39;s) that forwards the chosen inbound TCP ports, raw and without TLS termination, to the same ports on the instance\&#39;s loopback. Request one at launch with the &#x60;dedicated_ip&#x60; field on POST /instances.  The response carries the hourly fee charged while the address is attached, the transfer price per GB (counted in both directions), the transfer cap per attachment after which forwarding is suspended, the ports a launch may forward, the organization\&#39;s limit and how many it holds, how many addresses are free right now, and the acceptable use policy. Requires the &#x60;instances:read&#x60; scope. Returns 404 when the add-on is not enabled for this deployment. 

### Example

```ts
import {
  Configuration,
  InstancesApi,
} from '@gpuai/sdk';
import type { GetDedicatedIpOfferRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InstancesApi(config);

  try {
    const data = await api.getDedicatedIpOffer();
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

[**DedicatedIPOffer**](DedicatedIPOffer.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | The dedicated IP add-on is not enabled for this deployment. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getInstance

> Instance getInstance(id, include)

Get an instance

### Example

```ts
import {
  Configuration,
  InstancesApi,
} from '@gpuai/sdk';
import type { GetInstanceRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InstancesApi(config);

  const body = {
    // string
    id: id_example,
    // 'credentials' | Opt-in expansion. `credentials` restores connection.app_password on this single-instance read — the only surface that returns the web-console basic-auth password. Omitted by default so bare reads can be logged without leaking the secret. Any other value is a 400 validation_failed. The list endpoint and operation reads never return the password, with or without this parameter. (optional)
    include: include_example,
  } satisfies GetInstanceRequest;

  try {
    const data = await api.getInstance(body);
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
| **include** | `credentials` | Opt-in expansion. &#x60;credentials&#x60; restores connection.app_password on this single-instance read — the only surface that returns the web-console basic-auth password. Omitted by default so bare reads can be logged without leaking the secret. Any other value is a 400 validation_failed. The list endpoint and operation reads never return the password, with or without this parameter. | [Optional] [Defaults to `undefined`] [Enum: credentials] |

### Return type

[**Instance**](Instance.md)

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


## getInstanceGpuSuggestion

> GpuSuggestion getInstanceGpuSuggestion(id)

Suggest a lower-priced GPU for an instance

Compares the highest GPU memory this instance has used (its &#x60;gpu_memory&#x60; peak, plus headroom) with the GPU models currently listed, and names the cheapest model that would have fit when the saving is worth a look. It never changes anything: it reports what the telemetry shows. Memory use can grow later, so treat it as a starting point.  &#x60;status&#x60; is &#x60;insufficient_data&#x60; until the instance has about an hour of telemetry, &#x60;no_cheaper_fit&#x60; when no cheaper listed model covers the peak, and &#x60;suggestion&#x60; when one does. Requires the &#x60;instances:read&#x60; scope. An instance owned by another organization returns 404. 

### Example

```ts
import {
  Configuration,
  InstancesApi,
} from '@gpuai/sdk';
import type { GetInstanceGpuSuggestionRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InstancesApi(config);

  const body = {
    // string
    id: id_example,
  } satisfies GetInstanceGpuSuggestionRequest;

  try {
    const data = await api.getInstanceGpuSuggestion(body);
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

[**GpuSuggestion**](GpuSuggestion.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | The instance does not exist or is not owned by the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listInstances

> InstancePage listInstances(cursor, limit, status)

List instances

Lists the organization\&#39;s instances. By default terminated instances are excluded; pass status&#x3D;terminated for the history or status&#x3D;all for everything.

### Example

```ts
import {
  Configuration,
  InstancesApi,
} from '@gpuai/sdk';
import type { ListInstancesRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InstancesApi(config);

  const body = {
    // string (optional)
    cursor: cursor_example,
    // number (optional)
    limit: 56,
    // 'allocating' | 'starting' | 'running' | 'stopping' | 'stopped' | 'terminated' | 'error' | 'all' | Filter by customer-facing status (default = all non-terminated). There is no \"unreachable\" filter value: an unreachable instance is a running instance with a dead tunnel, so it is listed under status=running and reads \"unreachable\" in the response body. (optional)
    status: status_example,
  } satisfies ListInstancesRequest;

  try {
    const data = await api.listInstances(body);
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
| **cursor** | `string` |  | [Optional] [Defaults to `undefined`] |
| **limit** | `number` |  | [Optional] [Defaults to `50`] |
| **status** | `allocating`, `starting`, `running`, `stopping`, `stopped`, `terminated`, `error`, `all` | Filter by customer-facing status (default &#x3D; all non-terminated). There is no \&quot;unreachable\&quot; filter value: an unreachable instance is a running instance with a dead tunnel, so it is listed under status&#x3D;running and reads \&quot;unreachable\&quot; in the response body. | [Optional] [Defaults to `undefined`] [Enum: allocating, starting, running, stopping, stopped, terminated, error, all] |

### Return type

[**InstancePage**](InstancePage.md)

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


## updateInstance

> Instance updateInstance(id, updateInstanceRequest, idempotencyKey)

Update an instance (rename only in v1)

### Example

```ts
import {
  Configuration,
  InstancesApi,
} from '@gpuai/sdk';
import type { UpdateInstanceOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new InstancesApi(config);

  const body = {
    // string
    id: id_example,
    // UpdateInstanceRequest
    updateInstanceRequest: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies UpdateInstanceOperationRequest;

  try {
    const data = await api.updateInstance(body);
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
| **updateInstanceRequest** | [UpdateInstanceRequest](UpdateInstanceRequest.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**Instance**](Instance.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

