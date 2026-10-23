# Realidad Mixta – Juego de pelotas con webcam 🎯

Juego interactivo de realidad mixta para dos jugadores. La webcam detecta por color las **paletas** que sostiene cada jugador y la **canasta** de cada lado. Las pelotas caen desde las nubes y cada jugador tiene que llevarlas con su paleta hasta su canasta.

- La partida dura **90 segundos**.
- **Fase 1:** solo caen pelotas azules (**+1**).
- **Fase 2:** también aparecen pelotas rojas (**−1**).
- Gana el jugador con más puntos.

Funciona en el navegador con [OpenCV.js](https://docs.opencv.org/4.8.0/opencv.js) (detección de color) y [Matter.js](https://brm.io/matter-js/) (física).

---

## 📋 Requisitos

- Una **webcam**, o una cámara virtual como OBS o TouchDesigner.
- **Google Chrome**, o cualquier navegador moderno.
- **Python 3**, o cualquier otro servidor web local (ver más abajo).
- **Conexión a internet** al abrir la página, para descargar OpenCV.js y Matter.js.
- Dos **paletas** del mismo color y dos **canastas** de otro color bien distinto. Por ejemplo, paletas celestes o verdes y canastas rojas.

---

## 💻 Instalación

### 1. Descargar el proyecto

```bash
git clone https://github.com/BR1bit/Realidadmixta.git
cd Realidadmixta
```

También se puede descargar como ZIP desde GitHub (botón **Code → Download ZIP**) y descomprimirlo.

### 2. Levantar un servidor local

La app usa la cámara del navegador, que **solo funciona a través de un servidor**. Si abrís el `index.html` con doble clic, el navegador bloquea la cámara.

Desde la carpeta del proyecto:

```bash
python -m http.server 8080
```

> En Linux o macOS puede ser `python3 -m http.server 8080`.
>
> **Sin Python**, cualquiera de estas opciones sirve:
> - Node.js: `npx http-server -p 8080`
> - La extensión **Live Server** de VS Code

### 3. Abrir el juego

Entrá desde el navegador a **http://localhost:8080**

---

## 🎮 Cómo jugar

1. En el panel derecho elegí la cámara y tocá **Iniciar cámara**. Aceptá el permiso del navegador.
2. **Calibrar las paletas:** tocá **🎯 Calibrar paleta** y hacé clic sobre una paleta en la imagen.
3. **Calibrar la canasta:** tocá **🎯 Calibrar canasta** y hacé clic sobre una canasta.
4. Tildá **Ver detección** para comprobar qué está reconociendo la app (blanco: paletas, rojo: canasta). Si se ve ruido, volvé a calibrar o ajustá la tolerancia.
5. Apretá **T** para empezar la partida.
6. Al terminar aparece el botón **Jugar de nuevo** para la revancha.

La configuración se **guarda sola** en el navegador. Para volver a los valores de fábrica, usá **Restablecer configuración**.

### ⌨️ Teclas

| Tecla | Acción |
|-------|--------|
| **T** | Empieza la partida |
| **R** | Reinicia la partida y la deja en pausa |
| **H** | Oculta o muestra el panel |
| **Esc** | Cancela la calibración |

---

## ⚙️ Opciones del panel

| Sección | Opción | Para qué sirve |
|---------|--------|----------------|
| Controles de física | Intervalo / posición de aparición, rebote | Cada cuánto y dónde caen las pelotas |
| Detección de color | Color de las paletas, tolerancia, saturación y brillo mínimos | Ajuste fino de la detección de las paletas |
| Detección de color | Opacidad de los bloques, Ver detección | Cómo se dibujan las paletas y vista de lo detectado |
| Paletas | Mostrar paleta (U) | Oculta el dibujo de la paleta (sigue funcionando) |
| Paletas | Estabilidad | Reduce el temblequeo de la paleta |
| Paletas | Rebote / velocidad | Cuánto rebotan las pelotas en la paleta y qué tan rápido la sigue |
| Canasta | Color, tolerancia, Mostrar canasta | Detección de la canasta y si se dibuja o no |
| — | Espejar cámara, Cámara | Volteo horizontal y elección de cámara |
| — | Mostrar/ocultar fondo de cámara | Muestra solo los elementos del juego, útil con proyector |

---

## 🛠️ Problemas frecuentes

- **No aparece la cámara:** abrí la página desde `http://localhost:8080` y no con doble clic sobre el archivo. Revisá también que ninguna otra app esté usando la cámara.
- **"Esperá a que termine de cargar OpenCV":** la librería pesa unos 10 MB. Esperá unos segundos y revisá la conexión a internet.
- **La paleta tiembla o desaparece:** volvé a calibrar con buena iluminación, subí la **Estabilidad** o la **Tolerancia de color**.
- **Se detectan cosas que no son la paleta:** bajá la tolerancia o usá colores de paleta y canasta más distintos entre sí y del fondo.

---

## 📁 Estructura

```
index.html             Página y panel de control
app.js                 Lógica del juego, detección (OpenCV.js) y física (Matter.js)
style.css              Estilos
Instructivo juego.txt  Instructivo breve del juego
```

---

## 🙌 Créditos

- Simulación original con webcam: **Bunyan** – IG [@bongyunng](https://instagram.com/bongyunng)
- Adaptación como juego: [luuucaso/app-realtime-block](https://github.com/luuucaso/app-realtime-block)
