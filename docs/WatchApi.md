# WatchApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createWatchRule**](WatchApi.md#createwatchrule) | **POST** /watch-rules | Create a watch rule |
| [**deleteWatchRule**](WatchApi.md#deletewatchrule) | **DELETE** /watch-rules/{id} | Delete a watch rule |
| [**getWatchRule**](WatchApi.md#getwatchrule) | **GET** /watch-rules/{id} | Get a watch rule |
| [**listWatchRules**](WatchApi.md#listwatchrules) | **GET** /watch-rules | List watch rules |
| [**updateWatchRule**](WatchApi.md#updatewatchrule) | **PATCH** /watch-rules/{id} | Update a watch rule |



## createWatchRule

> WatchRule createWatchRule(watchRuleCreate, idempotencyKey)

Create a watch rule

Creates a rule that notifies you when the market moves on a GPU model. Requires the &#x60;watch:write&#x60; scope (or &#x60;full_access&#x60;).  A watch rule ONLY notifies. It cannot launch capacity and cannot spend money: there is no field on this resource that provisions anything. Automatic launching is a separate resource with its own spend-consent gate.  Targeting is dimensional — a GPU model plus optional canonical region and capacity class. It is deliberately NOT possible to pin a rule to a specific catalog listing: listing identity is unstable, so a pinned rule can silently match nothing and never fire.  Delivery is to the organization\&#39;s registered webhook endpoints, plus an email to the rule\&#39;s creator. &#x60;webhook_endpoint_override_id&#x60; routes one rule to one specific endpoint and is the id of an endpoint already registered via &#x60;/webhook-endpoints&#x60; — the resource accepts no URL of any kind.  Organizations are limited to 50 ENABLED rules; the 422 names the limit. 

### Example

```ts
import {
  Configuration,
  WatchApi,
} from '@gpuai/sdk';
import type { CreateWatchRuleRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new WatchApi(config);

  const body = {
    // WatchRuleCreate
    watchRuleCreate: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CreateWatchRuleRequest;

  try {
    const data = await api.createWatchRule(body);
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
| **watchRuleCreate** | [WatchRuleCreate](WatchRuleCreate.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**WatchRule**](WatchRule.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created |  -  |
| **422** | Validation failed — an unknown condition kind, a non-canonical region, a missing threshold on a threshold condition, an override id that is not an endpoint registered by this organization, a field naming a catalog listing or a delivery address, or the enabled-rule limit already reached.  |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteWatchRule

> deleteWatchRule(id)

Delete a watch rule

Deletes a watch rule. Requires the &#x60;watch:write&#x60; scope (or &#x60;full_access&#x60;). Deleting an already-deleted rule returns 404. 

### Example

```ts
import {
  Configuration,
  WatchApi,
} from '@gpuai/sdk';
import type { DeleteWatchRuleRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new WatchApi(config);

  const body = {
    // string
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies DeleteWatchRuleRequest;

  try {
    const data = await api.deleteWatchRule(body);
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

`void` (Empty response body)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Deleted |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getWatchRule

> WatchRule getWatchRule(id)

Get a watch rule

Fetches one watch rule. Requires the &#x60;watch:read&#x60; scope (or &#x60;full_access&#x60;). A rule belonging to another organization returns 404 — the same answer as an id that does not exist. 

### Example

```ts
import {
  Configuration,
  WatchApi,
} from '@gpuai/sdk';
import type { GetWatchRuleRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new WatchApi(config);

  const body = {
    // string
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies GetWatchRuleRequest;

  try {
    const data = await api.getWatchRule(body);
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

[**WatchRule**](WatchRule.md)

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


## listWatchRules

> WatchRulePage listWatchRules(cursor, limit)

List watch rules

Lists this organization\&#39;s watch rules. Requires the &#x60;watch:read&#x60; scope (or &#x60;full_access&#x60;). Rules belonging to other organizations are never returned. 

### Example

```ts
import {
  Configuration,
  WatchApi,
} from '@gpuai/sdk';
import type { ListWatchRulesRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new WatchApi(config);

  const body = {
    // string (optional)
    cursor: cursor_example,
    // number (optional)
    limit: 56,
  } satisfies ListWatchRulesRequest;

  try {
    const data = await api.listWatchRules(body);
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

### Return type

[**WatchRulePage**](WatchRulePage.md)

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


## updateWatchRule

> WatchRule updateWatchRule(id, watchRuleUpdate)

Update a watch rule

Partially updates a watch rule. Requires the &#x60;watch:write&#x60; scope (or &#x60;full_access&#x60;).  An ABSENT key keeps the stored value; an explicit &#x60;null&#x60; on &#x60;region&#x60;, &#x60;capacity_class&#x60; or &#x60;webhook_endpoint_override_id&#x60; CLEARS it back to \&quot;any\&quot; / \&quot;organization default\&quot;. The two are distinguished by which keys the body carries, so send only the keys you mean to change.  Editing a rule RE-ARMS it: the fired latch describes the condition that was replaced, so carrying it across an edit would suppress the first alert on the new one. 

### Example

```ts
import {
  Configuration,
  WatchApi,
} from '@gpuai/sdk';
import type { UpdateWatchRuleRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new WatchApi(config);

  const body = {
    // string
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
    // WatchRuleUpdate
    watchRuleUpdate: ...,
  } satisfies UpdateWatchRuleRequest;

  try {
    const data = await api.updateWatchRule(body);
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
| **watchRuleUpdate** | [WatchRuleUpdate](WatchRuleUpdate.md) |  | |

### Return type

[**WatchRule**](WatchRule.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **422** | Validation failed against the MERGED rule — for example switching to a threshold condition on a rule that has no stored threshold.  |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

