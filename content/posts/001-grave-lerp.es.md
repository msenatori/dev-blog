+++
date = '2026-02-03T19:13:57-03:00'
draft = false
title = 'Reto #01: Grave Lerp'
tags = ["Godot", "Devlog", "Reto"]
cover = { image = "images/001/banner.png", alt = "Boceto original del juego", caption = "El plan original en papel" }
+++

La idea es simple: romper el hielo y completar un ciclo de desarrollo entero (idea, código, bugfix, deploy) en una sola tarde.

### Theme & Objetivo
El jugador es un objeto que sigue al mouse con un delay suave (**lerp**) y debe esquivar sierras circulares.

Queremos aprender cómo hacer un jueguito rápido usando algunos `RigidBody` y un `CharacterBody`. Es lo primero que me imagino; seguro existen miles de formas de hacerlo, pero estoy intentando resolverlo **como me parece al momento de leerlo**. Obviamente este post fue posterior al desarrollo, pero la proxima quizas pongo el post antes y el resultado despues para ver que paso.

### La Lógica
La idea del juego es mover al player y esquivar las sierras que vayan cayendo del cielo.
Como seguro va a ser muy fácil de esquivar, pienso hacer que el juego vaya mucho más rápido, **escalando la velocidad de respawn** de los enemigos. Supongo que para hacerlo un poco más entretenido pondré un timer para saber hasta dónde llegaste.

### El Bug del Día:
Me encontré con un problema clásico de Godot 4: Las sierras no detectaban el piso.
Resulta que que existe una propiedad dentro de los staticbody que activa la colision.
1. Configurar el **Contact Monitor** en el RigidBody para que detecte el impacto.
2. Setear el **Max Contact Report** en 1

### Tareas Completadas

- [x] Crear escena `Node2D` principal y atachear un Level Controller para que orqueste todo.
- [x] Agregar un canvas layer para setear toda la ui.
- [x] Agregar lógica de **Instanciar/Borrar** enemigos (sin Arrays complejos, pura performance web).
- [x] `CharacterBody` con movimiento suavizado (Lerp).
- [x] Agregar botón de *Reset Level* (Game Over instantáneo).
- [x] Agregar un TileMap para armar el nivel rápido.

### Aclaraciones
- Posiblemente no tenga sonido, no creo que llegue (y no llegué 😅).
- No me sente a mirar como configurar un theme complejo, es algo pendiente para la proxima.

### Jugar
El juego corre nativo en el navegador.

[👉 Jugar en Itch.io](https://arcou.itch.io/001-grave-lerp)

---
**Assets:** [Pixel Adventure 1](https://pixelfrog-assets.itch.io/pixel-adventure-1) por Pixel Frog.

**Tiempo aproximado:** 2 horas.