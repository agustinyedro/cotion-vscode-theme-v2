# 🎨 Resumen del Proyecto

El proyecto es una extensión de **tema de color oscuro para VS Code** llamada **"Cotion Theme"**, inspirada en los colores de interfaz de Notion.

- El tema no se edita directamente como JSON, sino que se construye **programáticamente** utilizando la herramienta **`vscode-theme-composer`** a partir de archivos fuente de JavaScript.

---

## 🏗️ Arquitectura y Estructura del Tema

### Sistema de Construcción (Build System)

| Componente           | Archivo/Proceso                 | Descripción                                                         |
| :------------------- | :------------------------------ | :------------------------------------------------------------------ |
| **Fuente**           | `src/themes/dark.js`            | Definiciones de colores en módulos JavaScript.                      |
| **Construcción**     | `src/index.js`                  | Script que usa `vscode-theme-composer` para compilar JS a JSON.     |
| **Salida**           | `themes/cotion-theme-dark.json` | Archivo **JSON** del tema generado (no editar directamente).        |
| **Punto de Entrada** | `package.json`                  | Manifiesto de la extensión que referencia el archivo JSON generado. |

### Definición de Colores

Las definiciones de color utilizan la API de `vscode-theme-composer`:

- **`setBaseColors()`**: Establece los colores principales de acento y fondo.
- **`setColors()`**: Define el resaltado de sintaxis a **nivel de _token_** (ej. _strings_, comentarios, funciones). La librería se encarga de mapear esto a los _scopes_ de TextMate.

---

## ⚙️ Comandos de Desarrollo Clave

| Comando                  | Descripción                                                                                        |
| :----------------------- | :------------------------------------------------------------------------------------------------- |
| `yarn theme:build`       | **Compila** `src/themes/*.js` y genera el JSON final. **Ejecutar después de cambiar los colores.** |
| `yarn vscode:prepublish` | **Alias de `yarn build`**. Se ejecuta automáticamente antes de publicar en el Marketplace.         |
| `yarn theme:publish`     | Publica la extensión en el **VS Code Marketplace** (requiere credenciales de _publisher_).         |
| **Testing (F5)**         | Presiona `F5` en VS Code para lanzar el Host de Desarrollo de la Extensión y probar el tema.       |

---

## 📄 Archivos Importantes

- `src/themes/dark.js`: El archivo donde se **definen y editan los colores del tema**.
- `themes/cotion-theme-dark.json`: El archivo **generado** que **no debe ser editado directamente**.
