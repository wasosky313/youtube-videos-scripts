# Cómo correr IA localmente con Ollama (sin API, sin nube)

**Duración estimada:** 6–8 min
**Idioma:** Español
**Herramienta principal:** Ollama

---

[GANCHO] (0:00–0:15)

Intentaste correr IA localmente, buscaste tutoriales, clonaste repos, editaste docker-compose... y lo abandonaste a mitad. Yo también. Hasta que encontré Ollama. Instalé todo en dos minutos. Te muestro cómo.

*Pantalla: terminal mostrando `ollama run llama3.2` respondiendo una pregunta en tiempo real.*

---

[INTRO / PROMESA] (0:15–0:45)

El problema con la mayoría de las soluciones de IA local es que asumen que ya entendés de Docker, containers y configuración de drivers. Es demasiada complejidad para llegar a algo que debería ser simple.

Ollama elimina todo eso. Un comando instala. Un comando baja el modelo. Un comando lo corre. Hoy salís de acá con un LLM funcionando 100% en tu computadora — sin API, sin nube, sin que tus datos salgan a ningún lado.

---

## 1. Instalar Ollama (0:45–2:00)

En Linux y Mac, abrís la terminal y corrés esto:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Solo eso. Este comando baja e instala Ollama, incluyendo el servidor que va a gestionar tus modelos en background.

En Windows tenés dos caminos, elegís el que prefieras:

- **Instalador gráfico:** bajás `OllamaSetup.exe` desde ollama.com/download/windows — link en la descripción — y hacés doble clic. Un solo instalador, sin pasos raros.
- **Winget (si preferís línea de comandos):** abrís PowerShell y corrés:

```powershell
winget install Ollama.Ollama
```

En ambos casos, Ollama queda corriendo en background apenas termina la instalación — no hace falta abrir nada más.

Para confirmar que funcionó, en Linux/Mac usás la terminal y en Windows PowerShell o CMD:

```bash
ollama --version
```

¿Apareció un número? Listo. Sin reiniciar, sin configurar nada.

*Pantalla: en Linux/Mac, terminal corriendo el curl. En Windows, el instalador gráfico terminando y PowerShell mostrando `ollama --version` con la versión instalada.*

---

## 2. Elegir y bajar un modelo (2:00–3:30)

Tres opciones según tu máquina:

- **llama3.2** — de Meta, 3B de parámetros, liviano. Funciona bien hasta en notebook sin GPU.
- **qwen2.5:7b** — mi favorito para uso general. Más capaz, todavía razonable en memoria.
- **gemma3** — de Google, excelente para código.

Si no sabés cuál elegir, empezá con llama3.2:

```bash
ollama pull llama3.2
```

Ollama muestra el progreso de la descarga. La primera vez tarda un poco — la próxima corrés directo, el modelo queda guardado.

*Pantalla: `ollama pull` mostrando la barra de progreso de la descarga.*

---

## 3. Correr y chatear (3:30–5:00)

```bash
ollama run llama3.2
```

Abre un chat directo en la terminal. Escribís, él responde. Sin cuenta, sin API key, sin nada saliendo de tu computadora.

Y sobre GPU: Ollama detecta automáticamente NVIDIA, AMD e Intel. Si tenés GPU compatible, ya la usa — sin instalar driver extra, sin configuración manual. Correr en CPU también funciona, solo un poco más lento.

*Pantalla: conversación en tiempo real en la terminal. Mostrar una pregunta y la respuesta apareciendo palabra por palabra.*

---

## 4. Interfaz en el navegador con Open WebUI (5:00–6:30)

¿Preferís una interfaz visual tipo ChatGPT? Open WebUI se integra directo con Ollama. Instalás con pip:

```bash
pip install open-webui
open-webui serve
```

Entrás en `http://localhost:8080`. Creás una cuenta local — la primera cuenta pasa a ser admin automáticamente. Open WebUI ya detecta Ollama y lista los modelos que bajaste.

*Pantalla: navegador abriendo Open WebUI, creando cuenta, eligiendo modelo y mandando un mensaje.*

---

## 5. Comandos que vas a usar siempre (6:30–7:00)

| Qué hacer | Comando |
|---|---|
| Ver modelos instalados | `ollama list` |
| Cambiar de modelo | `ollama run qwen2.5:7b` |
| Borrar un modelo | `ollama rm llama3.2` |

---

[CIERRE + CTA] (7:00–7:45)

Eso es todo. Sin docker-compose, sin script, sin configurar drivers. Un comando instala, uno baja el modelo, uno lo corre.

Ollama es de lejos la forma más simple de tener IA local — y una vez que lo probás, es difícil volver a cualquier otra cosa.

Si querés más videos sobre self-hosting e IA local, suscribite acá. Vienen más.

---

## Notas de producción

- La sección 3 (correr en terminal) es el corazón del video — grabá en tiempo real, sin cortes.
- Posible versión corta (Shorts de 60s): solo instalar + pull + run.
- **Duración estimada**: 7 minutos (~910 palabras / 130 ppm)
- **Palabras totales**: ~910
- **Tono**: educativo, directo, sin vueltas
- **Sugerencias de título**:
  1. "Corré IA en tu PC en 2 minutos (sin Docker, sin API)"
  2. "Ollama: la forma más fácil de tener IA local"
  3. "ChatGPT en tu computadora, gratis y sin nube"
- **Thumbnail**: terminal oscura con `ollama run llama3.2` en verde, texto "2 MINUTOS" en rojo destacado
