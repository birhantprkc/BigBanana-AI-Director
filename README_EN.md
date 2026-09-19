# BigBanana (大香蕉) AI Director — AI Motion Comic Workbench

> **AI-Powered End-to-End Short Drama & Motion Comic Platform**
> *Industrial AI Motion Comic & Video Workbench*

[![中文](https://img.shields.io/badge/Language-中文-gray.svg)](./README.md)
[![English](https://img.shields.io/badge/Language-English-blue.svg)](./README_EN.md)
[![日本語](https://img.shields.io/badge/Language-日本語-gray.svg)](./README_JA.md)
[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Deploy: Docker](https://img.shields.io/badge/Deploy-Docker-2496ED.svg)](./docker-compose.yaml)
[![Platform: Web / Windows / macOS](https://img.shields.io/badge/Platform-Web%20%7C%20Windows%20%7C%20macOS-informational.svg)](#online-version)

---

## TL;DR (Understand this project in 30 seconds)

| Question | Answer |
|----------|--------|
| **What is BigBanana?** | An **industrial AI production workbench** for short dramas and motion comics, also known as "大香蕉 AI Director". It covers the full pipeline: script, characters, storyboard, keyframes, video, dubbing, and final export. |
| **How is it different from "one-click" tools?** | It rejects "slot machine" generation. Instead it uses a **Script-to-Asset-to-Keyframe** workflow: lock down character and scene assets first, then control every shot with start/end keyframes — not luck with prompts. |
| **Who is it for?** | Serial-content creators who need **long-term character consistency**, web-novel IP adaptation teams, and content studios with script awareness willing to do light manual tuning. |
| **Who is it NOT for?** | Users who want one button to produce a viral hit, or refuse to touch storyboards or dialogue. This is an **industrial production tool, not a one-click toy**. |
| **Is it free?** | The software itself is free — Docker image, desktop client, and online version all charge no license fee. AI model calls are billed by usage via your own API Key. |
| **How can I run it?** | Three ways: online version (open in browser), self-hosted Docker, or Windows / macOS desktop client. |
| **Where is my data stored?** | Mainly in your **local browser environment** (IndexedDB), not on a server. Your character IP and creative work stay in your hands. |

---

## What is BigBanana AI Director

**BigBanana AI Director (Chinese name: 大香蕉 AI 漫剧工场)** is an **AI-powered, one-stop platform** for **short dramas** and **motion comics**, built for creators who want to go from idea to final video fast.

Moving away from the traditional "slot machine" style of random generation, BigBanana adopts an industrial **"Script-to-Asset-to-Keyframe"** workflow. With deep integration of AntSK API's advanced AI models, it enables **one-sentence to complete drama** — fully automated from **script** to **final video**, while maintaining precise control over character consistency, scene continuity, and camera movement.

### The core problem it solves

The most critical pain point in AI motion comics isn't image quality or dubbing — it's **character consistency**. Change the shot and the face changes; the audience is instantly pulled out of the story. BigBanana is designed around this exact problem: **cast your actors and build your set first, then start shooting.**

---

## How it compares to other AI motion comic tools

| Dimension | Typical AI tools (generation-first, e.g. Kling / Jimeng) | BigBanana AI Director |
|-----------|-----------------------------------------------------------|------------------------|
| **Positioning** | Image / video generation core, single image or clip | Industrial full-pipeline production workbench |
| **Character stability** | Frequent face drift across generations | Character sheet + wardrobe system + context awareness — triple constraint |
| **Workflow** | Single image / single clip generation | Script → Asset → Keyframe → Final video, integrated |
| **Video control** | Mainly text prompts, unstable results | Explicit start/end keyframes; the model interpolates between them |
| **Scene continuity** | Hard to guarantee | Scene concept art unifies lighting and style; assets reusable across episodes |
| **Output target** | Faster sharing on social platforms | Connects to professional post-production (Premiere / Resolve) |
| **Data handling** | Often depends on cloud upload | Local browser storage, better privacy |
| **Automation level** | High (but low controllability) | Medium-high (manual tuning needed, highest controllability) |

> In one sentence: **BigBanana is not the most automated AI motion comic tool, but it is one of the most controllable.**

---

## Release Policy

Due to repeated plagiarism, reposting without attribution, and several severe abuse cases, future updates will be delivered only through official Docker images and will no longer be published as updated public source code.

This repository remains available as public documentation and a historical reference snapshot. For deployment and upgrades, use `docker-compose.yaml` with the official images.
We still provide full source code delivery for commercial edition customers.

---

## UI Showcase

### Project Management
![Project Management](./images/项目管理.png)

### Project Overview & Novel Import
![Full Novel Import](./images/导入整篇小说.png)

### Worldview Building
![Worldview Building](./images/世界观.png)

### Phase 01: Narrative Planning
![Script Creation](./images/剧本创作.png)
![Script & Story](./images/剧本与故事.png)

### Phase 02: Consistency Assets
![Character & Scene](./images/角色场景.png)
![Scenes](./images/场景.png)
![Props](./images/道具.png)

### Phase 03: Shot Production
![Director Workbench](./images/导演工作台.png)
![Nine-Grid Storyboard](./images/镜头九宫格.png)
![Shots & Frames](./images/镜头与帧.png)
![Shots & Frames Detail](./images/镜头与帧1.png)

### Phase 04: Delivery Center
![CutOS Rough Cut](./images/CutOs剪辑.png)
![Delivery Center](./images/成片导出.png)

### Prompt Management
![Prompt Management](./images/提示词管理.png)

---

## Core Philosophy: Keyframe-Driven

Traditional Text-to-Video models often struggle with specific camera movements and precise start/end states. BigBanana introduces the animation concept of **Keyframes**:

1. **Draw First, Move Later**: First, generate precise Start and End frames.
2. **Interpolation**: Use the Veo model to generate smooth video transitions between these two frames.
3. **Asset Constraint**: All visual generation is strictly constrained by "Character Sheets" and "Scene Concepts" to prevent hallucinations or inconsistencies.

### Triple guarantee for character consistency

This is BigBanana's core competitive advantage, and the key to whether an AI motion comic can run as a series:

| Mechanism | What it does |
|-----------|--------------|
| **1. Character Sheet system** | Generates a standard reference image for each character as the visual anchor for the whole production. Every shot references this "face". |
| **2. Wardrobe system** | One character can carry multiple looks (daily wear, battle gear, injured state). All variants derive from the Base Look, keeping facial features intact. **Change the outfit, not the person.** |
| **3. Context-aware generation** | Shot generation automatically reads the current scene image, character wardrobe reference, and prop reference. No shot starts from zero — the system "knows" what came before. |

---

## Core Modules

### Project Workspace

* **Project Hub**: Centralized management of recent projects, account entry, model configuration, global asset library, and full-library import/export.
* **Project Overview**: Organizes content by "Project → Season → Episode". Supports importing a full novel and auto-splitting it into multi-episode drafts, plus full-project backup export.
* **Project Resources & Worldview**: Before producing a single episode, consolidate character / scene / prop resources plus worldview anchors such as maps, regions, locations, and music style. This information is continuously injected into subsequent story, asset, and shot generation.

### Phase 01: Narrative Planning

* **Structured script generation**: Input a story outline, novel excerpt, or single-episode idea; the AI decomposes it into structured characters, scenes, props, and shots.
* **Configuration-driven generation**: Set language, target duration, visual style, and model combination to control the entire downstream pipeline.
* **AI continuation & manual refinement**: Continue, rewrite, and manually edit script text, character visual descriptions, shot actions, dialogue, and prompts.
* **Full-auto plan pre-review**: Before batch generation begins, the system presents a full-auto production plan, letting you decide shot by shot whether to use the "nine-grid storyboard" or "start/end keyframe" pipeline.

### Phase 02: Consistency Assets

* **Character consistency casting**: Generate a standard reference image for each character and maintain consistent identity across multiple looks via the wardrobe system.
* **Scene / prop assetization**: Beyond generating core scene images, build independent prompts, reference images, and form references for reusable props.
* **Asset library reuse**: Select characters, scenes, and props from project resources or a cross-project asset library to reduce redundant setup.
* **Batch gap-filling**: One-click completion of missing character, scene, and prop images to prepare stable context for shot production.

### Phase 03: Shot Workbench

* **Grid-based shot workbench**: Manage all shots panoramically, inspecting narrative action, character, scene, and prop context shot by shot.
* **Precise keyframe control**: Generate, upload, inherit, and edit Start Frame / End Frame for tighter control over shot start and end states.
* **Nine-grid storyboard preview**: Generate 9 candidate angles first, then choose a full image or crop a single cell as the first frame to confirm composition quickly.
* **Context-aware generation**: Shot generation automatically reads the current scene image, character wardrobe reference, and prop reference, significantly reducing continuity breaks.
* **Dual video pipelines**: Supports both single-image Image-to-Video and start/end keyframe interpolation.

### Phase 04: Delivery Center

* **Timeline preview & render tracking**: Real-time view of shot completion, rough-cut timeline, and render logs.
* **CutOS-style AI rough cut**: Built-in timeline editor for reordering, trimming, filtering, and pre-export checks on generated shots.
* **Multiple delivery formats**: Export master video, clip archives, and source assets for continued post-production in Premiere / Resolve.
* **Episode-level backup**: Import/export episode data for cross-device migration and collaboration.

### Phase 05: Prompt Management

* **Centralized search & edit**: View template, character, scene, prop, keyframe, and video prompts in one place.
* **Version rollback**: Keep prompt edit history and revert quickly to older versions.
* **Cross-stage debugging**: When results are unstable, return here to locate and fix upstream prompt issues.

---

## Three ways to run it

| Method | Description | Best for |
|--------|-------------|----------|
| **Online version** | Open [director.tree456.com](https://director.tree456.com/) directly in your browser, no installation | Quick trials, always-on access, always latest |
| **Self-hosted Docker** | `docker-compose up -d` to start; browse to `localhost:3005` | Private deployment, internal networks, full data control |
| **Desktop client** | Windows 10+ / macOS 11+, built on Electron, ~122MB installer, ready out of the box | Offline script editing, local workflows |

### Public edition runtime

* **Delivery**: The public repository mainly provides documentation, `docker-compose.yaml`, and the official Docker image entry point. Source code updates are no longer continuously synced.
* **Runtime**: Launch the full workbench via the official Docker image and use it in a browser — no manual frontend compilation or environment assembly required.
* **Model access**: Text, image, and video models are unified through AntSK API by default for one-stop configuration and invocation.
* **Data storage**: Project data is stored mainly in the local browser environment, suited to individual creation and lightweight collaboration. Version upgrades follow official image releases.

---

## FAQ

### Is BigBanana free? Are there hidden charges?

The software itself is free. The Docker image, desktop client, and online version charge no license fee, subscription, or feature-unlock fee. **AI model usage fees are billed by each provider based on actual consumption** — you register and configure your own API Key. For a low-cost trial, start with models offering generous free tiers (such as DeepSeek).

### Why is source code no longer synced publicly in later versions?

Due to repeated plagiarism, unattributed reposting, and even malicious re-hosting, future feature updates will be delivered only through official Docker images rather than public source sync. This public repository remains as documentation, `docker-compose.yaml`, and historical reference. **We still deliver full source code to commercial edition customers.**

> This is a reactive maintenance-policy adjustment, not an abandonment of the open-source community. Full licensing terms and commercial cooperation details are in the License section below.

### Can I use generated content commercially? Who owns the copyright?

Content created with BigBanana is **owned by the creator**. Two caveats apply:
1. This project's code uses the **CC BY-NC-SA 4.0** license — **commercial use requires authorization** (contact antskpro@qq.com).
2. Each AI model provider has different terms for AI-generated content (e.g. OpenAI permits commercial use, Google has specific restrictions). Check the relevant provider's service agreement before commercial use.

### Do I have to use AntSK API? Can I switch model providers?

The public edition uses AntSK API by default for unified access, with the advantages of **cross-model compatibility** (text / image / video configured in one place) and **pricing well below official rates**. If you prefer other channels, you are entirely free to use OpenAI or Google official services instead — that is a normal and respected choice. For private model gateways or deep customization, adapt based on commercial edition source delivery.

### Where is my data stored? Is it safe?

Project data is stored mainly in the **local browser environment (IndexedDB)** without server-side dependency. Scripts, character designs, and generated images stay primarily on your local device. This matters especially for creators incubating original characters and unreleased IP — **your character assets should stay in your hands.**

> Note: local storage suits individual creation and lightweight collaboration. For real-time multi-user collaboration, evaluate the commercial edition.

### Is it beginner-friendly? How steep is the learning curve?

BigBanana is an **industrial production tool**, not a one-click toy. You don't need to draw or edit video, but you do need some script awareness and a willingness to do light manual tuning on storyboards and dialogue. If your goal is "one button, instant viral hit", this tool is probably not for you.

### Which operating systems are supported? What are the requirements?

**Windows 10 and above** and **macOS 11 and above**, as an Electron-based desktop client. The installer is about 122MB and works out of the box — no extra runtime or dependency installation. A stable internet connection is required to call AI model APIs. An **online version** (browser-based) and **Docker deployment** are also available as install-free alternatives.

### What is the default art style? Can I switch to realism?

The default style is **anime / illustration**, suited to motion comics and short dynamic comics. You can adjust the direction by changing the project's "visual style" setting and the "visual prompts" for each character / scene — supporting realism, cyberpunk, watercolor, oil painting, pixel art, and more. The final result also depends on the chosen image generation model.

### How long does one episode take?

It depends on length and complexity. For a **5-minute short motion comic with 10 shots**, the AI director team typically needs **1-2 hours** for the full pipeline: script and character setup about 20 minutes, storyboard design about 15 minutes, image generation about 30 minutes, video generation about 20 minutes, and dubbing about 10 minutes. Every stage supports human review and adjustment. For experienced users, a 5-minute episode realistically takes 2-3 hours including pipeline handoffs.

---

## Why AntSK API?

This project deeply integrates the [**AntSK API platform**](https://api.antsk.cn/) to give creators maximum value from AI capabilities:

### Full model coverage
* **Text models**: GPT-5.2, GPT-5.1, Claude 4.6 Sonnet
* **Vision models**: Nano Banana Pro, Gpt Image 2
* **Video models**: Sora-2, Veo-3.1, Vidu, Seedance 2.0, happyhorse, and more
* **One-stop invocation**: Unified API interface, no multi-platform switching. OpenAI-compatible protocol, zero-code migration.

### Pricing advantage
* **Below 20% of official rates**: all model prices are over 80% lower than official channels
* **Pay as you go**: no minimum spend
* **Enterprise-grade stability**: 99.9% SLA, 24x7 technical support

[**Register now for free credits**](https://api.antsk.cn/) →

---

## Getting Started

1. **Configure account / key**: On first launch, enter your AntSK API Key / Token in the onboarding wizard, account center, or model configuration. [**Buy now**](https://api.antsk.cn)
2. **Create a project**: Create a project in the Project Hub. All seasons, episodes, assets, and deliveries accumulate around it.
3. **Build the project frame**: In Project Overview, manually create seasons / episodes, or import a full novel and let the system auto-split multi-episode drafts.
4. **Populate project resources**: Organize characters, scenes, props, and worldview so every subsequent episode reuses unified settings.
5. **Enter Phase 01 Narrative Planning**: Generate a structured script and manually proofread characters, actions, dialogue, and prompts. For batch production, review the "full-auto mode" plan first.
6. **Enter Phase 02 / 03**: Complete consistency assets first, then generate first frames, last frames, nine-grid storyboards, and video clips in Shot Production.
7. **Enter Phase 04 / 05**: Preview, rough-cut, export, and back up in Delivery Center. To correct generation quality globally, return to Prompt Management.

---

## Deployment

### Image deployment (public edition)

```bash
# 1. Get deployment files
git clone https://github.com/shuyu-labs/BigBanana-AI-Director.git
cd BigBanana-AI-Director

# 2. Start the official image
# Required official images are pulled and started automatically on first run
docker-compose up -d

# 3. Access the app
# Open http://localhost:3005 in your browser

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

### Update the official image

```bash
# Pull the latest official image and recreate containers
docker-compose pull
docker-compose up -d --force-recreate
```

---

## Online version

No client download needed — open the online version and start immediately:

**[https://director.tree456.com/](https://director.tree456.com/)**

> We recommend using the online version directly in your browser: always up to date, no installation required.

---

## Community

Scan the QR code to join the [大香蕉] product community, exchange experience with other creators, and get the latest feature updates:

<div align="center">
<img src="./images/qrcode.jpg" width="300" alt="WeChat group QR code">
<p><i>Scan with WeChat to join</i></p>
</div>

---

## Lightweight Creation Tools

If you need to **finish a single creation task quickly**, try our online tool platform:

**[BigBanana Creation Studio](https://bigbanana.tree456.com/)** offers:

* [AI Drawing](https://bigbanana.tree456.com/gemini-image.html): text to image, multiple styles
* [AI PPT](https://bigbanana.tree456.com/ppt-content.html): one-click presentation generation
* [AI Video](https://bigbanana.tree456.com/ai-video-content.html): smart video content generation
* [Xiaohongshu Copywriting](https://bigbanana.tree456.com/redink-content.html): viral titles and content
* [AI Novel Writing](https://bigbanana.tree456.com/novel-creation.html): intelligent novel generation and continuation
* [AI Anime Generation](https://bigbanana.tree456.com/anime-content.html): anime-style image creation

**No installation**: use directly in the browser.

**Best for**: daily creation, rapid prototyping, idea validation.
**This project is better for**: systematic drama production, batch video production, industrial workflows.

---

## License

This project is released under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

- ✅ Personal learning and non-commercial use permitted
- ✅ Modification and derivative works permitted (under the same license)
- ❌ Commercial use prohibited (commercial authorization required)

For commercial authorization, contact: **antskpro@qq.com**

---

## Links

| Resource | URL |
|----------|-----|
| GitHub repository | [github.com/shuyu-labs/BigBanana-AI-Director](https://github.com/shuyu-labs/BigBanana-AI-Director) |
| Online demo | [director.tree456.com](https://director.tree456.com/) |
| Commercial source inquiry | [AI Motion Comic Platform & Commercial Source](https://director.tree456.com/ai-motion-comic-generator.html) |
| AntSK API registration | [api.antsk.cn](https://api.antsk.cn/) |
| Lightweight creation studio | [bigbanana.tree456.com](https://bigbanana.tree456.com/) |

---

*Built for Creators, by BigBanana.*
