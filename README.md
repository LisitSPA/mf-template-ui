
# Documentación del Template de Microfrontend

## 1. Introducción

Este template de microfrontend está diseñado para facilitar la creación de nuevos microfrontends en nuestro ecosistema de aplicaciones. Incluye una configuración estándar para React, Webpack, single-spa, y más. Este documento guía a los pasos necesarios para clonar el template, personalizarlo, y configurarlo.

## 3. Clonación del Template

Instrucciones para clonar el template desde el repositorio.

```bash
git clone https://github.com/LisitSPA/mf-template-ui.git
cd mf-template-ui
```

## 4. Instalación de Dependencias

Comandos para instalar las dependencias del proyecto.

```bash
npm install
```

## 5. Configuración Inicial

### Cambio de Nombres

Instrucciones para cambiar el nombre del proyecto y otros identificadores importantes.

- **Nombre del Proyecto**: Modificar en `package.json`, `README.md`, y otros archivos relevantes.
- **Identificador del Microfrontend**: Actualizar en la configuración de single-spa y cualquier otro lugar donde se utilice.

**Cambiar el nombre del archivo `react-gufo-mf-template-ui.tsx`. Ejemplo:**

```
 react-gufo-mf-nuevoNombre-ui.tsx 
```

**Ejemplo en `package.json`:**

```json
{
  "name": "@react-gufo-mf/nuevoNombre-ui",
  "description": "Descripción del nuevo proyecto",
  "version": "1.0.0",
  ...
}
```

**Ejemplo en configuración de webpack.config:**

```javascript
// webpack.config.js
const defaultConfig = singleSpaDefaults({
  orgName: "react-gufo-mf",
  projectName: "nuevoNombre-ui",
  ...
});
```

### Cambio de Puertos

Instrucciones para cambiar el puerto en el que el microfrontend se sirve en desarrollo.

- **Webpack DevServer**: Configuración en `webpack.config.js` o el equivalente.

**Ejemplo en `webpack.config.js`:**

```javascript
module.exports = {
  devServer: {
    port: 9005, // Revisar cual es el último puerto en index.ejs de mf-root-ui y sumarle +1
    ...
  },
  ...
};
```

### Actualización del Import Map en mf-root-ui archivo index.ejs

Instrucciones para actualizar o agregar rutas en el import map.

```html
//  <% if (isLocal) { %>
<script type="systemjs-importmap">
{
  "imports": {
    @react-gufo-mf/nuevoNombre-ui": "http://localhost:9005/react-gufo-mf-nuevoNombre-ui.js",
    ...
  }
}
</script>
```
### Agregar ruta con aplicación en microfrontend-layout.html


```html
//  Agregar una ruta nueva
  <route path="/rutaNueva" exact>
        <application name="@react-gufo-mf/nuevoNombre-ui"></application>
 </route>
```

