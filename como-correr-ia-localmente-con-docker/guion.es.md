# Cómo correr IA localmente con Docker (sin API, sin nube)

**Duración estimada:** 8–10 min
**Idioma:** Español
**Repo mostrado en el video:** ai-containers (start.sh + docker-compose)

---

## 1. Hook (0:00–0:20)

> "¿Sabías que puedes tener tu propio ChatGPT corriendo en tu compu, sin pagar un centavo de API y sin mandar tus datos a la nube? Te muestro cómo en menos de 5 minutos."

*Pantalla: mostrar la interfaz de Open WebUI ya funcionando (spoiler del resultado final) para generar interés.*

## 2. Qué vamos a lograr (0:20–1:00)

- Un modelo de lenguaje (LLM) corriendo 100% local con Docker.
- Interfaz de chat tipo ChatGPT (Open WebUI).
- Funciona en Linux, Windows y Mac.
- Sin GPU también funciona (más lento), y si tienes GPU Intel/AMD en Linux, se acelera.

## 3. Requisitos (1:00–1:45)

- Tener Docker instalado y corriendo.
  - Windows/Mac → Docker Desktop.
  - Linux → Docker Engine.
- ~6GB libres en disco.

*Pantalla: mostrar `docker --version` en la terminal para confirmar que está instalado.*

## 4. Clonar el repo (1:45–2:15)

```bash
git clone <url-del-repo>
cd ai-containers
```

*Pantalla: terminal clonando y haciendo `cd`.*

## 5. (Opcional) Drivers Vulkan si tienes GPU Intel/AMD en Linux (2:15–2:45)

```bash
sudo apt install -y mesa-vulkan-drivers vulkan-tools libvulkan1
```

> "Si no tienes GPU o estás en Windows/Mac, te saltas este paso — el script funciona igual en CPU."

## 6. Ejecutar el script (2:45–4:30) — el corazón del video

```bash
./start.sh
```

- Muestra el menú interactivo eligiendo modelo:
  - Qwen2.5 3B → sin GPU, rápido.
  - Qwen2.5 7B → recomendado, balance.
  - Qwen2.5 14B / 32B → si tienes GPU con VRAM.
- Explica en cámara: "El script ya sabe cuánta VRAM necesita cada modelo, así que si no sabes cuál elegir, agarra el de más arriba en la lista."
- Responde "s" o "N" a la pregunta de GPU.

*Pantalla: grabar el `select` interactivo completo, en tiempo real, sin cortar — es la parte más "demo" del video.*

## 7. Esperar la descarga del modelo (4:30–5:15)

```bash
docker compose logs -f llama-server
```

> "Esto solo pasa la primera vez — el modelo se descarga y queda guardado."

*Pantalla: acelerar el clip (timelapse) hasta que aparezca `model loaded` y `listening on http://0.0.0.0:8080`.*

## 8. Abrir la interfaz y chatear (5:15–6:15)

- Ir a `http://localhost:3000`.
- Crear cuenta local (la primera cuenta es admin).
- Elegir el modelo y mandar un mensaje de prueba en vivo.

*Pantalla: navegador, crear cuenta, escribir algo tipo "Explícame qué es Docker en 2 líneas" y mostrar la respuesta en tiempo real.*

## 9. Bonus — Verificar que está usando la GPU (6:15–7:15) *(opcional, cortar si el video se alarga)*

```bash
docker run --rm --device /dev/dri ghcr.io/ggml-org/llama.cpp:server-vulkan --list-devices
```

- Intel: `sudo intel_gpu_top`
- AMD: `sudo radeontop`

> "Si ves que el uso de GPU sube cuando mandas un mensaje, confirma que está acelerando de verdad."

## 10. Cambiar de modelo (7:15–7:45)

> "¿Quieres probar otro modelo? Solo corres `./start.sh` de nuevo y eliges otro."

## 11. Comandos útiles (7:45–8:15)

| Qué | Comando |
|---|---|
| Detener todo | `docker compose down` |
| Borrar todo (modelo, historial) | `docker compose down -v` |
| Ver logs | `docker compose logs -f` |

## 12. Cierre + CTA (8:15–9:00)

> "Y eso es todo — tu propio asistente de IA, corriendo local, sin costos ocultos ni cuentas en ningún lado. El repo está en la descripción. Si te sirvió, dale like y suscríbete, que vienen más videos sobre self-hosting."

---

## Notas de producción

- Los pasos 6–8 son los que más vale la pena grabar en tiempo real (son el "wow" del video); el resto puede ir con voz en off sobre capturas de pantalla.
- Posible versión corta (Shorts/Reels de 60s) enfocada solo en los pasos 6–8.
