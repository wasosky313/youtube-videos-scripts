# Como rodar IA localmente com Ollama (sem API, sem nuvem)

**Duração estimada:** 6–8 min
**Idioma:** Português
**Ferramenta principal:** Ollama

---

[GANCHO] (0:00–0:15)

Você já tentou rodar IA localmente, foi atrás de tutorial, clonou repositório, editou docker-compose — e desistiu no meio do caminho? Eu também. Até descobrir o Ollama. Instalei tudo em dois minutos. Deixa eu te mostrar.

*Tela: terminal mostrando `ollama run llama3.2` respondendo uma pergunta em tempo real.*

---

[INTRO / PROMESSA] (0:15–0:45)

O problema com a maioria das soluções de IA local é que elas assumem que você já entende de Docker, containers e configuração de drivers. É muita complexidade pra chegar num resultado que deveria ser simples.

O Ollama remove tudo isso. Um comando instala. Um comando baixa o modelo. Um comando roda. Hoje você sai daqui com um LLM funcionando 100% no seu computador — sem API, sem nuvem, sem dado saindo da sua máquina.

---

## 1. Instalar o Ollama (0:45–2:00)

No Linux e no Mac, você abre o terminal e roda isso:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Só isso. Esse comando baixa e instala o Ollama, incluindo o servidor que vai gerenciar seus modelos em background.

No Windows, tem um instalador gráfico — link na descrição, é um clique só.

Pra confirmar que funcionou:

```bash
ollama --version
```

Apareceu um número? Tá pronto. Sem reiniciar, sem configurar nada.

*Tela: terminal rodando o curl e mostrando `ollama --version` com a versão instalada.*

---

## 2. Escolher e baixar um modelo (2:00–3:30)

Três opções, dependendo da sua máquina:

- **llama3.2** — da Meta, 3B de parâmetros, leve. Funciona bem até em notebook sem GPU.
- **qwen2.5:7b** — meu favorito pra uso geral. Mais capaz, ainda razoável em memória.
- **gemma3** — do Google, excelente pra código.

Se você não sabe qual escolher, começa com o llama3.2:

```bash
ollama pull llama3.2
```

O Ollama mostra o progresso do download. Na primeira vez demora um pouco — na próxima você roda direto, o modelo fica salvo.

*Tela: `ollama pull` mostrando a barra de progresso do download.*

---

## 3. Rodar e conversar (3:30–5:00)

```bash
ollama run llama3.2
```

Abre um chat direto no terminal. Você digita, ele responde. Sem conta, sem API key, sem nada saindo do seu computador.

E GPU: o Ollama detecta automaticamente NVIDIA, AMD e Intel. Se você tiver uma GPU compatível, ele já usa — sem instalar driver extra, sem configuração manual. Se rodar na CPU, funciona também, só um pouco mais devagar.

*Tela: conversa em tempo real no terminal. Mostra uma pergunta e a resposta aparecendo palavra por palavra.*

---

## 4. Interface no navegador com Open WebUI (5:00–6:30)

Prefere uma interface visual tipo ChatGPT? O Open WebUI integra direto com o Ollama. Instala com pip:

```bash
pip install open-webui
open-webui serve
```

Acessa em `http://localhost:8080`. Cria uma conta local — a primeira conta vira admin automaticamente. O Open WebUI já detecta o Ollama e lista os modelos que você baixou.

*Tela: navegador abrindo o Open WebUI, criando conta, escolhendo modelo e mandando uma mensagem.*

---

## 5. Comandos que você vai usar sempre (6:30–7:00)

| O que fazer | Comando |
|---|---|
| Ver modelos instalados | `ollama list` |
| Trocar de modelo | `ollama run qwen2.5:7b` |
| Apagar um modelo | `ollama rm llama3.2` |

---

[CIERRE + CTA] (7:00–7:45)

Isso é tudo. Sem docker-compose, sem script, sem configuração de driver. Um comando instala, um baixa o modelo, um roda.

O Ollama é de longe a forma mais simples de ter IA local — e depois que você experimenta, é difícil voltar pra qualquer outra coisa.

Se você quer mais vídeos sobre self-hosting e IA local, se inscreve aqui. Tem bastante coisa vindo.

---

## Notas de produção

- A seção 3 (rodar no terminal) é o coração do vídeo — grava em tempo real, sem corte.
- Possível versão curta (Shorts de 60s): só instalar + pull + run.
- **Duração estimada**: 7 minutos (~910 palavras / 130 ppm)
- **Palavras totais**: ~910
- **Tono**: educativo, direto, sem enrolação
- **Sugestões de título**:
  1. "Roda IA no seu PC em 2 minutos (sem Docker, sem API)"
  2. "Ollama: a forma mais fácil de ter IA local"
  3. "ChatGPT no seu computador, de graça e sem nuvem"
- **Thumbnail**: terminal escuro com `ollama run llama3.2` em verde, texto "2 MINUTOS" em vermelho em destaque
