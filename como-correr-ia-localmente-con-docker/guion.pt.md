# Como rodar IA localmente com Docker (sem API, sem nuvem)

**Duração estimada:** 8–10 min
**Idioma:** Português
**Repo mostrado no vídeo:** ai-containers (start.sh + docker-compose)

---

## 1. Gancho (0:00–0:20)

> "Você sabia que dá pra ter seu próprio ChatGPT rodando no seu computador, sem pagar um centavo de API e sem mandar seus dados pra nuvem? Te mostro como em menos de 5 minutos."

*Tela: mostrar a interface do Open WebUI já funcionando (spoiler do resultado final) para gerar interesse.*

## 2. O que vamos alcançar (0:20–1:00)

- Um modelo de linguagem (LLM) rodando 100% local com Docker.
- Interface de chat tipo ChatGPT (Open WebUI).
- Funciona em Linux, Windows e Mac.
- Sem GPU também funciona (mais lento), e se você tiver GPU Intel/AMD no Linux, acelera.

## 3. Requisitos (1:00–1:45)

- Ter o Docker instalado e rodando.
  - Windows/Mac → Docker Desktop.
  - Linux → Docker Engine.
- ~6GB livres em disco.

*Tela: mostrar `docker --version` no terminal para confirmar que está instalado.*

## 4. Clonar o repositório (1:45–2:15)

```bash
git clone <url-do-repositorio>
cd ai-containers
```

*Tela: terminal clonando e fazendo `cd`.*

## 5. (Opcional) Drivers Vulkan se você tiver GPU Intel/AMD no Linux (2:15–2:45)

```bash
sudo apt install -y mesa-vulkan-drivers vulkan-tools libvulkan1
```

> "Se você não tem GPU ou está no Windows/Mac, pode pular essa etapa — o script funciona igual na CPU."

## 6. Rodar o script (2:45–4:30) — o coração do vídeo

```bash
./start.sh
```

- Mostra o menu interativo escolhendo o modelo:
  - Qwen2.5 3B → sem GPU, rápido.
  - Qwen2.5 7B → recomendado, equilibrado.
  - Qwen2.5 14B / 32B → se você tiver GPU com VRAM.
- Explica na câmera: "O script já sabe quanta VRAM cada modelo precisa, então se você não souber qual escolher, pega o de mais acima na lista."
- Responde "s" ou "N" para a pergunta sobre GPU.

*Tela: gravar o menu `select` interativo completo, em tempo real, sem cortar — é a parte mais "demo" do vídeo.*

## 7. Esperar o download do modelo (4:30–5:15)

```bash
docker compose logs -f llama-server
```

> "Isso só acontece na primeira vez — o modelo é baixado e fica salvo."

*Tela: acelerar o clipe (timelapse) até aparecer `model loaded` e `listening on http://0.0.0.0:8080`.*

## 8. Abrir a interface e conversar (5:15–6:15)

- Ir em `http://localhost:3000`.
- Criar conta local (a primeira conta criada vira admin).
- Escolher o modelo e mandar uma mensagem de teste ao vivo.

*Tela: navegador, criar conta, escrever algo tipo "Explica o que é Docker em 2 linhas" e mostrar a resposta em tempo real.*

## 9. Bônus — Verificar se está usando a GPU (6:15–7:15) *(opcional, cortar se o vídeo ficar longo)*

```bash
docker run --rm --device /dev/dri ghcr.io/ggml-org/llama.cpp:server-vulkan --list-devices
```

- Intel: `sudo intel_gpu_top`
- AMD: `sudo radeontop`

> "Se você ver o uso da GPU subir quando manda uma mensagem, confirma que está acelerando de verdade."

## 10. Trocar de modelo (7:15–7:45)

> "Quer testar outro modelo? É só rodar `./start.sh` de novo e escolher outro."

## 11. Comandos úteis (7:45–8:15)

| O que você quer fazer | Comando |
|---|---|
| Parar tudo | `docker compose down` |
| Parar e apagar tudo (modelo, histórico) | `docker compose down -v` |
| Ver logs | `docker compose logs -f` |

## 12. Encerramento + CTA (8:15–9:00)

> "E é isso — seu próprio assistente de IA, rodando local, sem custo escondido nem conta em lugar nenhum. O repositório está na descrição. Se ajudou, deixa o like e se inscreve, que vêm mais vídeos sobre self-hosting."

---

## Notas de produção

- As etapas 6–8 são as que mais vale a pena gravar em tempo real (são o "uau" do vídeo); o resto pode ir com narração sobre capturas de tela.
- Possível versão curta (Shorts/Reels de 60s) focada só nas etapas 6–8.
