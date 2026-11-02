# Kuldeep Singh

Founder of [YouxAI](https://youxai.app). I work on running small language models fast and correctly inside a web browser, on ordinary laptops and gaming GPUs. Before that I was an iOS developer at Walmart, on the US shopping app (100M+ downloads).

YouxAI needed private, on-device AI. That led me to write my own WebGPU engine, the engine led me to a GPU driver bug on NVIDIA, and that led to a small-model research program. Four papers are in preparation; none is posted yet.

### YouxAI

A Chrome extension and web app that tracks job applications, fills application forms from your profile and scores how well a job fits. The model is Google's Gemma 4 E2B, running in the browser through Google's LiteRT-LM web runtime, so your profile isn't sent to a server for those tasks. The code is private.

[youxai.app](https://youxai.app) · [Chrome Web Store](https://chromewebstore.google.com/detail/job-application-tracker/mggpimiojdmbijnlfeibpokbjnbcblnl)

### Browser AI engine work

- [gemma4-webgpu-engine](https://github.com/Ar5en1c/gemma4-webgpu-engine): my WebGPU inference engine for Gemma 4 E2B, in TypeScript and WGSL with no runtime dependencies. Alpha, Apache-2.0, with a [live benchmark page](https://ar5en1c.github.io/gemma4-webgpu-engine/). It was written without copying code from any other inference engine. On an RTX 5070 the latest eight-prompt runs decode at 296.5 to 296.95 tokens/s, against 272.75 to 273.25 in matching controls, with identical generated IDs.
- [gemma4-webgpu-nvidia-subgroup-fix](https://github.com/Ar5en1c/gemma4-webgpu-nvidia-subgroup-fix): root cause and fix for an in-browser Gemma engine that printed garbage on NVIDIA GPUs under Windows. The fix runs at 213 to 223 tokens/s with correct output, against 193 for the community workaround. The patch is sent upstream and not merged yet.
- [headroom](https://github.com/Ar5en1c/headroom): a 30-second browser test of your GPU's memory-bandwidth ceiling, plus a check for the NVIDIA bug. [Try it](https://ar5en1c.github.io/headroom/).
- [webllm-bench](https://github.com/Ar5en1c/webllm-bench) and [qwen2.5-1.5b-ctx8192-mlc](https://github.com/Ar5en1c/qwen2.5-1.5b-ctx8192-mlc): earlier browser model benchmarks and an extended-context Qwen build ([Hugging Face](https://huggingface.co/Ar5en1c/Qwen2.5-1.5B-Instruct-q4f16_1-MLC-ctx8192)), from before YouxAI moved to Gemma 4.

### Research

Since October 30, 2026 I've run a small-model research program sized to one RTX 5070 and an M1 MacBook. Each study writes its hypotheses down before scoring and reports only public benchmarks. Preprints in preparation:

- Compressing the per-layer embedding tables of Gemma 4 E2B, building on OPTIC
- Prompt re-reading in a looped language model
- Exact prefill on stable WebGPU on a low-end Apple GPU
- The subgroup reduction miscompile behind the NVIDIA bug above

### Agent tooling

- [context-guardian](https://github.com/Ar5en1c/context-guardian): an MCP server that indexes code, logs and config locally and gives coding agents search tools. On npm as `context-guardian-mcp`, 242 downloads in its first week. Its README calls its own benchmark a smoke test.
- [youxpc](https://github.com/Ar5en1c/youxpc): a macOS MCP server that shows app windows to an agent as numbered text. It's a fork of [Ghost OS](https://github.com/ghostwright/ghost-os) by Ghostwright (MIT), and the README says so. On 17 desktop tasks, 3 trials each on one M1, it passed 51 of 51 runs against 46 of 51 for Ghost OS 2.2.1, with 77% fewer tokens. I wrote the harder tasks myself, and the README discloses that.
- [localqa](https://github.com/Ar5en1c/localqa): a local sidecar that compacts logs, browser evidence and repo context for coding agents. 53.39% fewer input tokens on one real task; size ratios aren't billing savings.
- [us-internships-and-new-grad-jobs](https://github.com/Ar5en1c/us-internships-and-new-grad-jobs): US internship and new-grad listings, pulled daily from employers' own job boards.

### Contact

[LinkedIn](https://www.linkedin.com/in/kuldeep-5ingh/) · [X](https://x.com/kuldeep_youxai) · [kponia05@gmail.com](mailto:kponia05@gmail.com)
