### Command for installing laravel and vue

1. Install new laravel project

```
laravel new [project name]
```

OR

```
composer create-project laravel/laravel projectName
```

2. Install NodeJs

```
npm install
```

3. Install vue

```
npm install vue@next vue-loader@next
```

4. Install Plugin Vue From Vite

```
npm i @vitejs/plugin-vue
```

5. Edit File `vite.config.js`

```
// vite.config.js
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';

import vue from '@vitejs/plugin-vue'


export default defineConfig({
    plugins: [

        vue(),

        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
});

```

6. Edit File `app.js` Inside Folder `resources/js`

```
import {createApp} from 'vue'

import App from './App.vue'

createApp(App).mount("#app")

```

7. Create File `app.blade.php` Inside Folder `resources/views`

```
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">

        <title>ًApplication</title>

        @vite('resources/css/app.css')

    </head>
    <body>

        <div id="app"></div>

        @vite('resources/js/app.js')

    </body>
</html>

```

8. Run PHP on local server & run node local server

```
php artisan serve

npm run dev
```
