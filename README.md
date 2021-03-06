# Preact Vite SPA Starter Template

This template is tuned for "SPA" sites; sites that do not need server side rendering (SSR). If you need SSR, then this template won't work for you.

Clone repo, use node.js 14+ and run following:
```
npm ci
cd tests; npm ci; cd ..
npm run dev

# works with yarn and pnpm too
```

## Features!

- [Preact](https://github.com/preactjs/preact) + Preact hooks = 4 KB
- [Vite](https://vitejs.dev) and all the goodies that comes with it
- [preact-router](https://github.com/preactjs/preact-router)
  - Code split by pages + lazy loaded (via [preact-lazy](https://github.com/iosio/preact-lazy)</a>)
  - Manages browser history
  - Manage page title - so that it looks good on browser tab & browser back button history
  - 404 Screen
  - Error Screen
- [CSS Modules](https://github.com/css-modules/css-modules) - with eslint typo/unused css check and autocomplete
- ESLint and Prettier
- Type check via JSDocs and typescript compiler
- Simple global state manager
- SVG icon loader (with browser caching!)
- [Yorkie](https://www.npmjs.com/package/yorkie) git push linting hook
- [postcss-custom-media](https://www.npmjs.com/package/postcss-custom-media) plugin
- Jest + [Preact testing library](https://preactjs.com/guide/v10/preact-testing-library/)

### About Routes

You can find routes mapping (url-to-component mapping) at src/routes/routes.js.

You will notice that <code>lazy(() =&gt; import('./file'))</code> is
used for lazy loading and bundling each page's JS into separate bundles
for production.

You can also manage page titles from routes.js. `title` must be a string (it can have placeholders from route pattern. e.g. `Orders | :orderId`) or a function that which receives route info and returns a string.

Route components receives following properties about current route:
- url: current page url
- path: route pattern. e.g. `/user/:id`
- matches: path matches (as an object). e.g: `{ id: 'user1' }`
- title: the title text used to set head title tag

Path redirects can be configured in src/routes/redirects.js

### About global state manager utility
The state manager at src/third-party/state-manager follows the same
interface as CSR version of [react-global-states](https://www.npmjs.com/package/react-global-states).

store.js creates a single store for the app and gives you simpler interface to update specific global state properties.

getInitialState.js file is where you can add initial states for the store.

You can easily remove the three files if you don't want this state manager.

### About SVG icon loading

SVG icon components are at src/components/icons. The SVG files for it are at src/third-party/icons/.

If you want to add an SVG icon, you need to add `id="id"` attribute into the `<svg>` tag before using the SVG and then follow one of the icon component file at src/components/icons/ to convert the svg into a preact component.

Use src/third-party/icons/add-svg-id.js file provided to add the id.

```
node add-svg-id.js myicon.svg
# or full directory
# node add-svg-id.js .
```
It also removes fill color if present on `<svg>` tag.

Tip: You can find material UI icons at https://github.com/material-icons/material-icons

### Path aliases

`~` is short hand for src/ directory. So you don't have to do `import '../../../js-file-in-src-directory'`. You can just do `import '~/js-file-in-src-directory'`

Similarly for types, there is a shorthand alias `@` to the types/ directory. `import('@/RouteComponentProps')`

## Where to go next?

- Check package.json - dependencies, scripts and eslint rules
- Check the implementation of src/initialization/Router.jsx
- Read about [preact/compat](https://preactjs.com/guide/v10/switching-to-preact/)
- Add or remove stuff as you need. Check out other tools:
  - Whole list of preact related tools at [awesome-preact](https://github.com/preactjs/awesome-preact)
  - Icons - [Material Icons](https://github.com/material-icons/material-icons)
  - CSS Libraries - [Open Props](https://open-props.style), [Tailwind](https://tailwindcss.com), 
  - UI Libraries - [Material UI](https://github.com/mui/material-ui/tree/master/examples/preact), [Preact Fluid](https://github.com/ajainvivek/preact-fluid)
