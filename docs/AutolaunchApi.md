# AutolaunchApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createAutolaunchRule**](AutolaunchApi.md#createautolaunchrule) | **POST** /autolaunch-rules | Create an auto-launch rule (pre-approves a bounded, unattended spend) |
| [**deleteAutolaunchRule**](AutolaunchApi.md#deleteautolaunchrule) | **DELETE** /autolaunch-rules/{id} | Cancel an auto-launch rule |
| [**disarmAutolaunchRule**](AutolaunchApi.md#disarmautolaunchrule) | **PATCH** /autolaunch-rules/{id} | Disarm an auto-launch rule |
| [**getAutolaunchRule**](AutolaunchApi.md#getautolaunchrule) | **GET** /autolaunch-rules/{id} | Get an auto-launch rule |
| [**listAutolaunchRules**](AutolaunchApi.md#listautolaunchrules) | **GET** /autolaunch-rules | List auto-launch rules |



## createAutolaunchRule

> AutolaunchRule createAutolaunchRule(autolaunchRuleCreate, idempotencyKey)

Create an auto-launch rule (pre-approves a bounded, unattended spend)

Creates a standing, pre-approved purchase order. When the condition holds and the live price is at or under &#x60;max_price_per_hour&#x60;, the platform launches the frozen &#x60;spec&#x60; with no further confirmation from anyone — the customer is approving NOW for a purchase that happens LATER, while nobody is watching.  SCOPE. Requires the &#x60;autolaunch:write&#x60; scope, which is granted only EXPLICITLY. It is deliberately NOT covered by &#x60;full_access&#x60;, &#x60;standard&#x60; or &#x60;read_only&#x60;: &#x60;instances:write&#x60; is real-time authority, exercised with someone present, whereas this is a standing, frozen authorization that fires days later unattended. Treating them as the same authority class would have handed unattended spend authority to every key ever issued, including keys minted long before this resource existed. Most existing keys therefore receive 403 here; the correct response is to mint a key whose scopes map includes &#x60;{\&quot;autolaunch\&quot;: \&quot;write\&quot;}&#x60;, never to retry, to substitute a key, or to fall back to a watch rule.  CONSENT. &#x60;acknowledged_max_total_usd&#x60; is REQUIRED and must equal &#x60;max_price_per_hour × max_runtime_hours&#x60; to within one cent. It is the API-level expression of \&quot;a valid confirmation must come AFTER the price\&quot;: a caller that never computed the number cannot have shown it to anyone, and a caller that displayed a different number disagrees with what is about to be stored. Show the figure to the person approving the rule, then send it back.  TWO PRICES, TWO UNITS. &#x60;threshold&#x60; is the TRIGGER, in dollars per GPU-hour — the same unit the market chart and watch rules speak in. &#x60;max_price_per_hour&#x60; is the CEILING, in dollars per hour for the WHOLE instance. A 4-GPU rule triggering under $4.00/GPU-hr typically carries a $16.00/hr ceiling. Conflating them scales the customer\&#39;s spend authorization by their GPU count.  FROZEN SPEC. &#x60;spec&#x60; is the full create-instance body the rule replays, validated at creation with the same validation a live create runs, so a spec that could never launch is refused while a human is present rather than at 3 a.m. &#x60;spec.offering_id&#x60; is REJECTED — offering identity churns between catalog polls, so a pin produces a rule that can never fire, which is the worst outcome here because the customer believes a purchase is armed. &#x60;spec.auto_terminate_hours&#x60; is overwritten from &#x60;max_runtime_hours&#x60; and must not be used to widen the bound.  Organizations are limited to 10 active rules; the 422 names the limit. The organization spending limit still applies as a backstop at fire time — a launch must fit both its own ceiling and the org cap. 

### Example

```ts
import {
  Configuration,
  AutolaunchApi,
} from '@gpuai/sdk';
import type { CreateAutolaunchRuleRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new AutolaunchApi(config);

  const body = {
    // AutolaunchRuleCreate
    autolaunchRuleCreate: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CreateAutolaunchRuleRequest;

  try {
    const data = await api.createAutolaunchRule(body);
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
| **autolaunchRuleCreate** | [AutolaunchRuleCreate](AutolaunchRuleCreate.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**AutolaunchRule**](AutolaunchRule.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created |  -  |
| **403** | The API key lacks &#x60;autolaunch:write&#x60;. This scope is explicit-grant only and is NOT covered by &#x60;full_access&#x60;, &#x60;standard&#x60; or &#x60;read_only&#x60;; the problem detail names the scope and the fix.  |  -  |
| **422** | Validation failed — a missing or mismatched &#x60;acknowledged_max_total_usd&#x60;, a missing ceiling or runtime bound, an unknown condition kind, a non-canonical region, a missing threshold on a threshold condition, a &#x60;spec&#x60; that would not launch, a pinned &#x60;spec.offering_id&#x60;, or the active-rule limit already reached.  Also refused: anything that would arm a rule which can never succeed. A &#x60;gpu_model&#x60; (or &#x60;spec.gpu_type&#x60;) that is not a model we list; a &#x60;spec.gpu_type&#x60; that disagrees with the rule\&#39;s &#x60;gpu_model&#x60;; and a &#x60;spec.gpu_count&#x60; that is not a node shape a single launch can ask for (1, 2, 4 or 8 — 3, 5, 6 and 7 all pass an ordinary bounds check and none is a machine anyone rents).  NOT refused: a &#x60;max_price_per_hour&#x60; below &#x60;threshold&#x60; x &#x60;spec.gpu_count&#x60;. The two are in different units — &#x60;threshold&#x60; is per GPU-hour, the ceiling is for the WHOLE instance — but the launch aborts only above ceiling/gpu_count, a LOWER bar than the trigger, so such a rule waits and then buys once the market falls far enough. That shape is supported deliberately.  |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteAutolaunchRule

> deleteAutolaunchRule(id)

Cancel an auto-launch rule

Deletes the rule and withdraws its pre-approved spend cap immediately. Requires only the &#x60;autolaunch:read&#x60; scope, for the same reason the disarm PATCH does. Deleting an already-deleted rule returns 404. 

### Example

```ts
import {
  Configuration,
  AutolaunchApi,
} from '@gpuai/sdk';
import type { DeleteAutolaunchRuleRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new AutolaunchApi(config);

  const body = {
    // string
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies DeleteAutolaunchRuleRequest;

  try {
    const data = await api.deleteAutolaunchRule(body);
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


## disarmAutolaunchRule

> AutolaunchRule disarmAutolaunchRule(id, autolaunchRuleDisarm)

Disarm an auto-launch rule

Disarms a rule. The body must be exactly &#x60;{\&quot;enabled\&quot;: false}&#x60; and nothing else. Requires only the &#x60;autolaunch:read&#x60; scope — cancelling a standing spend authorization is deliberately never harder than holding one, so a key narrowed since it created a rule can still stop that rule.  This is the entire update surface, and the absence is the design. Changing a ceiling, a runtime bound, the targeting or the frozen spec is a DIFFERENT bounded purchase, so it requires deleting the rule and creating a new one through the consent gate. Re-arming is refused too: a fired rule consumed its one shot, so &#x60;{\&quot;enabled\&quot;: true}&#x60; would resurrect a purchase order that was already consented to and spent. 

### Example

```ts
import {
  Configuration,
  AutolaunchApi,
} from '@gpuai/sdk';
import type { DisarmAutolaunchRuleRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new AutolaunchApi(config);

  const body = {
    // string
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
    // AutolaunchRuleDisarm
    autolaunchRuleDisarm: ...,
  } satisfies DisarmAutolaunchRuleRequest;

  try {
    const data = await api.disarmAutolaunchRule(body);
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
| **autolaunchRuleDisarm** | [AutolaunchRuleDisarm](AutolaunchRuleDisarm.md) |  | |

### Return type

[**AutolaunchRule**](AutolaunchRule.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **422** | The body carried a key other than &#x60;enabled&#x60;, omitted &#x60;enabled&#x60;, or asked to re-arm the rule.  |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getAutolaunchRule

> AutolaunchRule getAutolaunchRule(id)

Get an auto-launch rule

Fetches one auto-launch rule, including the frozen launch spec. Requires the &#x60;autolaunch:read&#x60; scope. A rule belonging to another organization returns 404 — the same answer as an id that does not exist. 

### Example

```ts
import {
  Configuration,
  AutolaunchApi,
} from '@gpuai/sdk';
import type { GetAutolaunchRuleRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new AutolaunchApi(config);

  const body = {
    // string
    id: 38400000-8cf0-11bd-b23e-10b96e4ef00d,
  } satisfies GetAutolaunchRuleRequest;

  try {
    const data = await api.getAutolaunchRule(body);
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

[**AutolaunchRule**](AutolaunchRule.md)

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


## listAutolaunchRules

> AutolaunchRulePage listAutolaunchRules(cursor, limit)

List auto-launch rules

Lists this organization\&#39;s auto-launch rules. Requires the &#x60;autolaunch:read&#x60; scope, which &#x60;standard&#x60; and &#x60;full_access&#x60; keys carry. Rules belonging to other organizations are never returned, and rules created through the dashboard are included — the list is the organization\&#39;s, not the key\&#39;s. 

### Example

```ts
import {
  Configuration,
  AutolaunchApi,
} from '@gpuai/sdk';
import type { ListAutolaunchRulesRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new AutolaunchApi(config);

  const body = {
    // string (optional)
    cursor: cursor_example,
    // number (optional)
    limit: 56,
  } satisfies ListAutolaunchRulesRequest;

  try {
    const data = await api.listAutolaunchRules(body);
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

[**AutolaunchRulePage**](AutolaunchRulePage.md)

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

