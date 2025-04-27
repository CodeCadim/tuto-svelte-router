# Tiny Router for Svelte

This is a demonstration of a very tiny router using URL hash to define the Svelte component to display and converting the query parameters as props.

## Usage

```bash
node esbuild.js
```

Open your browser on http://localhost:5432 and click !

Each link to a component is of the form :

```html
<a href="#page=blog&art=1">Art. 1</a>
```

with a '#page=component' to select the component to display and the props as search query, if any.
