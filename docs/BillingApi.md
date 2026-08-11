# BillingApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getSpendingLimit**](BillingApi.md#getspendinglimit) | **GET** /billing/spending-limit | Get the org spending limit |
| [**updateSpendingLimit**](BillingApi.md#updatespendinglimitoperation) | **PUT** /billing/spending-limit | Set the org spending limit |



## getSpendingLimit

> SpendingLimit getSpendingLimit()

Get the org spending limit

Returns the organization\&#39;s monthly spending limit and opt-in daily spend cap, with the current month and day spend. Requires the &#x60;billing:read&#x60; scope. Returns 404 when no limit is configured. 

### Example

```ts
import {
  Configuration,
  BillingApi,
} from '@gpuai/sdk';
import type { GetSpendingLimitRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new BillingApi(config);

  try {
    const data = await api.getSpendingLimit();
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

[**SpendingLimit**](SpendingLimit.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | Error response (RFC 7807) |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## updateSpendingLimit

> SpendingLimit updateSpendingLimit(updateSpendingLimitRequest)

Set the org spending limit

Sets the monthly spending limit and optionally sets or clears the opt-in daily spend cap. Requires the &#x60;billing:write&#x60; scope AND org-admin privileges (a non-admin member gets 403). &#x60;daily_limit_dollars&#x60; uses pointer semantics: omit to leave the cap unchanged, 0 to clear it, a positive value to set it. 

### Example

```ts
import {
  Configuration,
  BillingApi,
} from '@gpuai/sdk';
import type { UpdateSpendingLimitOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new BillingApi(config);

  const body = {
    // UpdateSpendingLimitRequest
    updateSpendingLimitRequest: ...,
  } satisfies UpdateSpendingLimitOperationRequest;

  try {
    const data = await api.updateSpendingLimit(body);
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
| **updateSpendingLimitRequest** | [UpdateSpendingLimitRequest](UpdateSpendingLimitRequest.md) |  | |

### Return type

[**SpendingLimit**](SpendingLimit.md)

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

