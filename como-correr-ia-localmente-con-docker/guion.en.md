# How to Run AI Locally with Docker (No API, No Cloud)

**Estimated length:** 8–10 min
**Language:** English
**Repo shown in the video:** ai-containers (start.sh + docker-compose)

---

## 1. Hook (0:00–0:20)

> "Did you know you can have your own ChatGPT running on your computer, without paying a cent in API costs and without sending your data to the cloud? I'll show you how in under 5 minutes."

*Screen: show the Open WebUI interface already working (spoiler of the final result) to build interest.*

## 2. What we're going to build (0:20–1:00)

- A language model (LLM) running 100% locally with Docker.
- A ChatGPT-like chat interface (Open WebUI).
- Works on Linux, Windows, and Mac.
- Also works without a GPU (slower), and if you have an Intel/AMD GPU on Linux, it accelerates.

## 3. Requirements (1:00–1:45)

- Docker installed and running.
  - Windows/Mac → Docker Desktop.
  - Linux → Docker Engine.
- ~6GB of free disk space.

*Screen: show `docker --version` in the terminal to confirm it's installed.*

## 4. Clone the repo (1:45–2:15)

```bash
git clone <repo-url>
cd ai-containers
```

*Screen: terminal cloning and `cd`-ing into the folder.*

## 5. (Optional) Vulkan drivers if you have an Intel/AMD GPU on Linux (2:15–2:45)

```bash
sudo apt install -y mesa-vulkan-drivers vulkan-tools libvulkan1
```

> "If you don't have a GPU, or you're on Windows/Mac, skip this step — the script works the same on CPU."

## 6. Run the script (2:45–4:30) — the heart of the video

```bash
./start.sh
```

- Show the interactive menu picking a model:
  - Qwen2.5 3B → no GPU needed, fast.
  - Qwen2.5 7B → recommended, balanced.
  - Qwen2.5 14B / 32B → if you have a GPU with enough VRAM.
- Explain on camera: "The script already knows how much VRAM each model needs, so if you're not sure which to pick, just go with the one higher up the list."
- Answer "y" or "N" to the GPU question.

*Screen: record the full interactive `select` menu, in real time, without cutting — this is the most "demo" part of the video.*

## 7. Wait for the model download (4:30–5:15)

```bash
docker compose logs -f llama-server
```

> "This only happens the first time — the model gets downloaded and stays cached."

*Screen: speed up the clip (timelapse) until `model loaded` and `listening on http://0.0.0.0:8080` show up.*

## 8. Open the interface and chat (5:15–6:15)

- Go to `http://localhost:3000`.
- Create a local account (the first account created becomes admin).
- Pick the model and send a live test message.

*Screen: browser, create account, type something like "Explain what Docker is in 2 lines" and show the response in real time.*

## 9. Bonus — Verify the GPU is actually being used (6:15–7:15) *(optional, cut if the video runs long)*

```bash
docker run --rm --device /dev/dri ghcr.io/ggml-org/llama.cpp:server-vulkan --list-devices
```

- Intel: `sudo intel_gpu_top`
- AMD: `sudo radeontop`

> "If you see GPU usage spike when you send a message, that confirms it's really accelerating."

## 10. Switch models (7:15–7:45)

> "Want to try another model? Just run `./start.sh` again and pick a different one."

## 11. Useful commands (7:45–8:15)

| What you want to do | Command |
|---|---|
| Stop everything | `docker compose down` |
| Stop and wipe data (model, history) | `docker compose down -v` |
| View logs | `docker compose logs -f` |

## 12. Outro + CTA (8:15–9:00)

> "And that's it — your own AI assistant, running locally, with no hidden costs and no account anywhere. The repo is in the description. If this helped you, drop a like and subscribe, more self-hosting videos are coming."

---

## Production notes

- Steps 6–8 are the most worth recording in real time (they're the "wow" of the video); the rest can be voiceover over screen captures.
- Possible short-form version (Shorts/Reels, 60s) focused only on steps 6–8.
