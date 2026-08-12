# How to Run AI Locally with Ollama (No API, No Cloud)

**Estimated length:** 6–8 min
**Language:** English
**Main tool:** Ollama

---

[HOOK] (0:00–0:15)

You tried running AI locally, followed a tutorial, cloned a repo, edited a docker-compose file... and gave up halfway. Same here. Until I found Ollama. I had everything running in two minutes. Let me show you.

*Screen: terminal showing `ollama run llama3.2` answering a question in real time.*

---

[INTRO / PROMISE] (0:15–0:45)

The problem with most local AI setups is that they assume you already know Docker, containers, and driver configuration. That's way too much complexity to get to something that should be simple.

Ollama cuts all of that. One command installs it. One command downloads the model. One command runs it. By the end of this video you'll have an LLM running 100% on your machine — no API, no cloud, no data leaving your computer.

---

## 1. Install Ollama (0:45–2:00)

On Linux and Mac, open a terminal and run:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

That's it. This command downloads and installs Ollama, including the server that manages your models in the background.

On Windows there's a graphical installer — link in the description, one click.

To confirm it worked:

```bash
ollama --version
```

Got a version number? You're ready. No restart, no configuration needed.

*Screen: terminal running the curl command and showing `ollama --version` with the installed version.*

---

## 2. Pick and download a model (2:00–3:30)

Three options depending on your machine:

- **llama3.2** — from Meta, 3B parameters, lightweight. Works fine even on a laptop without a GPU.
- **qwen2.5:7b** — my go-to for general use. More capable, still reasonable on memory.
- **gemma3** — from Google, great for coding tasks.

Not sure which to pick? Start with llama3.2:

```bash
ollama pull llama3.2
```

Ollama shows download progress. The first time takes a moment — after that you run it directly, the model stays cached.

*Screen: `ollama pull` showing the download progress bar.*

---

## 3. Run and chat (3:30–5:00)

```bash
ollama run llama3.2
```

This opens a chat right in your terminal. You type, it responds. No account, no API key, no data leaving your machine.

On GPU: Ollama auto-detects NVIDIA, AMD, and Intel GPUs. If you have a compatible GPU, it uses it automatically — no extra drivers to install, no manual configuration. Running on CPU works too, just a bit slower.

*Screen: live conversation in the terminal. Show a question and the response appearing word by word.*

---

## 4. Browser interface with Open WebUI (5:00–6:30)

Prefer a visual ChatGPT-like interface? Open WebUI integrates directly with Ollama. Install it with pip:

```bash
pip install open-webui
open-webui serve
```

Go to `http://localhost:8080`. Create a local account — the first account you create automatically becomes admin. Open WebUI detects Ollama and lists the models you've downloaded.

*Screen: browser opening Open WebUI, creating account, picking a model, and sending a message.*

---

## 5. Commands you'll use all the time (6:30–7:00)

| What to do | Command |
|---|---|
| List installed models | `ollama list` |
| Switch models | `ollama run qwen2.5:7b` |
| Delete a model | `ollama rm llama3.2` |

---

[OUTRO + CTA] (7:00–7:45)

That's all of it. No docker-compose, no custom script, no manual driver setup. One command installs, one downloads the model, one runs it.

Ollama is by far the simplest way to run AI locally — and once you try it, it's hard to go back to anything else.

If you want more videos on self-hosting and local AI, subscribe here. More is coming.

---

## Production notes

- Section 3 (running in terminal) is the heart of the video — record in real time, no cuts.
- Possible short version (Shorts, 60s): just install + pull + run.
- **Estimated length**: 7 minutes (~910 words / 130 wpm)
- **Total words**: ~910
- **Tone**: educational, direct, no fluff
- **Title suggestions**:
  1. "Run AI on Your PC in 2 Minutes (No Docker, No API)"
  2. "Ollama: The Easiest Way to Run AI Locally"
  3. "Free ChatGPT on Your Computer — No Cloud, No Account"
- **Thumbnail**: dark terminal with `ollama run llama3.2` in green, bold "2 MINUTES" text in red
