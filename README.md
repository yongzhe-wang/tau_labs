<div align="center">
  <h1>Tau Labs</h1>
</div>

Tau Labs is an AI hardware customization startup based in Philadelphia, PA, built by engineers from the University of Pennsylvania. We help small and medium businesses integrate conversational AI into their products, providing end-to-end services from prototype hardware to optimized on-device inference and secure deployment.

## Table Of Contents

1. [Getting Started](#getting-started)
2. [Commands](#commands)
3. [Tech Stack](#tech-stack)
4. [Content Management](#content-management)

## Getting Started

This website is built with Astro. To run it locally:

```bash
# install deps
pnpm install

# dev server
pnpm dev
```

## Commands

| Command          | Action                                                         |
| :--------------- | :------------------------------------------------------------- |
| `pnpm install`   | Installs dependencies                                          |
| `pnpm dev`       | Starts local dev server at `localhost:3000`                    |
| `pnpm build`     | Build your production site to `./dist/`                        |
| `pnpm postbuild` | Pagefind script to build the static search of your blog posts  |
| `pnpm preview`   | Preview your build locally, before deploying                   |
| `pnpm sync`      | Generate types based on your config in `src/content/config.ts` |

## Tech Stack

- **Framework**: Astro v5
- **Styling**: Tailwind CSS v4
- **Search**: Pagefind
- **Icons**: Astro Icon
- **Content**: MDX for posts and notes

## Content Management

This project uses [Content Collections](https://docs.astro.build/en/guides/content-collections/) to organize content.

- **Blog Posts**: Add `.md` or `.mdx` files to `src/content/post/`.
- **Notes**: Add `.md` or `.mdx` files to `src/content/note/`.
- **Tags**: Add `.md` files to `src/content/tag/` to customize tag pages.

### Frontmatter

Ensure your markdown files have the correct frontmatter.

**Post Example:**
```yaml
---
title: "My Post Title"
description: "A short description."
publishDate: "2025-12-10"
tags: ["ai", "hardware"]
---
```

## License

MIT
