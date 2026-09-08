# MarketApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getMarketHistory**](MarketApi.md#getmarkethistory) | **GET** /market-history | Get a GPU\&#39;s price and availability over time |



## getMarketHistory

> MarketHistoryResponse getMarketHistory(gpuModel, region, capacityClass, bucket, from, to)

Get a GPU\&#39;s price and availability over time

Returns GPU.ai\&#39;s own price and obtainable capacity for one GPU model over a window, at 15-minute or daily resolution. Requires the &#x60;market:read&#x60; scope (or &#x60;full_access&#x60;).  THE NULL CONTRACT. &#x60;price_per_gpu_hour&#x60; and &#x60;available_count&#x60; are nullable, and the two states are different facts that must not be collapsed:  * a real &#x60;0&#x60; means we sampled that bucket and the market was sold out; * &#x60;null&#x60; means we did NOT sample that bucket — a failed poll, a skipped cycle, an incident on our side. It says nothing about supply.  The response materializes the full bucket grid across the window, so a gap has visible width. Do not interpolate across a null: that asserts a continuity the data does not have, and reading one as a zero reports our own outages as supplier stockouts.  PER-GPU NORMALIZATION. &#x60;price_per_gpu_hour&#x60; is always a per-GPU rate. When it was divided out of a whole-node price, &#x60;node_price_per_hour&#x60; and &#x60;gpu_count&#x60; are present and describe that derivation; they are absent for single-GPU capacity. A per-GPU figure presented without that context implies single-GPU rentability that whole-node capacity does not offer.  WINDOW CAPS. &#x60;bucket&#x3D;1d&#x60; is capped at 365 days (the retention window). &#x60;bucket&#x3D;15m&#x60; is capped at 90 days when BOTH &#x60;region&#x60; and &#x60;capacity_class&#x60; are supplied, and at 31 days when either is omitted, because an unscoped 15-minute series scans every region and class in every bucket. An over-wide window is a 400 naming the cap and both escapes, never a silent truncation.  This series carries no upstream supplier identity of any kind: the price is GPU.ai\&#39;s own floor and the count is an aggregate. 

### Example

```ts
import {
  Configuration,
  MarketApi,
} from '@gpuai/sdk';
import type { GetMarketHistoryRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new MarketApi(config);

  const body = {
    // string | GPU model to chart, e.g. \"H100\". Required — it is the leading column of the lookup index.
    gpuModel: gpuModel_example,
    // string | Canonical region to narrow the series to. Omit to MERGE every region rather than to filter on the empty string. (optional)
    region: region_example,
    // 'secure' | 'community' | Capacity class to narrow the series to. Omit to merge both. (optional)
    capacityClass: capacityClass_example,
    // '15m' | '1d' | Resolution. Only these two values are accepted: the series cannot be returned finer than it was stored. (optional)
    bucket: bucket_example,
    // Date | Start of the window (RFC3339). Defaults to 7 days before `to`. (optional)
    from: 2013-10-20T19:20:30+01:00,
    // Date | End of the window (RFC3339). Defaults to now; a future value is clamped to now, since no bucket can exist for a time that has not happened. (optional)
    to: 2013-10-20T19:20:30+01:00,
  } satisfies GetMarketHistoryRequest;

  try {
    const data = await api.getMarketHistory(body);
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
| **gpuModel** | `string` | GPU model to chart, e.g. \&quot;H100\&quot;. Required — it is the leading column of the lookup index. | [Defaults to `undefined`] |
| **region** | `string` | Canonical region to narrow the series to. Omit to MERGE every region rather than to filter on the empty string. | [Optional] [Defaults to `undefined`] |
| **capacityClass** | `secure`, `community` | Capacity class to narrow the series to. Omit to merge both. | [Optional] [Defaults to `undefined`] [Enum: secure, community] |
| **bucket** | `15m`, `1d` | Resolution. Only these two values are accepted: the series cannot be returned finer than it was stored. | [Optional] [Defaults to `&#39;15m&#39;`] [Enum: 15m, 1d] |
| **from** | `Date` | Start of the window (RFC3339). Defaults to 7 days before &#x60;to&#x60;. | [Optional] [Defaults to `undefined`] |
| **to** | `Date` | End of the window (RFC3339). Defaults to now; a future value is clamped to now, since no bucket can exist for a time that has not happened. | [Optional] [Defaults to `undefined`] |

### Return type

[**MarketHistoryResponse**](MarketHistoryResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **400** | Validation failed — a missing &#x60;gpu_model&#x60;, a non-canonical region, an unknown &#x60;capacity_class&#x60; or &#x60;bucket&#x60;, a non-RFC3339 timestamp, a &#x60;from&#x60; that is not before &#x60;to&#x60;, or a window wider than the cap for the requested resolution and scope. The detail names the cap and both ways to stay under it.  |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

