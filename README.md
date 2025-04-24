
# Encuesta de Confianza Institucional – Universidad Autónoma de Occidente

Este es un formulario web en HTML que permite levantar una encuesta en línea sobre confianza institucional y procesos de designación. Las respuestas se registran automáticamente en una hoja de cálculo de Google Sheets.

## 📝 Instrucciones de uso

### 1. Subir el formulario a GitHub Pages

1. Crea una cuenta o inicia sesión en [GitHub](https://github.com)
2. Crea un nuevo repositorio, por ejemplo `encuesta-confianza`
3. Sube los archivos `index.html` y `README.md` a ese repositorio
4. Activa GitHub Pages en `Settings > Pages` seleccionando la rama principal y la carpeta raíz (`/`)
5. Tu formulario estará disponible en una URL como: `https://tuusuario.github.io/encuesta-confianza/`

### 2. Conectar con tu Google Sheets

#### Paso 1: Abre tu hoja de cálculo
Abre tu [hoja de cálculo de Google Sheets](https://docs.google.com/spreadsheets/d/1fm9qMFRnre5Y91EchMgKBznE9c_115xt0UMJ4DJ2ZVk/edit).

#### Paso 2: Abre Apps Script
- Menú superior: **Extensiones > Apps Script**

#### Paso 3: Pega este código

```javascript
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  const data = e.parameter;

  sheet.appendRow([
    new Date(),
    data.perfilSeleccionado
  ]);

  return ContentService.createTextOutput("OK");
}
```

#### Paso 4: Implementar como Aplicación Web

1. Ve a **Implementar > Nueva implementación**
2. Tipo: `Aplicación web`
3. Ejecutar como: tú
4. Quién puede acceder: `Cualquiera`
5. Da clic en `Implementar` y autoriza permisos
6. Copia el **URL** que empieza con `https://script.google.com/macros/s/...`

#### Paso 5: Edita el HTML

Abre `index.html` y **reemplaza** esta línea:

```javascript
fetch('https://script.google.com/macros/s/TU_SCRIPT_ID/exec',
```

Por el URL que copiaste del paso anterior.

¡Y listo! Tu formulario ya está conectado con tu hoja de cálculo.

---

📌 Este formulario detecta si el usuario cambia de pestaña, y muestra aleatoriamente una historia de tratamiento.
