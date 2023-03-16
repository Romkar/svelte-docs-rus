# Начало работы
---

Чтобы попробовать Svelte в интерактивной онлайн-среде, вы можете попробовать [REPL](https://svelte.dev/repl) или [StackBlitz](https://node.new/svelte).

Для создания проекта локально мы рекомендуем использовать [SvelteKit](https://kit.svelte.dev/), официальный фреймворк приложений от команды Svelte:
```
npm create svelte@latest myapp
cd myapp
npm install
npm run dev
```

SvelteKit будет обрабатывать вызов [компилятора Svelte](https://www.npmjs.com/package/svelte) для преобразования ваших `.svelte` файлов в `.js` файлы, создающие DOM и `.css` файлы, которые его стилизуют. Он также предоставляет все остальные компоненты, необходимые для создания веб-приложения, такие как сервер разработки, маршрутизация и развертывание. [SvelteKit](https://kit.svelte.dev/) использует [Vite](https://vitejs.dev/) для сборки вашего кода и обработки рендеринга на стороне сервера (SSR). Существуют [плагины для всех основных веб-пакетов](https://sveltesociety.dev/tools#bundling) для обработки компиляции Svelte, дающие на выходе файлы `.js` и `.css`, которые вы можете вставить в ваш HTML, но большинство других не обрабатывают SSR.

Если вам не нужен полноценный фреймворк для приложений, и вы хотите создать простой сайт/приложение только для фронтенда, вы также можете использовать Svelte (без Kit) с Vite, запустив `npm init vite` и выбрав опцию `svelte`. При этом `npm run build` будет генерировать HTML, JS и CSS файлы внутри каталога `dist`. 

Команда Svelte поддерживает [расширение VS Code](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) и также есть интеграции с различными другими  [редакторами](https://sveltesociety.dev/tools#editor-support) и инструментами.

Если у вас возникли проблемы, обратитесь за помощью в [Discord](https://svelte.dev/chat), [StackOverflow](https://stackoverflow.com/questions/tagged/svelte) или в русскоязычный Telegram-канал [@sveltejs](https://t.me/sveltejs).
