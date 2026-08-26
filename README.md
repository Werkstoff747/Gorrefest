# 🎲 Listado de Partidas - Gorre

¡Bienvenido al repositorio del listado de partidas de rol de **Gorre**! Esta web está diseñada como un catálogo interactivo, ligero y autogestionable que se alimenta directamente de una hoja de cálculo de Google Sheets. Cuenta con modo oscuro y claro automático, buscador en tiempo real, filtros por sistemas y un sistema inteligente de descripciones y ordenación.

---

## 📂 Estructura de Imágenes (`/images`)

Dentro de la carpeta `images` del proyecto se encuentran los recursos gráficos fijos de la interfaz:

*   **`gorre.ico`**: El icono (favicon) que aparece en la pestaña del navegador.
*   **`gorre.jpg`**: Imagen general de respaldo o de presentación del proyecto.
*   **`gorre_l.png`**: Logotipo corporativo principal. Se muestra tal cual en el **Modo Claro** y el sistema CSS le aplica automáticamente un filtro para pasar las letras a blanco en el **Modo Oscuro**.
  
*(Nota: Las portadas individuales de cada aventura no se guardan en el repositorio, sino que se enlazan mediante una URL directa desde el Google Sheet).*

---

## 📊 Gestión de Datos (Google Sheets)

La web no requiere bases de datos complejas; toda la información de las partidas se gestiona de forma cómoda desde un documento de Google Sheets.

### ¿Cómo cambiar el origen de los datos?
El código de la página web se conecta a Google Sheets mediante un enlace de exportación en formato TSV (valores separados por tabuladores). Si necesitas cambiar la hoja de cálculo por otra propia, busca la línea del enlace en el archivo `index.html` y sustituye el ID de la hoja de cálculo por el tuyo propio:

> `https://docs.google.com/spreadsheets/d/` **`TU_ID_DE_GOOGLESHEET_AQUI`** `/export?format=tsv`

---

## 📝 Guía Rápida para el Administrador (Estructura de las Columnas)

El orden de las columnas en la hoja de cálculo de Google Sheets debe ser estrictamente el siguiente (comenzando desde la columna A, fila 2 en adelante):

*   **Columna A (Título):** Nombre de la aventura o partida de rol (ej: *Caso sin resolver*).
*   **Columna B (Línea / Sistema):** El sistema o juego de rol al que pertenece (ej: *Cazador*, *Cthulhu*, *Vampiro*). *Nota: La web agrupa y ordena automáticamente las partidas primero por este campo.*
*   **Columna C (Género):** Etiquetas o hashtags de género (ej: `#drama #terror #sobrenatural`).
*   **Columna D (Descripción):** Sinopsis o texto de la aventura. La web mostrará de forma elegante hasta 5 líneas y añadirá un botón desplegable `+ info` de manera inteligente solo si el texto es más largo.
*   **Columna E (Portada):** Enlace directo a la imagen de la portada de la aventura.
*   **Columna F (Aviso):** Alertas de contenido o advertencias para jugadores (ej: *Violencia, Temas maduros*). Si se deja en blanco, la alerta no aparecerá.
*   **Columna G (Jugadores):** Rango de plazas o número de jugadores (ej: *2-4*).
*   **Columna H (Sesiones):** Duración estimada. Si pones `"1"` o dejas el espacio indicado para sesión única, la web lo transformará automáticamente en la etiqueta roleras **"One-Shot"**. Si pones un número superior (ej: `"3"`), indicará *"3 sesiones"*.
*   **Columna I (Link Discord):** Enlace de invitación directo al canal o servidor de Discord para unirse a la partida.
*   **Columna J (Publicar):** Interruptor de visibilidad. Si escribes `"no"` (en minúsculas o mayúsculas), esa partida se ocultará automáticamente de la web principal sin necesidad de borrarla del Excel.

---

## 🛠️ Características Técnicas para Desarrolladores
*   **Tipografías:** Utiliza *Montserrat* para títulos y sistemas, e *Inter* para el cuerpo de texto.
*   **Iconografía:** Integración completa mediante CDN con *FontAwesome 6*.
*   **Diseño Adaptativo:** Cuadrícula automatizada (*CSS Grid*) totalmente responsive para móviles, tablets y escritorios.
