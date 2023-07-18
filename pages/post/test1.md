---
title: Test1
date: 2023-7-1
---

# Test1

```scss
@import "./font-face.scss";

.markdown-body {
  a {
    text-align: center;
    margin: 0 0.2rem;
    opacity: 0.75;

    &:hover {
      opacity: 1;
    }

    &::before {
      display: inline-block;
      content: "🔗";
      padding: 0 0.2rem;
    }

    &[href^="/post/"] {
      margin: 0;

      &::before {
        display: none;
      }
    }
  }

  s {
    opacity: 0.5;
    margin: 0 0.2rem;
  }

  ul {
    padding: 0;
    list-style: none;
  }

  code:not(pre code) {
    margin: 0 0.2rem;
    padding: 0.1em 0.4em;
    font-size: 0.8em;
    white-space: break-spaces;
    border-radius: 6px;
    background-color: rgba(175, 184, 193, 0.2);
  }

  pre,
  code {
    font-family: "JetBrains Mono", monospace;
  }

  pre {
    overflow-x: scroll;
    font-size: 0.8rem;
    margin: 0;
    padding: 0.5rem 1rem;
    border-radius: 5px;
  }
}

html {
  .markdown-body {
    .shiki-dark,
    .shiki-light {
      display: none;
    }

    .shiki-light {
      display: block;
    }
  }

  &.dark {
    .markdown-body {
      .shiki-light {
        display: none;
      }
      .shiki-dark {
        display: block;
      }
    }
  }
}
```