# JobsApi

All URIs are relative to *https://api.gpu.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**cancelJob**](JobsApi.md#canceljob) | **POST** /jobs/{id}/cancel | Cancel a job |
| [**createJob**](JobsApi.md#createjob) | **POST** /jobs | Submit a job |
| [**getJob**](JobsApi.md#getjob) | **GET** /jobs/{id} | Get a job |
| [**getJobLogs**](JobsApi.md#getjoblogs) | **GET** /jobs/{id}/logs | Read a job\&#39;s output |
| [**getJobTelemetry**](JobsApi.md#getjobtelemetry) | **GET** /jobs/{id}/telemetry | Read a job\&#39;s GPU memory telemetry |
| [**getJobTrial**](JobsApi.md#getjobtrial) | **GET** /jobs/trial | Whether this organization\&#39;s first jobs are free |
| [**listJobGpuTypes**](JobsApi.md#listjobgputypes) | **GET** /jobs/gpu-types | List the GPU types a job can run on |
| [**listJobs**](JobsApi.md#listjobs) | **GET** /jobs | List jobs |



## cancelJob

> Job cancelJob(id, idempotencyKey)

Cancel a job

Cancels a job. A queued job is cancelled at once. A running job is stopped the next time its machine reports, within a few seconds, and shows &#x60;cancel_requested&#x60; until then. Cancelling a job that has already finished returns it unchanged. Requires the &#x60;instances:write&#x60; scope. 

### Example

```ts
import {
  Configuration,
  JobsApi,
} from '@gpuai/sdk';
import type { CancelJobRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new JobsApi(config);

  const body = {
    // string | The job id.
    id: id_example,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CancelJobRequest;

  try {
    const data = await api.cancelJob(body);
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
| **id** | `string` | The job id. | [Defaults to `undefined`] |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**Job**](Job.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The job after the cancel request. |  -  |
| **404** | The job does not exist or is not owned by the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createJob

> Job createJob(jobCreate, idempotencyKey)

Submit a job

Queues a batch job: a container image, a command, and the GPU it needs. The platform places it on a machine in your organization\&#39;s job pool, starting a machine when none has room, and terminates machines that have been empty for a few minutes. Requires the &#x60;instances:write&#x60; scope, because a job can start a machine.  Three opt-ins decide how the job is placed. &#x60;max_wait_seconds&#x60; lets the job wait for space on a machine you are already paying for before a new one is started. &#x60;allow_sharing&#x60; lets the job run on the same GPU as other jobs from your own organization. A GPU is never shared with another customer. &#x60;allow_restart&#x60; lets the platform stop and rerun the job, which sharing needs.  A job shares a GPU only when &#x60;allow_sharing&#x60; and &#x60;allow_restart&#x60; are both true and its memory is known, from &#x60;memory_hint_mb&#x60; or from the peaks of earlier finished jobs with the same name or image. Any other job gets a whole GPU.  Sharing is also limited by compute. Jobs share a GPU only while the sum of their expected compute duties (the share of time each keeps the GPU busy) stays at or under 100%, so two jobs that saturate the GPU never share one. A job\&#39;s duty comes from &#x60;compute_hint_pct&#x60; or from the measured utilization of earlier finished jobs with the same name or image. A job with neither counts as 100% and gets a GPU to itself until it has been measured.  The memory reservation is not a hard cap. A job that exits out of GPU memory, or that is stopped for outgrowing its reservation on a full GPU, is run again with a larger reservation, then with a whole GPU, up to &#x60;max_retries&#x60;. Every job gets a checkpoint directory that survives those reruns on the same machine.  Billing: the machines a job runs on are instances of your organization and are billed like any instance. &#x60;attributed_cost_usd&#x60; on the job is its share of that, for display.  Free trial: when this deployment runs one, an organization\&#39;s first jobs are free up to a cap (GET /jobs/trial). Their attributed cost is credited back to the balance as they run.  No balance: an organization with no balance is refused (402) unless the deployment runs the free trial for organizations with no balance and GET /jobs/trial reports &#x60;funding&#x60; \&quot;no_deposit\&quot;. Then the job runs on the trial with &#x60;trial_funded&#x60; true. When the trial credit is used the job is cancelled with the status reason \&quot;Stopped because your free Jobs trial credit ran out. Add credits to keep running jobs.\&quot; 

### Example

```ts
import {
  Configuration,
  JobsApi,
} from '@gpuai/sdk';
import type { CreateJobRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new JobsApi(config);

  const body = {
    // JobCreate
    jobCreate: ...,
    // string (optional)
    idempotencyKey: idempotencyKey_example,
  } satisfies CreateJobRequest;

  try {
    const data = await api.createJob(body);
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
| **jobCreate** | [JobCreate](JobCreate.md) |  | |
| **idempotencyKey** | `string` |  | [Optional] [Defaults to `undefined`] |

### Return type

[**Job**](Job.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created |  * GPUAI-Hint - Advisory only. Sent while the organization\&#39;s first jobs are free (GET /jobs/trial), e.g. \&quot;Your first jobs are free, up to $10. We credit back what they cost as they run.\&quot; For a job that runs on the trial with no balance it says the job stops when the trial credit is used. <br>  |
| **402** | The organization has no balance and the job cannot run on the free trial (the trial is off, used, or at its limit for today, or the person already used it). The detail says which. Add credits, then submit again.  |  -  |
| **422** | Validation failed. The detail names the field: a missing image or command, an unknown field, an unknown &#x60;gpu_type&#x60;, neither &#x60;gpu_type&#x60; nor &#x60;min_vram_gb&#x60;, a memory hint larger than the GPU, an environment variable name starting with &#x60;GPUAI_&#x60;, or a value out of range.  |  -  |
| **429** | Rate limited, or the organization already has the maximum number of queued and running jobs.  |  -  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getJob

> Job getJob(id)

Get a job

Returns one job with its attempts. Requires the &#x60;instances:read&#x60; scope. 

### Example

```ts
import {
  Configuration,
  JobsApi,
} from '@gpuai/sdk';
import type { GetJobRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new JobsApi(config);

  const body = {
    // string | The job id.
    id: id_example,
  } satisfies GetJobRequest;

  try {
    const data = await api.getJob(body);
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
| **id** | `string` | The job id. | [Defaults to `undefined`] |

### Return type

[**Job**](Job.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | The job does not exist or is not owned by the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getJobLogs

> JobLogs getJobLogs(id, after, limit)

Read a job\&#39;s output

Returns the job\&#39;s combined standard output and standard error, in chunks, across all attempts. Pass the &#x60;next_after&#x60; of one response as &#x60;after&#x60; on the next to read on from there. Output is uploaded every few seconds while the job runs, and stored output is capped at about 8 MB per attempt. Requires the &#x60;instances:read&#x60; scope. 

### Example

```ts
import {
  Configuration,
  JobsApi,
} from '@gpuai/sdk';
import type { GetJobLogsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new JobsApi(config);

  const body = {
    // string | The job id.
    id: id_example,
    // number | Return chunks after this chunk id. (optional)
    after: 789,
    // number | Maximum number of chunks to return. (optional)
    limit: 56,
  } satisfies GetJobLogsRequest;

  try {
    const data = await api.getJobLogs(body);
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
| **id** | `string` | The job id. | [Defaults to `undefined`] |
| **after** | `number` | Return chunks after this chunk id. | [Optional] [Defaults to `0`] |
| **limit** | `number` | Maximum number of chunks to return. | [Optional] [Defaults to `100`] |

### Return type

[**JobLogs**](JobLogs.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | The job does not exist or is not owned by the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getJobTelemetry

> JobTelemetry getJobTelemetry(id)

Read a job\&#39;s GPU memory telemetry

Returns the job\&#39;s peak GPU memory, its reservation, and up to the 720 most recent memory points. The machine samples every 2 seconds and stores one point per report, the highest sample in that window. Points are kept for 30 days. Requires the &#x60;instances:read&#x60; scope. 

### Example

```ts
import {
  Configuration,
  JobsApi,
} from '@gpuai/sdk';
import type { GetJobTelemetryRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new JobsApi(config);

  const body = {
    // string | The job id.
    id: id_example,
  } satisfies GetJobTelemetryRequest;

  try {
    const data = await api.getJobTelemetry(body);
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
| **id** | `string` | The job id. | [Defaults to `undefined`] |

### Return type

[**JobTelemetry**](JobTelemetry.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **404** | The job does not exist or is not owned by the caller\&#39;s organization. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getJobTrial

> JobTrial getJobTrial()

Whether this organization\&#39;s first jobs are free

Reports the Jobs free trial for this organization. When the deployment runs one, an organization\&#39;s first jobs are free up to &#x60;cap_cents&#x60;: the cost attributed to its jobs is credited back to its balance as they run, until the credits reach the cap. One trial per organization, for organizations that had not used Jobs before the trial started. &#x60;enabled&#x60; is false when there is no trial. Requires the &#x60;instances:read&#x60; scope. 

### Example

```ts
import {
  Configuration,
  JobsApi,
} from '@gpuai/sdk';
import type { GetJobTrialRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new JobsApi(config);

  try {
    const data = await api.getJobTrial();
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

[**JobTrial**](JobTrial.md)

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


## listJobGpuTypes

> JobGpuTypes listJobGpuTypes()

List the GPU types a job can run on

Returns the GPU types the suppliers that run jobs rent as a one-GPU machine, smallest memory first. A type is listed when one of them offered it in the last 7 days, in stock or not. &#x60;available_now&#x60; says whether one has such a machine to rent now, and &#x60;price_per_gpu_hour&#x60; is the cheapest retail price of it at that read (a guide, not a quote: the launch prices it again). When &#x60;complete&#x60; is true, &#x60;POST /jobs&#x60; refuses any other &#x60;gpu_type&#x60; with a 422 (and a &#x60;min_vram_gb&#x60; larger than every listed type), instead of queueing a job that could never start. When &#x60;complete&#x60; is false the list may be partial or empty, and a job for any known GPU model is accepted and waits for a machine. Requires the &#x60;instances:read&#x60; scope. 

### Example

```ts
import {
  Configuration,
  JobsApi,
} from '@gpuai/sdk';
import type { ListJobGpuTypesRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new JobsApi(config);

  try {
    const data = await api.listJobGpuTypes();
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

[**JobGpuTypes**](JobGpuTypes.md)

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


## listJobs

> JobPage listJobs(status, cursor, limit)

List jobs

Lists this organization\&#39;s jobs, newest first. Requires the &#x60;instances:read&#x60; scope. Jobs belonging to other organizations are never returned. 

### Example

```ts
import {
  Configuration,
  JobsApi,
} from '@gpuai/sdk';
import type { ListJobsRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new JobsApi(config);

  const body = {
    // 'queued' | 'assigned' | 'running' | 'succeeded' | 'failed' | 'cancelled' | Only return jobs in this status. (optional)
    status: status_example,
    // string (optional)
    cursor: cursor_example,
    // number (optional)
    limit: 56,
  } satisfies ListJobsRequest;

  try {
    const data = await api.listJobs(body);
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
| **status** | `queued`, `assigned`, `running`, `succeeded`, `failed`, `cancelled` | Only return jobs in this status. | [Optional] [Defaults to `undefined`] [Enum: queued, assigned, running, succeeded, failed, cancelled] |
| **cursor** | `string` |  | [Optional] [Defaults to `undefined`] |
| **limit** | `number` |  | [Optional] [Defaults to `50`] |

### Return type

[**JobPage**](JobPage.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **422** | Validation failed, such as an unknown status or an invalid cursor. |  -  |
| **429** | Rate limit exceeded (RFC 7807). Retry-After header indicates seconds to wait. |  * Retry-After - Seconds the client should wait before retrying. <br>  |
| **0** | Error response (RFC 7807) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

