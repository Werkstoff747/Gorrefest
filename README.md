# 🎲 Gorre - Archivo de Crónicas y Partidas de Rol

Repositorio oficial de la interfaz web para el catálogo y listado de partidas de rol de **Gorre**. La web está diseñada con un enfoque moderno, responsivo y adaptado a sistemas de modo claro/oscuro, conectando de forma dinámica con un documento de Google Sheets.

---

## 📁 Estructura del Proyecto

El proyecto se compone principalmente de dos archivos HTML independientes:
1. **`index.html`**: La página de bienvenida/portada. Presenta el logotipo corporativo, una breve introducción y los accesos directos principales (al listado y al servidor de Discord). Incluye su propio selector de modo claro/oscuro.
2. **`partidas.html`**: La página principal del catálogo. Obtiene las partidas en tiempo real desde Google Sheets, ofrece un sistema de búsqueda instantánea, filtros por líneas de rol, tarjetas adaptativas en dos columnas y una botonera flotante.

---

## 🔄 Funcionamiento General de `partidas.html`

* **Carga de Datos (TSV):** Al iniciar, la función `cargarPartidas()` realiza un `fetch` a una URL de exportación en formato TSV de Google Sheets. 
* **Filtros Dinámicos:** Lee automáticamente la columna de sistemas (líneas) para generar botones de filtrado interactivos ("Todas" + cada sistema único detectado).
* **Buscador Instantáneo:** Filtra en tiempo real combinando el título, sistema, género y descripción.
* **Control de Publicación:** Si una fila del Google Sheet tiene la columna de publicación configurada como `"no"`, el sistema la descarta automáticamente.

### 📊 Estructura del Google Sheet (Columnas esperadas en orden)
1. **Título de la partida** (`columnas[0]`)
2. **Línea / Sistema de rol** (`columnas[1]`)
3. **Género / Etiquetas** (`columnas[2]`)
4. **Descripción** (`columnas[3]`)
5. **URL de la imagen de portada** (`columnas[4]`)
6. **Aviso de contenido / Advertencia** (`columnas[5]`)
7. **Número de jugadores** (`columnas[6]`)
8. **Sesiones (ej. "1" para One-Shot o número de sesiones)** (`columnas[7]`)
9. **Enlace de invitación a Discord** (`columnas[8]`)
10. **Publicar (escribir "no" para ocultar la partida)** (`columnas[9]`)

---

## 🎨 Sistema de Paletas de Colores y Variables CSS

La web gestiona toda su estética mediante variables CSS personalizadas dentro de la etiqueta `<style>`. Existen dos estados: **Modo Oscuro (`:root`)** y **Modo Claro (`body.light-mode`)**.

### Guía detallada de variables CSS:

| Variable | Descripción / Dónde se aplica |
| :--- | :--- |
| `--bg-color` | Color de fondo general de toda la página web. |
| `--card-bg` | Color de fondo de las tarjetas de partidas y botones flotantes. |
| `--card-border` | Color de los bordes exteriores de las tarjetas y controles. |
| `--text-color` | Color principal del texto (títulos, elementos destacados). |
| `--text-muted` | Color secundario/atenuado para descripciones y metadatos. |
| `--accent-color` | Color de acento corporativo (empleado en etiquetas de sistema y botones activos). |
| `--accent-hover` | Color que adoptan los elementos interactivos al pasar el ratón (*hover*). |
| `--header-bg` | Color de fondo de la cabecera superior de la página (`#415A77` en ambos modos o `#8ecae6` en claro). |
| `--header-border` | Color del borde que enmarca la cabecera. |
| `--header-text` | Color del texto del título principal dentro de la cabecera. |
| `--logo-filter` | Filtros CSS aplicados al logotipo corporativo (`images/gorre_l.png`) para adaptarlo al fondo. |
| `--img-bg` | Color de fondo dentro del contenedor de la portada de la partida. |
| `--warning-bg` / `--warning-text` | Estilos para la caja de avisos o advertencias de contenido. |
| `--tag-bg` | Fondo de las etiquetas secundarias (géneros de la partida). |
| `--discord-bg` / `--discord-hover` | Color de fondo de la caja del botón de Discord y su estado *hover* (hereda del color del sistema). |
| `--discord-text` / `--discord-hover-text` | Color del texto y del icono de Discord. |

---

## ⚙️ Guía de Personalización y Mantenimiento

### 1. Ajustar el límite de texto en las descripciones (`-webkit-line-clamp`)
En el archivo `partidas.html`, dentro de los estilos CSS, busca la clase `.desc-text`:

```css
.desc-text {
    display: -webkit-box;
    -webkit-line-clamp: 5; /* <--- Número máximo de líneas visibles antes de cortar */
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    margin: 0 0 4px 0;
}
```

* **Recomendación de caracteres:** Para un diseño de 2 columnas con la fuente actual, cada línea abarca unos **50-55 caracteres**.
  * Con **5 líneas**, se recomiendan descripciones de **250 a 280 caracteres**.
  * Si subes el límite a **6 líneas**, el texto ideal puede rondar los **300 a 330 caracteres** para evitar que aparezca el botón de `+ info` por solo un par de palabras sobrantes.

### 2. Cambiar colores de la cabecera o temas
Modifica directamente los valores hexadecimales en `:root` (Modo Oscuro) o `body.light-mode` (Modo Claro) en las variables `--header-bg`, `--header-text` o `--accent-color`.

---

## 🤖 Nota para Asistencia con IA
> *Si estás utilizando una Inteligencia Artificial para continuar el desarrollo o mantenimiento de este proyecto, facilítale este archivo `README.md` junto con el código fuente de `index.html` o `partidas.html`. La IA comprenderá inmediatamente la estructura de datos del TSV, el sistema de variables CSS y la lógica de renderizado JavaScript.*
