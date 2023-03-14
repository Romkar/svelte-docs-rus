# FAQ (Часто Задаваемые Вопросы)

## Я новичок в Svelte. Как мне лучше начинать изучение?

Полагаем, что лучшее всего начинать с нашего интерактивного [Учебника](/tutorial). Каждый урок раскрывает определёный аспект фреймворка и прост для понимания. Вы сможете редактировать и запускать настоящие компоненты Svelte прямо в браузере.

Чтобы понять основы хватит 5-10 минут. А за полтора часа вы сможете пройти весь учебник.

## Где мне получить помощь?

Если вопрос касается определенного синтаксиса, [страница описания API](https://ru.svelte.dev/docs) лучшее место для начала.

Stack Overflow – это популярный форум для вопросов по написанию кода или если вы застряли с какой-то непонятной ошибкой. Прочтите существующие вопросы, помеченные тегом [Svelte](https://stackoverflow.com/questions/tagged/svelte+or+svelte-3) или [задайте собственный вопрос](https://stackoverflow.com/questions/ask?tags=svelte)!

Есть форумы и чаты, которые являются хорошим местом для обсуждения лучших практик, архитектуры приложений или просто познакомиться с людьми из сообщества Svelte. Например, заходите в русскоязычный [Telegram-чат](https://t.me/sveltejs), [официальный Discord](https://svelte.dev/chat) или [канал на Reddit](https://www.reddit.com/r/sveltejs/). Но вопросы связанные, с кодом лучше подходят для Stack Overflow.

## Есть ли какие-либо видеокурсы?

Рич Харрис, создатель Svelte, провел курс(на английском):

- [Frontend Masters](https://frontendmasters.com/courses/svelte/)

Ещё есть несколько сторонних курсов:

- [Курс от Владилена Минина](https://www.youtube.com/playlist?list=PLqKQF2ojwm3mgL-JymBaquJItb0eP0MTR)
- [Курс от DevMagazine (на русском языке)](https://www.youtube.com/playlist?list=PLmfIBo6rTVR5XNcJxu8TwzEvIDUCAhGc6)
- [Egghead](https://egghead.io/playlists/getting-started-with-svelte-3-05a8541a)
- [Udemy](https://www.udemy.com/sveltejs-the-complete-guide/)

Кстати, на Udemy часто бывают скидки до 90% процентов.

## Есть какие-то книги?

Вышло несколько книг про Svelte:

- [Svelte Handbook](https://flaviocopes.com/page/svelte-handbook/) от Flavio Copes
- [Svelte 3 Up and Running](https://www.amazon.com/dp/B08D6T6BKS/) от Alessandro Segala
- [Svelte and Sapper in Action](https://www.manning.com/books/svelte-and-sapper-in-action) от R. Mark Volkmann

## Как в VS Code включить подсветку синтаксиса .svelte файлов?

Есть [официальное расширение Svelte для VS Code](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## Есть ли инструмент для автоматического форматирования моих файлов .svelte?

Вы можете использовать Prettier с [prettier-plugin-svelte](https://www.npmjs.com/package/prettier-plugin-svelte).

## Как мне документировать свои компоненты?

Редакторы, которые работают с Svelte Language Server, позволяют документировать компоненты, функции и экспорты при помощи специальных комментариев.

````svelte
<script>
	/** Как нам называть пользователя? */
	export let name = 'world';
</script>

<!--
@component
Тут поместите описание вашего компонента.
Оно будет отображаться в всплывающей подсказке.

- Здесь можно использовать _markdown_.
- Также можно вставлять блоки с кодом.
- Вот так:
  ```tsx
  <main name="Arethra">
  ```
-->
<main>
	<h1>
		Hello, {name}
	</h1>
</main>
````

Обратите внимане, что необходимо написать `@component` в HTML комментарии, который описывает ваш компонент.

## Что с поддержкой TypeScript?

Нужно установить [препроцессор](https://github.com/sveltejs/svelte-preprocess). Также вы можете использовать проверку типов из командной строки при помощи [svelte-check](https://www.npmjs.com/package/svelte-check).

Для объявления типа реактивной переменной в шаблоне Svelte используйте следующий синтаксис:
```
let x: number;
$: x = count + 1;
```

Для импорта типа или интерфейса обязательно используйте [модификатор `type`](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-8.html#type-only-imports-and-export)

```
import type { SomeInterface } from './SomeFile';
```

Использовать модификатор `type` необходимо, поскольку `svelte-preprocess` не может знать импортируете ли вы тип или значение — он просто обрабатывает один файл за раз и ничего не знает о других файлах, поэтому не может безопасно убрать импорты, которые содержать только типы если в них нет модификатора.

## Масштабируется ли Svelte?

Со временем в блоге будет статья на эту тему, а пока можете почитать об этом [тут](https://github.com/sveltejs/svelte/issues/2546).

## Существуют ли библиотеки UI компонентов?

Есть несколько библиотек UI компонентов и отдельных компонентов. Вы можете найти их список в разделе [Components](https://sveltesociety.dev/components) на сайте Svelte Society.

## Как мне тестировать Svelte приложения?

Мы рекомендуем постараться отделить логику представления от бизнес-логики. Преобразования данных и управление межкомпонентным состоянием лучше вынести из компонентов Svelte наружу. Тестируйте их как обычный JavaScript код. В компонентах же можно протестировать их логику, и помнить что Svelte имеет свои собственные тесты и тестировать то что вы получаете на выходе компилятора нет необходимости.

Существует несколько подходов для тестирования, которые используют наши пользователи. Но обычно все они основываются на компилировании и монтировании компонента, перед выполнением тестов. То есть, придется создавать отдельный бандл для каждого тестируемого компонента. Вы можете подключиться к этому компоненту посредством JSDOM. Если нужен настоящий браузер, можно использовать Puppeteer или Cypress

Некоторые ресурсы, которые могут помочь с юнит-тестами:

- [Svelte Testing Library](https://testing-library.com/docs/svelte-testing-library/example/)
- [Пример использования uvu вместе с JSDOM](https://github.com/lukeed/uvu/tree/master/examples/svelte)

## Есть ли роутеры?

Официальная библиотека для роутинга – [SvelteKit](https://ru.kit.svelte.dev/), которая пока находится в бета-версии. SvelteKit предлагает роутер основанный на файловой системе, рендер на стороне сервера(SSR), и горячую перезагрузку модулей(HMR) в одном пакете, который легко использовать. Он предлагает концепции схожие с идеями Next.js для React.

Тем не менее, вы можете использовать любую библиотеку маршрутизатора, которую хотите. Многие люди используют [page.js](https://github.com/visionmedia/page.js). Есть также [navaid](https://github.com/lukeed/navaid), что очень похоже. И [universal-router](https://github.com/kriasoft/universal-router), который изоморфен дочерним маршрутам, но без встроенной поддержки истории.

Если вы предпочитаете декларативный подход, попробуйте [tinro](https://github.com/AlexxNB/tinro) или изоморфный [svelte-routing](https://github.com/EmilTholin/svelte-routing) или его форк [svelte-navigator](https://github.com/mefechoel/svelte-navigator), содержащий некоторую дополнительную функциональность.

Если нужна навигация на клиенте при помощи hash части URL, возьмите [svelte-spa-router](https://github.com/ItalyPaleAle/svelte-spa-router) или [abstract-state-router](https://github.com/TehShrike/abstract-state-router/), зрелый роутер.

[Routify](https://routify.dev) - это еще один маршрутизатор на основе файловой системы, похожий на маршрутизатор SvelteKit.

## Как мне обновить мои компоненты, написанные на Svelte v2?

svelte-upgrade ещё полностью не готова для преобразования v2->v3, [но уже почти готова](https://github.com/sveltejs/svelte-upgrade/pull/12).

## Доступен ли ещё Svelte v2?

Новый функционал добавляться не будет и какие-либо баги будут исправляться только если они являются уязвимостями в безопасности.

Документация всё еще доступна [тут](https://v2.svelte.dev/guide).

## Как сделать HMR?

Рекомендуем использовать [SvelteKit](https://ru.kit.svelte.dev/), который поддерживает HMR из коробки и построен поверх Vite и svelte-hmr. Существуют также плагины от нашего сообщества [rollup](https://github.com/rixo/rollup-plugin-svelte-hot) и [webpack](https://github.com/rixo/svelte-loader-hot).