---
title: Test2
date: 2021-2-1
---

# Test2

```ts
import "virtual:uno.css";
import "./styles/index.scss";
import "./styles/markdown.scss";

import { ViteSSG } from "vite-ssg";
import autoRoutes from "pages-generated";
import App from "./App.vue";

const routes = autoRoutes.map(i => {
  return {
    ...i,
  };
});

export const createApp = ViteSSG(App, { routes });
```