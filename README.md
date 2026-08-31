# @gpuai/sdk@0.3.2

A TypeScript SDK client for the api.gpu.ai API.

## Usage

First, install the SDK from npm.

```bash
npm install @gpuai/sdk --save
```

Next, try it out.


```ts
import {
  Configuration,
  BillingApi,
} from '@gpuai/sdk';
import type { CreateCryptoDepositOperationRequest } from '@gpuai/sdk';

async function example() {
  console.log("🚀 Testing @gpuai/sdk SDK...");
  const config = new Configuration({ 
    // Configure HTTP bearer authorization: bearerAuth
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new BillingApi(config);

  const body = {
    // CreateCryptoDepositRequest
    createCryptoDepositRequest: ...,
  } satisfies CreateCryptoDepositOperationRequest;

  try {
    const data = await api.createCryptoDeposit(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```


## Documentation

### API Endpoints

All URIs are relative to *https://api.gpu.ai/v1*

| Class | Method | HTTP request | Description
| ----- | ------ | ------------ | -------------
*BillingApi* | [**createCryptoDeposit**](docs/BillingApi.md#createcryptodepositoperation) | **POST** /billing/deposits/crypto | Create a stablecoin deposit
*BillingApi* | [**getDeposit**](docs/BillingApi.md#getdeposit) | **GET** /billing/deposits/{id} | Get one stablecoin deposit
*BillingApi* | [**getSpendingLimit**](docs/BillingApi.md#getspendinglimit) | **GET** /billing/spending-limit | Get the org spending limit
*BillingApi* | [**listDeposits**](docs/BillingApi.md#listdeposits) | **GET** /billing/deposits | List stablecoin deposits
*BillingApi* | [**updateSpendingLimit**](docs/BillingApi.md#updatespendinglimitoperation) | **PUT** /billing/spending-limit | Set the org spending limit
*CommunityApi* | [**delistCommunityMachine**](docs/CommunityApi.md#delistcommunitymachine) | **POST** /community/machines/{id}/delist | Delist a Community Cloud machine
*CommunityApi* | [**enableCommunitySupplier**](docs/CommunityApi.md#enablecommunitysupplier) | **POST** /community/suppliers | Enable the Community Cloud supplier role
*CommunityApi* | [**getCommunitySupplierMe**](docs/CommunityApi.md#getcommunitysupplierme) | **GET** /community/suppliers/me | Get the caller\&#39;s Community Cloud supplier
*CommunityApi* | [**listCommunityMachines**](docs/CommunityApi.md#listcommunitymachines) | **GET** /community/machines | List your Community Cloud machines
*CommunityApi* | [**reclaimCommunityMachine**](docs/CommunityApi.md#reclaimcommunitymachine) | **POST** /community/machines/{id}/reclaim | Reclaim a spot-tier Community Cloud machine
*CommunityApi* | [**registerCommunityMachine**](docs/CommunityApi.md#registercommunitymachineoperation) | **POST** /community/machines | Register a Community Cloud machine
*EnvironmentsApi* | [**getEnvironments**](docs/EnvironmentsApi.md#getenvironments) | **GET** /environments | List launch environments (no auth required)
*FineTuningApi* | [**cancelFineTuningJob**](docs/FineTuningApi.md#cancelfinetuningjob) | **POST** /fine_tuning/jobs/{id}/cancel | Cancel a fine-tuning job (OpenAI-compatible)
*FineTuningApi* | [**createFile**](docs/FineTuningApi.md#createfile) | **POST** /files | Upload a fine-tuning dataset file (OpenAI-compatible)
*FineTuningApi* | [**createFineTuningJob**](docs/FineTuningApi.md#createfinetuningjoboperation) | **POST** /fine_tuning/jobs | Create a managed fine-tuning job (OpenAI-compatible)
*FineTuningApi* | [**getFineTuningJob**](docs/FineTuningApi.md#getfinetuningjob) | **GET** /fine_tuning/jobs/{id} | Retrieve a fine-tuning job (OpenAI-compatible)
*FineTuningApi* | [**listFineTuningJobEvents**](docs/FineTuningApi.md#listfinetuningjobevents) | **GET** /fine_tuning/jobs/{id}/events | List fine-tuning job events (OpenAI-compatible)
*FineTuningApi* | [**listFineTuningJobs**](docs/FineTuningApi.md#listfinetuningjobs) | **GET** /fine_tuning/jobs | List fine-tuning jobs (OpenAI-compatible)
*GpuTypesApi* | [**listGpuTypes**](docs/GpuTypesApi.md#listgputypes) | **GET** /gpu-types | List available GPU types (no auth required)
*InferenceApi* | [**cancelVideo**](docs/InferenceApi.md#cancelvideo) | **POST** /videos/{id}/cancel | Cancel a video generation job
*InferenceApi* | [**createChatCompletion**](docs/InferenceApi.md#createchatcompletion) | **POST** /chat/completions | Create a chat completion (OpenAI-compatible)
*InferenceApi* | [**createImage**](docs/InferenceApi.md#createimage) | **POST** /images/generations | Create image (OpenAI-compatible)
*InferenceApi* | [**createVideo**](docs/InferenceApi.md#createvideo) | **POST** /videos | Create a video generation job (async)
*InferenceApi* | [**getModel**](docs/InferenceApi.md#getmodel) | **GET** /models/{id} | Get a specific model (OpenAI-compatible)
*InferenceApi* | [**getVideo**](docs/InferenceApi.md#getvideo) | **GET** /videos/{id} | Get a video generation job
*InferenceApi* | [**getVideoContent**](docs/InferenceApi.md#getvideocontent) | **GET** /videos/{id}/content | Download a completed video artifact
*InferenceApi* | [**listModels**](docs/InferenceApi.md#listmodels) | **GET** /models | List available models (OpenAI-compatible)
*InferenceApi* | [**listVideos**](docs/InferenceApi.md#listvideos) | **GET** /videos | List video generation jobs
*InstancesApi* | [**createInstance**](docs/InstancesApi.md#createinstanceoperation) | **POST** /instances | Create an instance (async — returns 202 + Operation-Id header)
*InstancesApi* | [**deleteInstance**](docs/InstancesApi.md#deleteinstance) | **DELETE** /instances/{id} | Terminate an instance (idempotent)
*InstancesApi* | [**getInstance**](docs/InstancesApi.md#getinstance) | **GET** /instances/{id} | Get an instance
*InstancesApi* | [**listInstances**](docs/InstancesApi.md#listinstances) | **GET** /instances | List instances
*InstancesApi* | [**updateInstance**](docs/InstancesApi.md#updateinstanceoperation) | **PATCH** /instances/{id} | Update an instance (rename only in v1)
*MetaApi* | [**getHealth**](docs/MetaApi.md#gethealth) | **GET** /health | Liveness probe
*MetaApi* | [**getOpenApiSpec**](docs/MetaApi.md#getopenapispec) | **GET** /openapi.json | OpenAPI 3.1 specification
*OperationsApi* | [**getOperation**](docs/OperationsApi.md#getoperation) | **GET** /operations/{id} | Get an async operation status
*PricingApi* | [**listPricing**](docs/PricingApi.md#listpricing) | **GET** /pricing | List pricing per GPU type + region (no auth required)
*SshKeysApi* | [**createSshKey**](docs/SshKeysApi.md#createsshkeyoperation) | **POST** /ssh-keys | Create an SSH key
*SshKeysApi* | [**deleteSshKey**](docs/SshKeysApi.md#deletesshkey) | **DELETE** /ssh-keys/{id} | Delete an SSH key (idempotent — 404 on already-gone per D-07)
*SshKeysApi* | [**getSshKey**](docs/SshKeysApi.md#getsshkey) | **GET** /ssh-keys/{id} | Get an SSH key
*SshKeysApi* | [**listSshKeys**](docs/SshKeysApi.md#listsshkeys) | **GET** /ssh-keys | List SSH keys
*TemplatesApi* | [**getTemplate**](docs/TemplatesApi.md#gettemplate) | **GET** /templates/{id} | Get one deployable application template
*TemplatesApi* | [**listTemplates**](docs/TemplatesApi.md#listtemplates) | **GET** /templates | List deployable application templates
*UsageApi* | [**listUsage**](docs/UsageApi.md#listusage) | **GET** /usage | Time-bucketed usage
*WebhooksApi* | [**createWebhookEndpoint**](docs/WebhooksApi.md#createwebhookendpointoperation) | **POST** /webhook-endpoints | Create a webhook endpoint
*WebhooksApi* | [**deleteWebhookEndpoint**](docs/WebhooksApi.md#deletewebhookendpoint) | **DELETE** /webhook-endpoints/{id} | Delete a webhook endpoint
*WebhooksApi* | [**getWebhookEndpoint**](docs/WebhooksApi.md#getwebhookendpoint) | **GET** /webhook-endpoints/{id} | Get a webhook endpoint
*WebhooksApi* | [**listWebhookEndpoints**](docs/WebhooksApi.md#listwebhookendpoints) | **GET** /webhook-endpoints | List webhook endpoints


### Models

- [ChatChoice](docs/ChatChoice.md)
- [ChatCompletionRequest](docs/ChatCompletionRequest.md)
- [ChatCompletionResponse](docs/ChatCompletionResponse.md)
- [ChatMessage](docs/ChatMessage.md)
- [CommunityMachine](docs/CommunityMachine.md)
- [CommunityMachineDelistResult](docs/CommunityMachineDelistResult.md)
- [CommunityMachineRegistration](docs/CommunityMachineRegistration.md)
- [CommunitySupplier](docs/CommunitySupplier.md)
- [CreateCryptoDepositRequest](docs/CreateCryptoDepositRequest.md)
- [CreateFineTuningJobRequest](docs/CreateFineTuningJobRequest.md)
- [CreateFineTuningJobRequestGpuai](docs/CreateFineTuningJobRequestGpuai.md)
- [CreateFineTuningJobRequestMethod](docs/CreateFineTuningJobRequestMethod.md)
- [CreateFineTuningJobRequestMethodLora](docs/CreateFineTuningJobRequestMethodLora.md)
- [CreateInstanceRequest](docs/CreateInstanceRequest.md)
- [CreateSshKeyRequest](docs/CreateSshKeyRequest.md)
- [CreateWebhookEndpointRequest](docs/CreateWebhookEndpointRequest.md)
- [CryptoDeposit](docs/CryptoDeposit.md)
- [Environments](docs/Environments.md)
- [FileObject](docs/FileObject.md)
- [FineTuningJob](docs/FineTuningJob.md)
- [FineTuningJobError](docs/FineTuningJobError.md)
- [FineTuningJobEvent](docs/FineTuningJobEvent.md)
- [FineTuningJobEventList](docs/FineTuningJobEventList.md)
- [FineTuningJobList](docs/FineTuningJobList.md)
- [FineTuningJobMethod](docs/FineTuningJobMethod.md)
- [FrameworkVersion](docs/FrameworkVersion.md)
- [GPUType](docs/GPUType.md)
- [GPUTypePage](docs/GPUTypePage.md)
- [GetHealth200Response](docs/GetHealth200Response.md)
- [ImagesGenerationsRequest](docs/ImagesGenerationsRequest.md)
- [ImagesResponse](docs/ImagesResponse.md)
- [ImagesResponseDataInner](docs/ImagesResponseDataInner.md)
- [ImagesResponseUsage](docs/ImagesResponseUsage.md)
- [IncludeItem](docs/IncludeItem.md)
- [Instance](docs/Instance.md)
- [InstanceConnection](docs/InstanceConnection.md)
- [InstancePage](docs/InstancePage.md)
- [ListCommunityMachines200Response](docs/ListCommunityMachines200Response.md)
- [ListDeposits200Response](docs/ListDeposits200Response.md)
- [Model](docs/Model.md)
- [ModelList](docs/ModelList.md)
- [ModelParametersInner](docs/ModelParametersInner.md)
- [ModelPricing](docs/ModelPricing.md)
- [OpenAIErrorEnvelope](docs/OpenAIErrorEnvelope.md)
- [OpenAIErrorEnvelopeError](docs/OpenAIErrorEnvelopeError.md)
- [Operation](docs/Operation.md)
- [OperationError](docs/OperationError.md)
- [OperationResult](docs/OperationResult.md)
- [Pricing](docs/Pricing.md)
- [PricingPage](docs/PricingPage.md)
- [Problem](docs/Problem.md)
- [RegisterCommunityMachineRequest](docs/RegisterCommunityMachineRequest.md)
- [SSHKey](docs/SSHKey.md)
- [SSHKeyPage](docs/SSHKeyPage.md)
- [SpendingLimit](docs/SpendingLimit.md)
- [StreamOptions](docs/StreamOptions.md)
- [SupplierMachineView](docs/SupplierMachineView.md)
- [Template](docs/Template.md)
- [TemplateEnvInner](docs/TemplateEnvInner.md)
- [TemplateList](docs/TemplateList.md)
- [TemplatePortsInner](docs/TemplatePortsInner.md)
- [UpdateInstanceRequest](docs/UpdateInstanceRequest.md)
- [UpdateSpendingLimitRequest](docs/UpdateSpendingLimitRequest.md)
- [Usage](docs/Usage.md)
- [UsageBucket](docs/UsageBucket.md)
- [UsagePage](docs/UsagePage.md)
- [VMImage](docs/VMImage.md)
- [VideoCreateRequest](docs/VideoCreateRequest.md)
- [VideoJob](docs/VideoJob.md)
- [VideoList](docs/VideoList.md)
- [WebhookEndpoint](docs/WebhookEndpoint.md)
- [WebhookEndpointPage](docs/WebhookEndpointPage.md)

### Authorization


Authentication schemes defined for the API:
<a id="bearerAuth"></a>
#### bearerAuth


- **Type**: HTTP Bearer Token authentication (gpuai_live_<24-base62>)

## About

This TypeScript SDK client supports the [Fetch API](https://fetch.spec.whatwg.org/)
and is automatically generated by the
[OpenAPI Generator](https://openapi-generator.tech) project:

- API version: `1.0.0`
- Package version: `0.3.2`
- Generator version: `7.24.0`
- Build package: `org.openapitools.codegen.languages.TypeScriptFetchClientCodegen`

The generated npm module supports the following:

- Environments
  * Node.js
  * Webpack
  * Browserify
- Language levels
  * ES5 - you must have a Promises/A+ library installed
  * ES6
- Module systems
  * CommonJS
  * ES6 module system


## Development

### Building

To build the TypeScript source code, you need to have Node.js and npm installed.
After cloning the repository, navigate to the project directory and run:

```bash
npm install
npm run build
```

### Publishing

Once you've built the package, you can publish it to npm:

```bash
npm publish
```

## License

[Apache-2.0]()
