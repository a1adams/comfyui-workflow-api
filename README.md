# ComfyUI API Options: 7 Ways to Serve a Workflow, Compared (2026)

These 7 ComfyUI API options were checked against vendor docs on 11 October 2026 and ranked by how little you host and operate to put a workflow behind one API call. Wireflow is first because there is no GPU or ComfyUI install to run, but it does not run ComfyUI graphs, so you rebuild the workflow there. The other 6 run your own ComfyUI graph.

1. **Wireflow**: Best overall for an API with no ComfyUI install to run, a hosted node canvas where you rebuild the workflow
2. **Comfy Cloud API**: Best for running your exported graph on the official hosted service, with a paid plan and an API key
3. **ComfyDeploy**: Best for teams that share one managed ComfyUI environment, with each deployment called by ID
4. **Replicate cog-comfyui**: Best for sending a graph to a shared hosted model, with a Cog fork when you need control
5. **RunPod worker-comfyui**: Best for your own serverless endpoint with a webhook, built from a Docker image
6. **SaladCloud comfyui-api**: Best for a stateless wrapper inside your own container, with signed webhooks
7. **comfy-api-proxy**: Best for the cloud contract on a machine you already run, a local proxy in front of ComfyUI

We build Wireflow, and entry 1 is the only one here that does not run ComfyUI, so read it with both facts in mind. [Wireflow's ComfyUI alternative page](https://www.wireflow.ai/comfyui-alternative) says plainly what does not transfer, and every other entry links to its own docs or README so each line can be checked.

The tables below are generated from [`data/tools.json`](data/tools.json). Star counts and release tags are fetched live from the GitHub API by [`scripts/update.js`](scripts/update.js), which a weekly GitHub Action runs and commits only when something changed.

<!-- LAST-CHECKED:START -->
Live repository data last checked **2026-10-13** by [`scripts/update.js`](scripts/update.js), which runs weekly via GitHub Actions.
<!-- LAST-CHECKED:END -->

Maintained by [a1adams](https://github.com/a1adams). Corrections are welcome, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contents

- [The data](#the-data)
- [Capability scores](#capability-scores)
- [Comparison table](#comparison-table)
- [The tools](#the-tools)
  - [Wireflow](#1-wireflow)
  - [Comfy Cloud API](#2-comfy-cloud-api)
  - [ComfyDeploy](#3-comfydeploy)
  - [Replicate cog-comfyui](#4-replicate-cog-comfyui)
  - [RunPod worker-comfyui](#5-runpod-worker-comfyui)
  - [SaladCloud comfyui-api](#6-saladcloud-comfyui-api)
  - [comfy-api-proxy](#7-comfy-api-proxy)
- [ComfyUI, the baseline](#comfyui-the-baseline)
- [What each check means](#what-each-check-means)
- [How this list is maintained](#how-this-list-is-maintained)
- [FAQ](#faq)
- [Contributing](#contributing)
- [License](#license)

## The data

One row per tool, one column per thing people actually check before committing. Columns with nothing verified behind them are dropped rather than filled with guesses.

<!-- DATA-TABLE:START -->
| Tool | REST API | Free tier | Pricing | Open-source SDK / MCP |
|---|---|---|---|---|
| **[Wireflow](#1-wireflow)** | Yes | [check](https://www.wireflow.ai/pricing) | [pricing](https://www.wireflow.ai/pricing) | n/a |
| **[Comfy Cloud API](#2-comfy-cloud-api)** | Yes | [check](https://comfy.org/pricing/) | [pricing](https://comfy.org/pricing/) | [Comfy-Org/comfy-python-sdk](https://github.com/Comfy-Org/comfy-python-sdk), 15 ★, v0.5.0 |
| **[ComfyDeploy](#3-comfydeploy)** | Yes | n/a | n/a | [comfy-deploy/comfydeploy](https://github.com/comfy-deploy/comfydeploy), 458 ★, pushed 2025-09-19 |
| **[Replicate cog-comfyui](#4-replicate-cog-comfyui)** | Yes | [check](https://replicate.com/pricing) | [pricing](https://replicate.com/pricing) | [replicate/cog-comfyui](https://github.com/replicate/cog-comfyui), 770 ★, pushed 2025-11-03 |
| **[RunPod worker-comfyui](#5-runpod-worker-comfyui)** | Yes | [check](https://www.runpod.io/pricing) | [pricing](https://www.runpod.io/pricing) | [runpod-workers/worker-comfyui](https://github.com/runpod-workers/worker-comfyui), 749 ★, 5.11.0 |
| **[SaladCloud comfyui-api](#6-saladcloud-comfyui-api)** | Yes | Yes | n/a | [SaladTechnologies/comfyui-api](https://github.com/SaladTechnologies/comfyui-api), 455 ★, 1.19.2 |
| **[comfy-api-proxy](#7-comfy-api-proxy)** | Yes | Yes | n/a | [Comfy-Org/comfy-api-proxy](https://github.com/Comfy-Org/comfy-api-proxy), 13 ★, v0.1.6 |
<!-- DATA-TABLE:END -->

## Capability scores

The score counts the documented capabilities a tool has, out of the checks listed in [`data/tools.json`](data/tools.json) under `capabilityChecks`. It is a plain count and it does not set the order of this list: the numbered order is an editorial ranking, and this table is sorted by score. The checks and every answer are in the file, so each cell can be checked. Disagree with a cell? Open an issue naming the tool, the check and the evidence.

<!-- CAPABILITY-SCORES:START -->
| Tool | Runs your ComfyUI graph | Custom nodes you choose | Your own models | Completion webhook | GPUs hosted for you | Score |
|------|---|---|---|---|---|-------|
| **[ComfyDeploy](#3-comfydeploy)** | ✅ | ✅ | ✅ | ✅ | ✅ | **5/5** |
| **[Replicate cog-comfyui](#4-replicate-cog-comfyui)** | ✅ | ✅ | ✅ | ✅ | ✅ | **5/5** |
| **[RunPod worker-comfyui](#5-runpod-worker-comfyui)** | ✅ | ✅ | ✅ | ✅ | ✅ | **5/5** |
| **[SaladCloud comfyui-api](#6-saladcloud-comfyui-api)** | ✅ | ✅ | ✅ | ✅ | ❌ | **4/5** |
| **[Comfy Cloud API](#2-comfy-cloud-api)** | ✅ | ❌ | ✅ | ❌ | ✅ | **3/5** |
| **[comfy-api-proxy](#7-comfy-api-proxy)** | ✅ | ✅ | ✅ | n/a | ❌ | **3/5** |
| **[Wireflow](#1-wireflow)** | ❌ | ❌ | ❌ | ✅ | ✅ | **2/5** |
<!-- CAPABILITY-SCORES:END -->

## Comparison table

| Tool | Best for | Pricing basis | Request carries | Job finished signal |
|---|---|---|---|---|
| **Wireflow** | An API with no ComfyUI to run | Credits per generation | Saved workflow ID and inputs | Webhook or polling |
| **Comfy Cloud API** | The official hosted service | Paid Comfy Cloud subscription | API-format graph | Polling, with an SSE stream |
| **ComfyDeploy** | Teams sharing one environment | Not published | Deployment ID and inputs | Webhook or Get Run |
| **Replicate cog-comfyui** | A shared hosted model | Free repo, Replicate rates to run | API-format graph | Replicate webhook or polling |
| **RunPod worker-comfyui** | Your own serverless endpoint | Free repo, RunPod GPU rates | API-format graph | Webhook, status poll or sync call |
| **SaladCloud comfyui-api** | A wrapper in your own container | Free, MIT licence | API-format graph | Webhook or sync response |
| **comfy-api-proxy** | The cloud contract, self-hosted | Free, MIT licence | API-format graph | Polling, with an SSE stream |

From each vendor's own docs, OpenAPI spec or README, checked on 2026-10-11. Prices are not typed in this table, so follow the pricing links in the data table.

## The tools

### 1. Wireflow

*Best overall for an API with no ComfyUI install to run*

![Wireflow screenshot](https://assets.wireflow.ai/competitors/wireflow-70f47ccd9660.png?v=r5)

- **What it is:** [Wireflow](https://www.wireflow.ai/) is a platform where ad teams and AI agents build and rerun creative on a shared node board. It runs hosted models on a browser canvas, so there is no GPU, model download or local Python environment to manage, and it is a separate platform, not ComfyUI running in a browser.
- **Best for:** Teams that want a node workflow behind an API and would rather rebuild the graph once than operate ComfyUI, its custom nodes and a GPU.
- **Pricing basis:** Credits per generation, set by the model you run, and one credit is US$0.01. Starter is US$24 a month with 1,600 credits, and the free plan builds up to 5 workflows but cannot run generations. The [Wireflow pricing page](https://www.wireflow.ai/pricing) lists a credit price for every model (October 2026).
- **Standout:** There is nothing to deploy. You send only the input values to `POST /api/v1/workflows/{id}/run` and the saved workflow runs, as [the run endpoint docs](https://www.wireflow.ai/docs/api/run) show. Add a webhook block and Wireflow POSTs the result to your URL when the run finishes, retried for up to 12 attempts.
- **Limit:** Wireflow does not run ComfyUI graphs. ComfyUI workflow JSON, custom Python nodes and local checkpoints do not transfer, so you rebuild the workflow from Wireflow's own nodes and hosted models, and it needs an internet connection. There is no official SDK, so you call the REST API with any HTTP client.
- **API or automation:** The REST API lives at `https://www.wireflow.ai/api/v1` and takes an API key as a Bearer token, and a new key starts read-only until you add scopes. If you lack credits, the run call returns a 402 with the credit cost of each node, and a model that fails is not charged. Wireflow is also a Claude connector over MCP.
- **Sources:** the Wireflow pages linked in this entry, plus the API overview, webhooks and executions docs, checked 2026-10-11.
- **Links:**
  - [Wireflow ComfyUI alternative page](https://www.wireflow.ai/comfyui-alternative)
  - [Docs](https://www.wireflow.ai/docs/api/overview)

Build on Wireflow when the result matters more than the exact graph, for example a text prompt that feeds an image model and then a video model. You hit a wall when the graph depends on a custom node or a checkpoint you trained, and in that case every entry below is a better fit.

Run a saved Wireflow workflow, from the official Run Workflows page. Replace the workflow ID and the input, and set WIREFLOW_API_KEY to your own key.
```bash
curl -X POST https://www.wireflow.ai/api/v1/workflows/cm1abc123/run \
  -H "Authorization: Bearer $WIREFLOW_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "inputs": {
      "node-tiktok": "https://www.tiktok.com/t/ZP8bar3Dk/"
    }
  }'
```

### 2. Comfy Cloud API

*Best for running your exported graph on the official hosted service*

![Comfy Cloud API screenshot](https://assets.wireflow.ai/competitors/comfy-cloud-api-18b7b2ff1d73.png?v=r5)

- **What it is:** [Comfy Cloud API](https://docs.comfy.org/get_started/cloud) lets you run ComfyUI workflows on Comfy Cloud from code. Comfy Cloud is the official, fully managed ComfyUI environment, so there is no build or deployment to create.
- **Best for:** Developers who want to trigger ComfyUI workflows on hosted GPUs from their own apps or scripts, using the graph they already tested.
- **Pricing basis:** Subscription. API access needs a paid Comfy Cloud plan, from $20 a month on Standard or $16 a month billed yearly (Comfy pricing page, October 2026), and the docs say the Free tier does not include API access.
- **Standout:** You export the tested workflow in API format and submit that file. The same Comfy API v2 also runs on Comfy API deployments and on a self-hosted ComfyUI, so one integration moves between them by changing the base URL.
- **Limit:** Custom nodes are a pre-installed set, so a graph that needs a node outside that set will not run as it is. The v2 job request rejects `webhook_url` today, so you poll, and your plan caps how many API runs execute at once.
- **API or automation:** `POST /api/v2/jobs` takes the API-format graph and rejects the UI-format export, and Python and TypeScript SDKs wrap it. The `Idempotency-Key` is single-use, so a retry with the same key is rejected with a 422 and you look the job up instead of sending it twice. A signed output URL lasts roughly 6 hours, so the docs tell you to re-host the file.
- **Note:** The linked repository is the official Python SDK.
- **Sources:** [Comfy Cloud quickstart](https://docs.comfy.org/development/deploy/cloud), [Comfy API v2 overview](https://docs.comfy.org/api-reference/v2/overview), [OpenAPI v2 spec](https://docs.comfy.org/openapi-v2.yaml), [v1 Cloud API overview](https://docs.comfy.org/development/cloud/overview), checked 2026-10-11.
- **Links:**
  - [Pricing](https://comfy.org/pricing/)
  - [Comfy-Org/comfy-python-sdk](https://github.com/Comfy-Org/comfy-python-sdk)

Pick Comfy Cloud API over Wireflow when the graph already works and every node in it is in the pre-installed set, because you keep the graph and still host nothing. Where it stops for teams shipping a product is covered in [nine hosted alternatives to Comfy Cloud](https://www.wireflow.ai/blog/best-comfy-cloud-alternatives-in-2026).

Install the SDK, from the official Comfy Cloud quickstart. Then export the workflow with File, Export Workflow (API) and run it.
```bash
pip install comfy-sdk
```

### 3. ComfyDeploy

*Best for teams that share one managed ComfyUI environment*

![ComfyDeploy screenshot](https://assets.wireflow.ai/competitors/comfydeploy-052348f27a5c.png?v=r5)

- **What it is:** [ComfyDeploy](https://www.comfydeploy.com/) is a platform for running and deploying ComfyUI for teams. You import a workflow JSON file, it detects the custom nodes and creates a machine, and you pick the GPU and the ComfyUI version.
- **Best for:** Teams that already build in ComfyUI and need sharing, versioning and a production API on the same environment.
- **Pricing basis:** Not published where we could read it. The homepage shows no plans or prices, and the pricing page returned a 404 to a plain fetch on 11 October 2026, so no price is stated here.
- **Standout:** The homepage lists installing any custom nodes and any models, full version history with one-click rollback, and auto-scaling GPUs. Each account also gets a private volume connected to ComfyUI's models folder, which you fill from Hugging Face, Civitai, any link or an upload.
- **Limit:** A request names a saved deployment and its inputs, not a graph, so what runs is whatever that deployment holds. Plans, prices and limits are not on the pages we could read.
- **API or automation:** `POST /run/deployment/queue` takes a `deployment_id`, an `inputs` object, an optional `webhook` and an optional GPU override, and returns a `run_id`. There are Get Run and Cancel Run endpoints, and the webhook delivers run status updates.
- **Sources:** [API reference](https://docs.comfydeploy.com/docs/api), [Queue Run](https://docs.comfydeploy.com/docs/api/queueRun), [importing a workflow file](https://docs.comfydeploy.com/docs/workflows/import), [downloading models](https://docs.comfydeploy.com/docs/models/download), checked 2026-10-11.
- **Links:**
  - [comfy-deploy/comfydeploy](https://github.com/comfy-deploy/comfydeploy)

Pick ComfyDeploy over Comfy Cloud API when the graph needs custom nodes or models that a pre-installed set does not have, and you want a webhook when the run ends. The request no longer carries the graph, so keep the deployment ID in config and treat a workflow change as a release.

Queue a run, from the official Queue Run reference. Add your Bearer token and your own deployment_id.
```bash
curl -X POST "https://api.comfydeploy.com/api/run/deployment/queue" \
  -H "Content-Type: application/json" \
  -d '{
    "deployment_id": "15e79589-12c9-453c-a41a-348fdd7de957"
  }'
```

### 4. Replicate cog-comfyui

*Best for sending a graph to a shared hosted model*

![Replicate cog-comfyui screenshot](https://assets.wireflow.ai/competitors/replicate-cog-comfyui-fc978928b46c.png?v=r5)

- **What it is:** [Replicate cog-comfyui](https://github.com/replicate/cog-comfyui) is an MIT-licensed repo that runs ComfyUI with an API, packaged as a Cog model. It powers the public any-comfyui-workflow model on Replicate, so you can send a graph without deploying anything.
- **Best for:** Developers who want to run exported ComfyUI API workflows on Replicate, starting on the shared model and moving to their own instance later.
- **Pricing basis:** The repo is free under the MIT licence, and running on Replicate is billed at Replicate rates. The README says a private deployment also means paying for setup and idle time.
- **Standout:** You pass the API-format workflow as `workflow_json`, as a string, a URL or a file, and a dedicated private instance lets you pin the ComfyUI and custom node versions.
- **Limit:** The shared model may load and unload models between users, which slows predictions, and the repo warns that ComfyUI node updates can break existing workflows. On the shared model you work from the supported lists of weights and custom nodes, unless you request more, bring weights through the train tab or fork the repo.
- **API or automation:** It runs as a Replicate model, so a prediction can deliver its completed result to a webhook. For full control, a fork deployed with Cog sets the ComfyUI version, the custom nodes and the API itself.
- **Sources:** the README linked above, [supported weights](https://github.com/replicate/cog-comfyui/blob/main/supported_weights.md), [Replicate webhooks](https://replicate.com/docs/topics/webhooks), checked 2026-10-11.
- **Links:**
  - [Pricing](https://replicate.com/pricing)

Pick Replicate cog-comfyui over ComfyDeploy when you already call Replicate and want the graph in the request and not in a saved deployment. Start on the shared model to prove the graph runs, then pin a private deployment before anything customer-facing depends on it.

Run a workflow file with Cog, from the cog-comfyui README.
```bash
cog predict -i workflow_json=@your_workflow.json
```

### 5. RunPod worker-comfyui

*Best for your own serverless endpoint with a webhook*

![RunPod worker-comfyui screenshot](https://assets.wireflow.ai/competitors/runpod-worker-comfyui-f8c5b6e72f7e.png?v=r5)

- **What it is:** [RunPod worker-comfyui](https://github.com/runpod-workers/worker-comfyui) is ComfyUI as a serverless API on RunPod: you send a workflow in an API call and get the generated images back.
- **Best for:** Developers who want their own ComfyUI endpoint on RunPod serverless GPUs, with full control of the image.
- **Pricing basis:** The repo is free under AGPL-3.0, and you pay RunPod Serverless GPU rates, which are listed on the RunPod pricing page (October 2026).
- **Standout:** It ships Docker images for a clean base, FLUX.1 schnell, FLUX.1 dev, SDXL and SD3, and exposes `/run`, `/runsync` and `/health`. Custom nodes and models go into a custom Dockerfile built from a base image, or the models sit on a network volume.
- **Limit:** RunPod request size limits apply, for example 10MB for `/run` and 20MB for `/runsync`, so large base64 input images can exceed them. The licence is AGPL-3.0, and custom models need a network volume or a Docker build.
- **API or automation:** The request carries the Export (API) graph in `input.workflow`, with optional base64 images in `input.images`. `/runsync` waits for the result, and `/run` returns a job ID that you poll at `/status` or pair with a `webhook` in the request. Images come back as base64 strings, or as S3 URLs when S3 is configured.
- **Sources:** the README linked above and [the customization guide](https://github.com/runpod-workers/worker-comfyui/blob/main/docs/customization.md), checked 2026-10-11.
- **Links:**
  - [Docs](https://github.com/runpod-workers/worker-comfyui/blob/main/docs/deployment.md)
  - [Pricing](https://www.runpod.io/pricing)

Pick RunPod worker-comfyui over Replicate cog-comfyui when you want to own the image, the custom nodes and the scaling settings of one endpoint. Keep base64 input images small, because the request body limit is the first wall you hit.

Send a workflow to the sync endpoint, from the worker-comfyui README. Replace <api_key> and <endpoint_id>, and put your Export (API) JSON in input.workflow.
```bash
curl -X POST \
  -H "Authorization: Bearer <api_key>" \
  -H "Content-Type: application/json" \
  -d '{"input":{"workflow":{... your workflow JSON ...}}}' \
  https://api.runpod.ai/v2/<endpoint_id>/runsync
```

### 6. SaladCloud comfyui-api

*Best for a stateless wrapper inside your own container*

![SaladCloud comfyui-api screenshot](https://assets.wireflow.ai/competitors/saladcloud-comfyui-api-d23ee31ff9e5.png?v=r5)

- **What it is:** [SaladCloud comfyui-api](https://github.com/SaladTechnologies/comfyui-api) is a simple wrapper that exposes ComfyUI as a stateless REST API with webhooks and storage backends. It sits in front of ComfyUI in your own container image and uses ComfyUI's own `/prompt` API, so any API-formatted prompt can be executed.
- **Best for:** Developers who want to scale ComfyUI behind a load balancer on their own infrastructure or on SaladCloud.
- **Pricing basis:** Free under the MIT licence. ComfyUI itself is GPL-3.0, and you supply and pay for your own GPU hosting.
- **Standout:** Completed outputs go to a webhook or to S3, Hugging Face or Azure Blob storage, and webhooks follow the Standard Webhooks format, so you can verify them with a `WEBHOOK_SECRET`. A startup manifest downloads models and installs custom nodes.
- **Limit:** You build, host and scale the container yourself. On SaladCloud the Container Gateway has a 100 second timeout, so a long workflow needs a webhook or SaladCloud Job Queues, and the container image is capped at 35GB compressed.
- **API or automation:** `POST /prompt` takes the prompt graph plus options. With a `webhook_v2` field the server answers 202 at once and sends one webhook when the whole workflow completes, or a webhook if the request fails. Without async options it answers 200 with base64 images, and new endpoints mount from `.js` or `.ts` files in the `/workflows` directory.
- **Sources:** the README linked above, checked 2026-10-11.

Pick SaladCloud comfyui-api over RunPod worker-comfyui when you are not tied to one GPU host and want the same container to run anywhere behind a load balancer. The server keeps no state between requests, so decide early where your own queue and job records live.

Add the server to your own ComfyUI Dockerfile, from the comfyui-api README.
```dockerfile
# Change this to the version you want to use
ARG api_version=1.19.0

# Download the comfyui-api binary, and make it executable
ADD https://github.com/SaladTechnologies/comfyui-api/releases/download/${api_version}/comfyui-api .
RUN chmod +x comfyui-api

# Set CMD to launch the comfyui-api binary. The comfyui-api binary will launch ComfyUI as a child process.
CMD ["./comfyui-api"]
```

### 7. comfy-api-proxy

*Best for the cloud contract on a machine you already run*

![comfy-api-proxy screenshot](https://assets.wireflow.ai/competitors/comfy-api-proxy-b0b7493c7194.png?v=r5)

- **What it is:** [comfy-api-proxy](https://github.com/Comfy-Org/comfy-api-proxy) is a local proxy that serves the Comfy API v2 in front of a self-hosted ComfyUI, so code written for Comfy Cloud can target your own machine.
- **Best for:** Developers who run ComfyUI themselves and want a Comfy Cloud style API on top of it.
- **Pricing basis:** Free and open source under the MIT licence, with no price. You need your own running ComfyUI instance behind it.
- **Standout:** It installs with `pip install comfy-api-proxy`, wraps ComfyUI's native HTTP and WebSocket API one-to-one, and works with the same Python and TypeScript SDKs that Comfy Cloud users use. Moving a workload between your machine and the cloud is a base URL change.
- **Limit:** A completion webhook is not described in the README, so you poll `GET /api/v2/jobs/{id}` or open the SSE stream, which is capped at 8 concurrent streams by default. It needs Python 3.10+ and a running ComfyUI instance, and it refuses to bind past `127.0.0.1` unless you set a token or opt out of that guard.
- **API or automation:** It serves the v2 routes under `/api/v2`, with an optional static bearer token. With `--comfyui-base-dir` set, a model upload lands directly in a ComfyUI model directory, safetensors only. An opt-in `--state-dir` stores job records and idempotency keys in SQLite.
- **Sources:** the README linked above, checked 2026-10-11.
- **Links:**
  - [Docs](https://docs.comfy.org/api-reference/v2/overview)

Pick comfy-api-proxy over SaladCloud comfyui-api when you might move to Comfy Cloud later and want to write the client once. It is the most to operate on this list, because the GPU, ComfyUI, the custom nodes and the network exposure are all yours.

Install and start the proxy, from the comfy-api-proxy README. By default it proxies the ComfyUI on 127.0.0.1:8188 and serves the v2 API on port 8189.
```bash
pip install comfy-api-proxy
comfy-api-proxy
```

## ComfyUI, the baseline

ComfyUI is what 6 of the 7 entries run, so it is described here and not ranked. These lines come from the Comfy docs and READMEs, checked 2026-10-11.

- **What it is:** [ComfyUI](https://comfy.org/) is a node-based visual engine for building image, video, audio and 3D workflows without code.
- **Its own API:** ComfyUI has a native HTTP and WebSocket API, and its `/prompt` endpoint queues a workflow graph. The options above host or wrap that API.
- **Cost and upkeep:** It is free under GPL-3.0 and local use is free. You set it up and update it yourself, with GPU-specific PyTorch builds and Python version requirements.
- **Nodes and models:** On a self-hosted ComfyUI you can install any custom node and use any model, and you manage and download them yourself.

## What each check means

A check means the vendor's own docs or README describe it. A cross means the source says it works another way. Anything in brackets without a mark means not published, which is not proof that it is absent.

- **Runs your ComfyUI graph:** The service executes a workflow you built in ComfyUI, sent with the request or saved as a deployment.
- **Custom nodes you choose:** You can run custom nodes you pick, not only a fixed pre-installed set.
- **Your own models:** You can add your own checkpoints, LoRAs or other model files.
- **Completion webhook:** You give a URL and the service POSTs the result or the status when the run finishes.
- **GPUs hosted for you:** The vendor runs the GPU, so there is no machine or container host of your own to keep up.

## How this list is maintained

Every line comes from the vendor's own docs, OpenAPI spec or README, read on 11 October 2026. For each option we read how a request is shaped, how a finished job reports back, how custom nodes and models get in, and who runs the GPU. The numbered order is editorial and follows 4 checks in this order: how much you host and operate, whether the request carries your graph or a saved ID, how you learn a job is done, and whether your own nodes and models can run. Nothing here was benchmarked, so no cold start was timed and no price was tested. Entry 1 is the only option that does not run ComfyUI, and it is ranked first on the first check alone. Options we had not checked against their own docs by that date are left out.

To correct a line, open an issue or a pull request with the tool, the check and a link to the vendor page that proves it. Corrections to entry 1 are welcome too.

- [`data/tools.json`](data/tools.json) is the source of truth. The tables in this README are generated from it and are overwritten on every run, so edit the JSON, not the tables.
- [`scripts/update.js`](scripts/update.js) fetches star counts and latest release tags from the GitHub API for the tools that publish an official repo, stamps the check date, and regenerates the tables. `--offline` regenerates without the network; `--check` exits non-zero if the README has drifted from the data.
- [`.github/workflows/refresh.yml`](.github/workflows/refresh.yml) runs it weekly and on manual dispatch, and commits only when the data actually changed.
- Prices are deliberately not stored as numbers. A stale price in a comparison table is worse than no price, so the table links to each vendor's own pricing page.

## FAQ

<details>
<summary><strong>Does ComfyUI have an API?</strong></summary>

Yes. ComfyUI has a native HTTP and WebSocket API, and its `/prompt` endpoint queues a workflow graph. The 6 ComfyUI options on this list host or wrap that API, and they differ in what the request carries and in how a finished job reports back.

</details>

<details>
<summary><strong>What is the easiest way to run ComfyUI in the cloud with an API?</strong></summary>

Comfy Cloud API is the shortest path for a graph that already works. You need a paid plan, an API key, the API-format export and the SDK, and there is no build or deployment to create. It only fits when every node you need is in the pre-installed set.

</details>

<details>
<summary><strong>Can I use custom nodes or bring my own models?</strong></summary>

On 5 of the 7, yes to both. ComfyDeploy, Replicate cog-comfyui, RunPod worker-comfyui, SaladCloud comfyui-api and a self-hosted ComfyUI behind comfy-api-proxy all run nodes and models you choose. Comfy Cloud API imports models but uses a pre-installed node set, and Wireflow runs neither.

</details>

<details>
<summary><strong>How do I get notified when an execution finishes?</strong></summary>

Five of the 7 document a completion webhook: Wireflow, ComfyDeploy, Replicate cog-comfyui, RunPod worker-comfyui and SaladCloud comfyui-api. Comfy API v2, on Comfy Cloud and behind comfy-api-proxy, is poll first with an SSE stream as a live extra. Wireflow's delivery format is in [the Wireflow webhook docs](https://www.wireflow.ai/docs/api/webhooks).

</details>

<details>
<summary><strong>Can I import my ComfyUI workflow JSON into Wireflow?</strong></summary>

No. Wireflow is a separate platform, and ComfyUI workflow JSON, custom Python nodes and local checkpoints do not transfer, so you rebuild the workflow from its own nodes. If keeping the exact graph matters, use one of the 6 ComfyUI options, and this page explains [how a rebuilt canvas differs from Comfy Cloud](https://www.wireflow.ai/features/comfy-cloud-alternative).

</details>

<details>
<summary><strong>Do I need a GPU or any local infrastructure to use the API?</strong></summary>

Not for 5 of the 7. Wireflow, Comfy Cloud API, ComfyDeploy, Replicate cog-comfyui and RunPod worker-comfyui run on the vendor's GPUs. SaladCloud comfyui-api runs in a container you host, and comfy-api-proxy sits in front of a ComfyUI on your own machine.

</details>

<details>
<summary><strong>What happens if a workflow execution fails?</strong></summary>

It depends on the option. SaladCloud comfyui-api sends a webhook when a request fails. Comfy API v2 keeps job state pollable by ID and rejects a retry that reuses an `Idempotency-Key`, so you look the job up before you resubmit. On Wireflow, a model that fails is not charged.

</details>

## The short version

Pick Wireflow when you want an API and can rebuild the workflow from hosted models, because there is nothing to host. Pick Comfy Cloud API, the next entry, when the graph must stay as it is and its nodes are in the pre-installed set. If the graph needs your own nodes or models, ComfyDeploy and Replicate cog-comfyui host it for you, and the last three entries give you the most control for the most work. Before you commit, run one real workflow through your two finalists and time the path from request to stored output. For entry 1, check first that the models your graph relies on are in [the Wireflow model catalog](https://www.wireflow.ai/models).

## Contributing

Corrections and additions are welcome, including corrections to the entry for the tool that maintains this list. Open an issue with the tool name, a working link, one line on what it does that the tools already listed do not, and one line on where it stops. Entries are judged on whether they are usable today, not on popularity. Full rules in [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[CC0 1.0 Universal](LICENSE), public domain. Take the data, fork the list, no attribution required.

---

Maintained by [a1adams](https://github.com/a1adams).
