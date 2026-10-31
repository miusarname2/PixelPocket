<div align="center">

# 🎮 PixelPocket

### *El mejor simulador de juegos* para tu LEGO® MINDSTORMS® NXT

Seis minijuegos retro, un reproductor de música chiptune y un menú en una sola consola de bolsillo hecha con un ladrillo NXT.

![Plataforma](https://img.shields.io/badge/plataforma-LEGO%20NXT-orange)
![Lenguaje](https://img.shields.io/badge/lenguaje-NXC-blue)
![Juegos](https://img.shields.io/badge/juegos-6-brightgreen)
![Pantalla](https://img.shields.io/badge/pantalla-100×64%20px-lightgrey)

</div>

---

## 📖 Tabla de contenidos

1. [¿Qué es PixelPocket?](#-qué-es-pixelpocket)
2. [Características](#-características)
3. [Los juegos](#-los-juegos)
4. [Requisitos](#-requisitos)
5. [Instalación](#-instalación)
6. [Cómo usarlo](#-cómo-usarlo)
7. [Guía de cada juego](#-guía-de-cada-juego)
8. [Estructura del código](#-estructura-del-código)
9. [Detalles técnicos](#-detalles-técnicos)
10. [Personalización](#-personalización)
11. [Solución de problemas](#-solución-de-problemas)
12. [Limitaciones conocidas](#-limitaciones-conocidas)
13. [Ideas para el futuro](#-ideas-para-el-futuro)
14. [Contribuir](#-contribuir)
15. [Licencia](#-licencia)

---

## 🕹️ ¿Qué es PixelPocket?

**PixelPocket** es una consola de minijuegos para el ladrillo **LEGO MINDSTORMS NXT**, escrita completamente en **NXC (Not eXactly C)**. Usa únicamente la pantalla monocromática de 100×64 píxeles, los botones del ladrillo y el altavoz integrado: no necesita sensores, motores ni hardware extra.

Al encender el programa aparece un menú con el título *"El mejor simulador de Juegos"* desde donde puedes elegir entre seis experiencias distintas: un Tetris, un RPG por turnos, dos juegos de plataformas, un reproductor de música y una culebrita clásica.

> Repositorio: <https://github.com/miusarname2/PixelPocket>

---

## ✨ Características

- 🎲 **6 módulos de juego** en un único programa.
- 🎵 **Música chiptune integrada** generada por código (sin archivos de sonido), con 5 melodías propias.
- 🖼️ **Gráficos 100% por código**: sprites de píxeles, plataformas, escaleras, perspectiva en primera persona y más.
- 🎛️ **Controles de 4 botones**: izquierda, derecha, centro (ENTER) y salida (EXIT).
- 📋 **Pantalla de instrucciones** antes de cada juego.
- 🔁 **Navegación fluida**: de cualquier juego puedes volver al menú.
- 📦 **Un solo archivo fuente**, fácil de leer, modificar y compilar.

---

## 🎮 Los juegos

| # | Juego | Género | Descripción corta |
|---|-------|--------|-------------------|
| 0 | **TETRAS** | Puzles | Tetris con tablero de 8×10, 7 piezas y rotación. |
| 1 | **MINI QUEST** | RPG por turnos | 4 batallas contra monstruos con ATK / DEF / POT / MAG. |
| 2 | **BEAR RUN** | Plataformas | Esquiva barriles y salta sobre el oso para vencerlo. |
| 3 | **SKY HOP** | Plataformas | Sube por las plataformas, esquiva bichos y llega a la estrella. |
| 4 | **TUNE BOX** | Música | Reproductor con 5 canciones de ~2 minutos cada una. |
| 5 | **CULEBRITA** | Arcade | Snake clásico con control de giros por doble toque. |

---

## 🧰 Requisitos

### Hardware

- Un ladrillo **LEGO MINDSTORMS NXT** (NXT 1.0 o NXT 2.0).
- Cable **USB** (o adaptador **Bluetooth**) para transferir el programa.
- Pilas AA o batería recargable del NXT con carga suficiente.

### Software

Necesitas **una** de estas herramientas para compilar y cargar el programa:

| Herramienta | Sistema | Comentario |
|-------------|---------|------------|
| [**BricxCC**](https://bricxcc.sourceforge.net/) | Windows | IDE gráfico, la opción más sencilla. |
| [**NBC / NXC**](https://bricxcc.sourceforge.net/nbc/) | Windows, macOS, Linux | Compilador por línea de comandos. |
| [**NeXTTool**](https://bricxcc.sourceforge.net/utilities.html) | Windows, macOS, Linux | Para descargar archivos al NXT desde terminal. |

> 💡 El programa usa solo funciones estándar de NXC (`TextOut`, `NumOut`, `LineOut`, `RectOut`, `CircleOut`, `PointOut`, `PlayTone`, `ButtonPressed`, `Wait`, `Stop`), por lo que **no requiere firmware mejorado** del NXT. Si tu compilador reporta alguna función no soportada, prueba con la última versión del firmware estándar de LEGO.

---

## 📥 Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/miusarname2/PixelPocket.git
cd PixelPocket
```

### 2. Opción A: con BricxCC (recomendada para Windows)

1. Instala y abre **BricxCC**.
2. Conecta el NXT por USB y enciéndelo.
3. En BricxCC ve a **Compile → Firmware / Brick…** y selecciona *NXT* como tipo de ladrillo y *USB* (o *Bluetooth*) como puerto.
4. Abre el archivo fuente del proyecto (`.nxc`) con **File → Open**.
5. Pulsa **Compile → Download** (o el icono de descarga) para compilarlo y enviarlo al NXT.
6. En el ladrillo, ve a **My Files → Software Files** y ejecuta **PixelPocket**.

### 3. Opción B: con línea de comandos (Windows / macOS / Linux)

Compila el programa con `nbc` y descárgalo con la opción `-d`:

```bash
# Compilar y descargar por USB
nbc -d -S=usb PixelPocket.nxc

# Solo compilar a un ejecutable .rxe
nbc PixelPocket.nxc -O=PixelPocket.rxe
```

Si prefieres separar los pasos, descarga el `.rxe` con NeXTTool:

```bash
nexttool /COM=usb -download=PixelPocket.rxe
```

Luego ejecútalo desde el menú del NXT: **My Files → Software Files → PixelPocket**.

> ℹ️ El nombre del archivo fuente puede variar según cómo lo hayas guardado en el repositorio. Ajusta los comandos al nombre real de tu `.nxc`.

### 4. Opción C: por Bluetooth

1. Empareja el NXT con tu computadora desde la configuración Bluetooth del sistema.
2. En BricxCC selecciona el puerto COM asociado (o usa `-S=bt` / `/COM=<puerto>` en la línea de comandos).
3. Descarga el programa como en las opciones anteriores.

---

## 🚀 Cómo usarlo

### Controles generales

| Botón del NXT | Acción en el menú |
|---------------|-------------------|
| ◀ **Izquierda** | Elemento anterior de la lista |
| ▶ **Derecha** | Elemento siguiente de la lista |
| ⬤ **ENTER (naranja)** | Abrir el juego seleccionado |
| ■ **EXIT (gris oscuro)** | Cerrar PixelPocket (detiene el programa) |

### Flujo de uso

1. Al iniciar verás el título y una lista de juegos con el cursor `>`.
2. Muévete con **izquierda/derecha** (la lista es circular).
3. Pulsa **ENTER** para abrir el juego: primero aparece una **pantalla de instrucciones**.
4. Vuelve a pulsar **ENTER** (*"ENTER TO START"*) para empezar a jugar.
5. Usa **EXIT** dentro del juego para volver al menú.
6. Al terminar una partida, pulsa **ENTER** para regresar al menú.

---

## 🎯 Guía de cada juego

### 🧱 TETRAS

Tetris adaptado a la pantalla del NXT.

- **Tablero:** 8 columnas × 10 filas, con celdas de 5×5 píxeles.
- **Piezas:** las 7 clásicas (I, O, T, L, J, S, Z) con 4 rotaciones.
- **Caída:** la pieza baja una fila cada 500 ms.
- **Puntuación:** al limpiar filas se suman `filas² × 10` puntos, así que limpiar varias a la vez rinde mucho más.
- **Panel lateral:** muestra el puntaje (`SCORE`) y las líneas completadas (`LINES`).
- **Fin de juego:** cuando una pieza nueva no puede aparecer.

| Botón | Acción |
|-------|--------|
| ◀ / ▶ | Mover la pieza |
| ENTER | Rotar |
| EXIT | Volver al menú |

---

### ⚔️ MINI QUEST

Un pequeño RPG por turnos con cuatro combates consecutivos.

**Enemigos (en orden):** Slime → Cave Bat → Golem → Wisp.

**Reglas:**

- Empiezas con **10 HP**, **3 pociones** y **4 MP**.
- La vida del enemigo crece con cada victoria (`4 + 2 × victorias`) y también su daño (`1 + victorias`).
- Tras cada victoria recuperas **+1 poción** (hasta 3) y **+2 MP** (hasta 4).
- Ganas la aventura al derrotar a los **4 enemigos**.

**Acciones** (elígelas con ◀/▶ y confirma con ENTER):

| Acción | Efecto |
|--------|--------|
| **ATK** | Ataque normal: 3 de daño al enemigo. |
| **DEF** | Te defiendes: reduces en 2 el daño del contraataque (mínimo 1). |
| **POT** | Usas una poción: curas 4 HP (máximo 10). |
| **MAG** | Hechizo: 5 de daño, cuesta 2 MP. |

> Si usas una acción sin recursos (por ejemplo, POT sin pociones) sonará un tono de error y no perderás el turno.

---

### 🐻 BEAR RUN

Juego de plataformas con estilo *arcade* clásico.

- **Objetivo:** vencer al oso saltando **sobre él desde arriba**.
- **Peligros:** un barril que rueda por las plataformas y el propio oso (si lo tocas de lado pierdes una vida).
- **Vidas:** 3. Al perder una vida reapareces en la esquina inferior izquierda.
- **Puntuación:** cuenta tus pasos (`STEPS`), con un bonus de +100 al vencer al oso.

| Botón | Acción |
|-------|--------|
| ◀ / ▶ | Correr |
| ENTER | Saltar |
| EXIT | Volver al menú |

---

### ⭐ SKY HOP

Plataformas verticales: sube hasta la cima y alcanza la estrella.

- **Objetivo:** llegar a la estrella en la esquina superior derecha.
- **Enemigo:** un bicho patrulla la plataforma central. Puedes **aplastarlo cayendo sobre él** (suma a `BUGS`) o esquivarlo.
- **Vidas:** 3.

| Botón | Acción |
|-------|--------|
| ◀ / ▶ | Correr |
| ENTER | Saltar |
| EXIT | Volver al menú |

---

### 🎶 TUNE BOX

Reproductor de música con cinco melodías originales generadas por código.

| Canción | Característica |
|---------|----------------|
| **PIXEL RUN** | Frase de 8 notas, ritmo animado. |
| **STAR QUEST** | Tono aventurero. |
| **CAVE LIGHT** | Ambiente misterioso. |
| **BEEP PARADE** | Alegre y saltarina. |
| **NIGHT SHADE** | La más larga: frase de 16 notas y 64 pasos. |

- Cada canción se repite hasta alcanzar unas **256 notas**, lo que equivale a **~2 minutos** de reproducción.
- La melodía varía por secciones: cada cierto número de compases sube una octava o baja una octava.
- Mientras suena se dibuja un **ecualizador animado** y se indica la **parte** actual.

| Botón | Acción |
|-------|--------|
| ◀ / ▶ | Cambiar de canción |
| ENTER | Reproducir |
| EXIT | Detener / volver al menú |

---

### 🐍 CULEBRITA

El clásico Snake con un esquema de control pensado para un ladrillo de solo dos botones de dirección.

- **Tablero:** cuadrícula de 20 × 10 celdas.
- **Velocidad:** un paso cada 320 ms.
- **Comida:** aparece en posiciones calculadas con un generador pseudoaleatorio simple.
- **Victoria:** llenar las 200 celdas (*"CULEBRA MASTER!"*).
- **Derrota:** chocar con una pared o con tu propio cuerpo.

**Controles por doble toque** (ventana de 600 ms):

| Entrada | Dirección |
|---------|-----------|
| ◀ (un toque) | Izquierda |
| ◀ ◀ (doble toque) | Arriba |
| ▶ (un toque) | Derecha |
| ▶ ▶ (doble toque) | Abajo |
| ENTER | Pausa / reanudar |
| EXIT | Volver al menú |

> No puedes invertir la dirección de golpe (por ejemplo, ir de derecha a izquierda directamente).

---

## 🗂️ Estructura del código

Todo el proyecto vive en un único archivo NXC, organizado por secciones:

```
PixelPocket.nxc
│
├── Constantes y variables globales
│     (tablero de Tetris, estado del RPG, plataformas, Snake, música)
│
├── 🎵 Sistema de música
│     ResetMusic · MusicPhraseNote · MusicLength · MusicPhraseLength
│     MusicNote · MusicTick · DrawSongPlayer · PlaySongPlayer
│
├── 🧱 Tetras
│     TetrominoCell · TetrisCollision · TetrisSpawn · TetrisClearLines
│     TetrisLock · DrawTetris · PlayTetris
│
├── 🖼️ Utilidades de dibujo y vistas
│     DrawBlock · DrawPlatform · DrawPixelSprite · DrawBear · DrawBug
│     ViewLeft/Right/Top/Bottom · DrawSideWall · DrawFrontWall
│
├── ⚔️ Mini Quest
│     DrawQuestBattle · PlayMiniQuest
│
├── 🐻 Bear Run
│     PlatformContains · FindLanding · IsSupported
│     DrawBarrelRun · ResetBarrel · PlayBarrelRun
│
├── ⭐ Sky Hop
│     DrawSkyHop · PlaySkyHop
│
├── 🐍 Culebrita
│     PlaceSnakeFood · DrawSnake · PauseSnake · PlaySnake
│
└── 🏠 Menú principal
      ShowGameInstructions · task main()
```

---

## 🔧 Detalles técnicos

- **Pantalla:** 100×64 píxeles, 1 bit por píxel. Todo el dibujo usa `LineOut`, `RectOut`, `CircleOut`, `PointOut` y `TextOut`; el relleno de bloques se hace con la función propia `DrawBlock`.
- **Sistema de coordenadas:** el origen `(0,0)` está en la esquina **inferior izquierda**, siguiendo el modelo de NXC.
- **Tetris con bitmasks:** cada fila del tablero se guarda como un `byte` donde cada bit es una celda. Las piezas se describen con la función `TetrominoCell`, que calcula las 4 rotaciones aplicando transformaciones de coordenadas sobre una cuadrícula de 4×4.
- **Sprites de 8×8:** el héroe y el oso se definen con una máscara de 8 filas (`HeroSpriteRow`, `BearSpriteRow`) y se escalan ×2.
- **Física de plataformas:** salto con velocidad vertical inicial, gravedad por fotograma, velocidad de caída máxima y detección de aterrizaje (`FindLanding`) contra cuatro superficies.
- **Música procedural:** cada canción es una frase corta (8 o 16 notas) que se expande a 32 o 64 pasos usando secciones que duplican o dividen la frecuencia (octava arriba/abajo). Se reproduce con `PlayTone`.
- **Música de fondo en los juegos:** `MusicTick(track, ticksPerNote)` hace sonar una nota cada cierto número de iteraciones del bucle principal sin bloquear el juego.
- **Snake:** el cuerpo se guarda en un arreglo `byte snakeCells[200]` con un índice lineal por celda (`y * 20 + x`).
- **Entrada:** se usa `ButtonPressed(..., false)` con antirrebote manual mediante `Wait` y bucles de espera a que se suelte el botón.
- **Salida del programa:** el botón **EXIT** en el menú llama a `Stop(true)`.

---

## 🎨 Personalización

Algunas ideas rápidas para modificar el proyecto:

| Quieres cambiar… | Dónde buscarlo |
|------------------|----------------|
| Velocidad de caída en Tetris | `fallClock >= 500` en `PlayTetris` |
| Tamaño del tablero de Tetris | Constantes `BOARD_W`, `BOARD_H`, `CELL` |
| Dificultad del Mini Quest | `enemyHP = 4 + questWins * 2` y `questDamage = 1 + questWins` |
| Número de vidas | `runnerLives`, `hopLives` en `PlayBarrelRun` / `PlaySkyHop` |
| Velocidad de la culebrita | `snakeClock < 320` en `PlaySnake` |
| Melodías | `MusicPhraseNote` (frecuencias en Hz) |
| Textos del menú | `task main()` y `ShowGameInstructions` |
| Añadir un séptimo juego | Crea `PlayTuJuego()`, súmalo en `ShowGameInstructions`, y amplía el menú (`% 6` → `% 7`) |

---

## 🩺 Solución de problemas

| Problema | Posible solución |
|----------|------------------|
| BricxCC no detecta el NXT | Revisa el cable, enciende el ladrillo y selecciona el puerto correcto (USB/COM). Instala el driver de LEGO si usas Windows. |
| Error de compilación por función desconocida | Actualiza BricxCC / NBC a la última versión disponible. |
| *"Not enough memory"* al descargar | Borra archivos antiguos desde **My Files** en el NXT. |
| El sonido no se oye | Sube el volumen en **Settings → Volume** del NXT. |
| Los botones responden con retraso | Es normal en juegos con música activa; suelta el botón antes de volver a pulsarlo. |
| El programa se cierra al pulsar EXIT en el menú | Es el comportamiento esperado: `EXIT` detiene la aplicación. |

---

## ⚠️ Limitaciones conocidas

- La pantalla es monocroma y muy pequeña, por lo que los gráficos son deliberadamente simples.
- No se guardan puntuaciones máximas entre sesiones.
- El generador de comida de Snake es determinista (la secuencia de posiciones es siempre la misma).
- Algunas rutinas heredadas (por ejemplo, las funciones de vista en primera persona `ViewLeft`, `DrawFrontWall` o `DrawBear`) están presentes pero no se usan en el menú actual; se mantienen como base para futuras ampliaciones.
- La música usa `PlayTone` del NXT, que es monofónica (una nota a la vez).

---

## 🔮 Ideas para el futuro

- [ ] Guardar puntuaciones máximas en un archivo del NXT.
- [ ] Modo de dos jugadores por Bluetooth.
- [ ] Niveles de dificultad en Tetras y Culebrita.
- [ ] Más canciones y un modo de reproducción aleatoria en Tune Box.
- [ ] Un modo de exploración de mazmorras en primera persona (aprovechando las rutinas de vista ya incluidas).
- [ ] Uso de sensores (táctil, ultrasónico) como controles alternativos.
- [ ] Menú de ajustes (volumen, velocidad, música activada/desactivada).

---

## 🤝 Contribuir

¡Las contribuciones son bienvenidas!

1. Haz un **fork** del repositorio.
2. Crea una rama para tu mejora: `git checkout -b feature/mi-mejora`
3. Haz tus cambios y prueba en un NXT real (o en un simulador).
4. Haz commit: `git commit -m "Añade mi mejora"`
5. Sube la rama: `git push origin feature/mi-mejora`
6. Abre un **Pull Request** describiendo qué cambia y por qué.

**Pautas sugeridas:**

- Mantén el estilo del código (nombres descriptivos, llaves en línea nueva, funciones cortas).
- Evita bloquear el bucle principal con `Wait` largos.
- Documenta cualquier juego nuevo en este README.

---

## 📄 Licencia

Aún no se ha definido una licencia para este proyecto. Si quieres que otras personas puedan usarlo, modificarlo y compartirlo, se recomienda añadir un archivo `LICENSE` (por ejemplo, **MIT**) a la raíz del repositorio.

---

## 🙌 Créditos

- Creado por [**miusarname2**](https://github.com/miusarname2).
- Hecho con ❤️ para el ladrillo **LEGO MINDSTORMS NXT** y el lenguaje **NXC** de John Hansen.
- *LEGO® y MINDSTORMS® son marcas registradas del Grupo LEGO, que no patrocina ni respalda este proyecto.*

<div align="center">

**¿Te gustó PixelPocket? ¡Dale una ⭐ al repositorio!**

[github.com/miusarname2/PixelPocket](https://github.com/miusarname2/PixelPocket)

</div>
