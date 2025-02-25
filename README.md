# newGotoProposition
Propuesta de instalacion en laravel y Vuejs


## Iniciar la aplicacion 
 En caso de no tener todo configurado ir a Instalacion base de Laravel
```bash 
    composer run dev
```

## Instalacion base de Laravel
- Instalar Nodejs y Composer (php)
- Crea un proyecto siguiendo las siguentes lineas.

```bash
composer create-project "laravel/laravel=^11.0" nombre-de-app
cd nombre-de-app
npm install && npm run dev
```

## Instalacion de vuejs

```bash
cd nombre-de-app
npm vue@latest vue-loader@latest
npm install --save-dev @vitejs/plugin-vue
```

### Configuracion de archivo vite.config.js
  
```js
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import vue from '@vitejs/plugin-vue';  //Adicionar despues de instalar @vitejs/plugin-vue

export default defineConfig({
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
        vue(), //Adicionar despues de instalar @vitejs/plugin-vue
    ],
});
```

## Modificar los siguientes archivos
### Archivo welcome.blade.php en resources/view/welcome.blade.php

```html
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>Laravel</title>
    @vite('resources/css/app.css')
</head>

<body>
    <div id="app"></div>
    @vite('resources/js/app.js')
</body>

</html>
```

### Archivo app.vue en resources/js/component/app.vue
```vue
  <template>
      <p>
          Hola
      </p>
  </template>
```

### Archivo app.js en resources/js/app.js
```js
import './bootstrap';
//Adicionar despues de instalar vue vue-loader @vitejs/plugin-vue
import { createApp } from 'vue';
import app from './components/app.vue';

createApp(app).mount("#app");
```
