# wdkeep 📝

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Open Source](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://opensource.org/)

**wdkeep** es una aplicación de notas autohospedada, de código abierto y centrada en la privacidad, inspirada en Google Keep. Toma el control total de tu información guardando las notas directamente en tu propio servidor WebDAV.

*Simple, seguro y tuyo.*


*(Recomendación: Reemplaza esta URL con una captura de pantalla real de tu aplicación en funcionamiento).*

---

## Tabla de Contenidos

-   [¿Por qué wdkeep?](#-por-qué-wdkeep)
-   [✨ Características Principales](#-características-principales)
-   [🔧 Cómo Funciona (Stack Técnico)](#-cómo-funciona-stack-técnico)
-   [🚀 Guía de Inicio Rápido (Instalación)](#-guía-de-inicio-rápido-instalación)
-   [💡 Hoja de Ruta (Roadmap)](#-hoja-de-ruta-roadmap)
-   [🤝 Contribuciones](#-contribuciones)
-   [📄 Licencia](#-licencia)

## 🤔 ¿Por qué wdkeep?

En un mundo donde nuestros datos son un producto, **wdkeep** nace de la necesidad de tener una herramienta simple para tomar notas sin ceder el control. A diferencia de los servicios en la nube comerciales:

-   **Tú eres el dueño de tus datos:** Las notas se guardan en tu propio servidor (Nextcloud, Synology, Apache, etc.). No hay análisis de datos, no hay publicidad, no hay seguimiento.
-   **Sin "Vendor Lock-in":** Tus notas son simples archivos `.html`. Puedes abrirlas, migrarlas o hacer una copia de seguridad en cualquier momento y con cualquier herramienta.
-   **Código Abierto y Transparente:** El código es completamente abierto. Puedes revisarlo, modificarlo y adaptarlo a tus necesidades.

## ✨ Características Principales

-   **Interfaz Familiar e Intuitiva:** Si has usado Google Keep, te sentirás como en casa.
-   **Control Total:** Funciona sobre cualquier servidor **WebDAV**, dándote libertad de elección.
-   **Editor de Texto Enriquecido:** Formato de texto, listas, enlaces y más, gracias a Summernote.
-   **Organización Avanzada:**
    -   **Etiquetas:** Clasifica tus notas y filtra por ellas.
    -   **Colores:** Asigna colores para una identificación visual rápida.
    -   **Fijar Notas:** Mantén las notas importantes siempre a la vista.
-   **Archivo y Papelera:** Archiva notas para despejar tu vista principal o muévelas a la papelera antes de su eliminación definitiva.
-   **Búsqueda en Tiempo Real:** Filtra tus notas al instante por título o etiqueta.
-   **Tema Oscuro:** Cómodo para tus ojos en condiciones de poca luz.
-   **Diseño Adaptable:** Funciona a la perfección en escritorio y dispositivos móviles.
-   **Cero Dependencias de Servidor:** Es una aplicación 100% frontend. Solo necesitas un servidor web estático para alojar el archivo `index.html`.

## 🔧 Cómo Funciona (Stack Técnico)

**wdkeep** es una **Single Page Application (SPA)** construida con tecnologías frontend estándar. No requiere un backend complejo, solo un servidor que soporte el protocolo **WebDAV**.

-   **Backend:** Tu propio servidor WebDAV. Cada nota es un archivo `.html`. Las etiquetas, el color y otros metadatos se guardan de forma inteligente en el nombre del archivo.
-   **Frontend:**
    -   **HTML5, CSS3, JavaScript (ES6):** La base de la aplicación.
    -   **Materialize CSS:** Para la interfaz y los componentes de Material Design.
    -   **jQuery:** Requerido por algunas librerías como Summernote.
    -   **Summernote:** Para el editor de texto enriquecido.

## 🚀 Guía de Inicio Rápido (Instalación)

Instalar **wdkeep** es muy sencillo. Solo necesitas dos cosas:

1.  Un **servidor WebDAV** accesible.
2.  Un **servidor web** para alojar un único archivo HTML (puede ser el mismo).

### Pre-requisitos

-   **Servidor WebDAV:** Configura una carpeta en tu servidor WebDAV para almacenar las notas. Por ejemplo, `https://tuservidor.com/remote.php/dav/files/tu-usuario/Notas`.
-   **Servidor Web:** Cualquier servidor capaz de servir archivos estáticos (Apache, Nginx, Caddy, o incluso GitHub Pages).

### Pasos

1.  **Descarga el código:** Clona este repositorio o descarga el archivo `index.html`.

    ```bash
    git clone https://github.com/tu-usuario/wdkeep.git
    ```

2.  **Configura las rutas WebDAV:** Abre el archivo `index.html` en un editor de texto y busca estas dos líneas dentro de la etiqueta `<script>`:

    ```javascript
    const webdavAppBaseUrl = "/dav/Notas/html/";
    const webdavNotesUrl = "/dav/Notas/html/notas/";
    ```

    Modifícalas para que apunten a las rutas de tu servidor WebDAV. **Importante:**
    -   `webdavAppBaseUrl`: Es la carpeta principal de la aplicación.
    -   `webdavNotesUrl`: Es la subcarpeta **dentro de la anterior** donde se guardarán los archivos `.html` de las notas. Debes crear esta subcarpeta (`notas`) manualmente.

    **Ejemplo de configuración para Nextcloud:**

    ```javascript
    const webdavAppBaseUrl = "/remote.php/dav/files/TU_USUARIO/WDKeepApp/";
    const webdavNotesUrl = "/remote.php/dav/files/TU_USUARIO/WDKeepApp/notas/";
    ```

3.  **Sube el archivo:** Sube el archivo `index.html` (o todo el repositorio) a tu servidor web.

4.  **¡Listo!** Accede a la URL donde subiste el archivo y empieza a tomar notas.

## 💡 Hoja de Ruta (Roadmap)

**wdkeep** es un proyecto en desarrollo. Algunas de las ideas para el futuro incluyen:

-   [ ] **Progressive Web App (PWA):** Soporte offline e instalación en el escritorio/móvil.
-   [ ] **Búsqueda de texto completo** dentro del contenido de las notas.
-   [ ] **Compartir notas** a través de un enlace público (solo lectura).
-   [ ] **Más opciones de personalización** (fuentes, temas).
-   [ ] **Eliminar la dependencia de jQuery** para una aplicación más ligera y moderna.

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Si tienes ideas, sugerencias o encuentras un error, por favor abre un *issue* en GitHub. Si quieres aportar código, no dudes en hacer un *fork* del repositorio y enviar un *pull request*.

## 📄 Licencia

Este proyecto está bajo la **Licencia MIT**. Consulta el archivo `LICENSE` para más detalles.
