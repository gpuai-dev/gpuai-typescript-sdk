# CommunityApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**delistCommunityMachine**](CommunityApi.md#delistcommunitymachine) | **POST** /community/machines/{id}/delist | Delist a Community Cloud machine |
| [**enableCommunitySupplier**](CommunityApi.md#enablecommunitysupplier) | **POST** /community/suppliers | Enable the Community Cloud supplier role |
| [**getCommunitySupplierMe**](CommunityApi.md#getcommunitysupplierme) | **GET** /community/suppliers/me | Get the caller\&#39;s Community Cloud supplier |
| [**listCommunityMachines**](CommunityApi.md#listcommunitymachines) | **GET** /community/machines | List your Community Cloud machines |
| [**reclaimCommunityMachine**](CommunityApi.md#reclaimcommunitymachine) | **POST** /community/machines/{id}/reclaim | Reclaim a spot-tier Community Cloud machine |
| [**registerCommunityMachine**](CommunityApi.md#registercommunitymachineoperation) | **POST** /community/machines | Register a Community Cloud machine |



## delistCommunityMachine

> CommunityMachineDelistResult delistCommunityMachine(id)

Delist a Community Cloud machine

Removes a machine the caller\&#39;s org owns from supply (ONBD-04). Drain-not-kill: an occupied machine becomes &#x60;draining&#x60; (its customer rental keeps running until it ends naturally) and an idle machine becomes &#x60;delisted&#x60;. The endpoint never force-terminates a running rental. A missing or cross-org machine returns 404 with an indistinguishable body so existence never leaks across orgs. Requires the &#x60;community&#x60; scope (or &#x60;full_access&#x60;).

### Example

```ts
import {
  Configuration,
  CommunityApi,
} from '@gpuai/sdk';
import type { DelistCommunityMachineRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new CommunityApi(config);

  const body = {
    // string | The machine id to delist.
    id: id_example,
  } satisfies DelistCommunityMachineRequest;

  try {
    const data = await api.delistCommunityMachine(body);
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
| **id** | `string` | The machine id to delist. | [Defaults to `undefined`] |

### Return type

[**CommunityMachineDelistResult**](CommunityMachineDelistResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The terminal status the machine reached. |  -  |
| **403** | The community supplier role is suspended. |  -  |
| **404** | The machine does not exist or is not owned by the caller\&#39;s org. |  -  |
| **409** | The community supplier role has not been enabled yet. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## enableCommunitySupplier

> CommunitySupplier enableCommunitySupplier(idempotencyKey)

Enable the Community Cloud supplier role

Idempotently enables the Community Cloud supplier role for the organization the API key belongs to. A repeat call is a no-op that returns the same supplier record (200, not 201). Requires the &#x60;community&#x60; scope (or &#x60;full_access&#x60;).

### Example

```ts
import {
  Configuration,
  CommunityApi,
} from '@gpuai/sdk';
import type { EnableCommunitySupplierRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new CommunityApi(config);

  const body = {
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies EnableCommunitySupplierRequest;

  try {
    const data = await api.enableCommunitySupplier(body);
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
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**CommunitySupplier**](CommunitySupplier.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The community supplier record (created or already-existing). |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getCommunitySupplierMe

> CommunitySupplier getCommunitySupplierMe()

Get the caller\&#39;s Community Cloud supplier

Returns the community supplier record for the organization the API key belongs to, or 404 &#x60;not-a-supplier&#x60; when the role has not been enabled. Requires the &#x60;community&#x60; scope (read).

### Example

```ts
import {
  Configuration,
  CommunityApi,
} from '@gpuai/sdk';
import type { GetCommunitySupplierMeRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new CommunityApi(config);

  try {
    const data = await api.getCommunitySupplierMe();
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

[**CommunitySupplier**](CommunitySupplier.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The community supplier record. |  -  |
| **404** | The organization has not enabled the community supplier role. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listCommunityMachines

> ListCommunityMachines200Response listCommunityMachines()

List your Community Cloud machines

Returns every machine the caller\&#39;s org has registered, newest first, as supplier-facing views (&#x60;occupied&#x60;/&#x60;online&#x60; projections — the renting customer\&#39;s instance id is never exposed). Requires the &#x60;community&#x60; scope (read).

### Example

```ts
import {
  Configuration,
  CommunityApi,
} from '@gpuai/sdk';
import type { ListCommunityMachinesRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new CommunityApi(config);

  try {
    const data = await api.listCommunityMachines();
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

[**ListCommunityMachines200Response**](ListCommunityMachines200Response.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The caller\&#39;s machines. |  -  |
| **404** | The organization has not enabled the community supplier role. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## reclaimCommunityMachine

> CommunityMachineDelistResult reclaimCommunityMachine(id)

Reclaim a spot-tier Community Cloud machine

The spot interruption mechanic — the supplier takes back a machine they listed as interruptible (tier&#x3D;spot). Drain-not-kill: an occupied machine becomes &#x60;draining&#x60; (the renter gets the grace window, surfaced to the spot router as a preemption warning) and an idle machine becomes &#x60;delisted&#x60;. An on-demand machine cannot be reclaimed (409 &#x60;machine-not-spot&#x60;) — use delist instead. Requires the &#x60;community&#x60; scope (or &#x60;full_access&#x60;).

### Example

```ts
import {
  Configuration,
  CommunityApi,
} from '@gpuai/sdk';
import type { ReclaimCommunityMachineRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new CommunityApi(config);

  const body = {
    // string | The machine id to reclaim.
    id: id_example,
  } satisfies ReclaimCommunityMachineRequest;

  try {
    const data = await api.reclaimCommunityMachine(body);
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
| **id** | `string` | The machine id to reclaim. | [Defaults to `undefined`] |

### Return type

[**CommunityMachineDelistResult**](CommunityMachineDelistResult.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The status the machine reached. |  -  |
| **403** | The community supplier role is suspended. |  -  |
| **404** | The machine does not exist or is not owned by the caller\&#39;s org. |  -  |
| **409** | The supplier role has not been enabled, or the machine is on-demand capacity (&#x60;machine-not-spot&#x60;). |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## registerCommunityMachine

> CommunityMachineRegistration registerCommunityMachine(idempotencyKey, registerCommunityMachineRequest)

Register a Community Cloud machine

Registers a self-declared machine under the caller\&#39;s community supplier and mints a one-time enrollment token. All spec fields are optional — an empty body registers a placeholder in &#x60;pending_verification&#x60;. The &#x60;enrollment_token&#x60; is shown exactly once and never returned again. Requires the &#x60;community&#x60; scope (or &#x60;full_access&#x60;).

### Example

```ts
import {
  Configuration,
  CommunityApi,
} from '@gpuai/sdk';
import type { RegisterCommunityMachineOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new CommunityApi(config);

  const body = {
    // string (optional)
    idempotencyKey: idempotencyKey_example,
    // RegisterCommunityMachineRequest (optional)
    registerCommunityMachineRequest: ...,
  } satisfies RegisterCommunityMachineOperationRequest;

  try {
    const data = await api.registerCommunityMachine(body);
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
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |
| **registerCommunityMachineRequest** | [RegisterCommunityMachineRequest](RegisterCommunityMachineRequest.md) |  | [Optional] |

### Return type

[**CommunityMachineRegistration**](CommunityMachineRegistration.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | The registered machine plus its one-time enrollment token. |  -  |
| **403** | The community supplier role is suspended. |  -  |
| **409** | The community supplier role has not been enabled yet. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

