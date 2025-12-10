<div align="center">
  <h1>Tau Labs</h1>
</div>

Tau Labs is an AI hardware customization startup that helps small and medium businesses integrate conversational AI into their products. We provide end-to-end services from prototype hardware to optimized on-device inference and secure deployment.

## Table Of Contents

1. [Key Features](#key-features)
2. [Demo](#demo-)
3. [Quick start](#quick-start)
4. [Preview](#preview)
5. [Commands](#commands)
6. [Configure](#configure)
7. [Updating](#updating)
8. [Adding posts, notes, and tags](#adding-posts-notes-and-tags)
   - [Post Frontmatter](#post-frontmatter)
   - [Note Frontmatter](#note-frontmatter)
   - [Tag Frontmatter](#tag-frontmatter)
   - [Frontmatter Snippets](#frontmatter-snippets)
9. [Pagefind search](#pagefind-search)
10. [Analytics](#analytics)
11. [Deploy](#deploy)
12. [Acknowledgment](#acknowledgment)

## Key Features

- Astro v5 Fast 🚀
- Tailwind v4
- Accessible, semantic HTML markup
- Responsive & SEO-friendly
- Dark & Light mode
- MD & [MDX](https://docs.astro.build/en/guides/markdown-content/#mdx-only-features) posts & notes
  - Includes [Admonitions](https://astro-cactus.chriswilliams.dev/posts/markdown-elements/admonitions/)
- [Satori](https://github.com/vercel/satori) for creating open graph png images
- [Automatic RSS feeds](https://docs.astro.build/en/guides/rss)
- [Webmentions](https://webmention.io/)
- Auto-generated:
  - [sitemap](https://docs.astro.build/en/guides/integrations-guide/sitemap/)
  - [robots.txt](https://github.com/alextim/astro-lib/blob/main/packages/astro-robots-txt/README.md)
  - [web app manifest](https://github.com/alextim/astro-lib/blob/main/packages/astro-webmanifest/README.md)
- [Pagefind](https://pagefind.app/) static search library integration
- [Astro Icon](https://github.com/natemoo-re/astro-icon) svg icon component
- [Expressive Code](https://expressive-code.com/) code blocks and syntax highlighter

## Local development

This repository contains the Tau Labs website built with Astro. To run it locally:

```bash
# install deps
pnpm install

# dev server
pnpm dev
```

## Quick start

[Create a new repo](https://github.com/chrismwilliams/astro-theme-cactus/generate) from this template.

```bash
# npm 7+
npm create astro@latest -- --template chrismwilliams/astro-theme-cactus

# pnpm
pnpm dlx create-astro --template chrismwilliams/astro-theme-cactus
```

[![Deploy with Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/chrismwilliams/astro-theme-cactus) [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fchrismwilliams%2Fastro-theme-cactus&project-name=astro-theme-cactus)

## Preview

![Astro Theme Cactus in a light theme mode](https://github.com/chrismwilliams/astro-theme-cactus/assets/12715988/84c89d42-4525-4674-b10c-6d6ebdc06382)

![Astro Theme Cactus in a dark theme mode](https://github.com/chrismwilliams/astro-theme-cactus/assets/12715988/e0e575e2-445f-4c2d-a812-b5b53d2d9031)

## Commands

Replace pnpm with your choice of npm / yarn

| Command          | Action                                                         |
| :--------------- | :------------------------------------------------------------- |
| `pnpm install`   | Installs dependencies                                          |
| `pnpm dev`       | Starts local dev server at `localhost:3000`                    |
| `pnpm build`     | Build your production site to `./dist/`                        |
| `pnpm postbuild` | Pagefind script to build the static search of your blog posts  |
| `pnpm preview`   | Preview your build locally, before deploying                   |
| `pnpm sync`      | Generate types based on your config in `src/content/config.ts` |

## Configure

- Edit `src/site.config.ts` to set site metadata (title, description, url, social links).
- Replace assets in `/public` (icons, default social image) with your brand assets.
- Edit `src/components/SocialList.astro` to update social links.
- Customize styles in `src/styles/global.css` and Tailwind config.

## Updating

If you've forked the template, you can [sync the fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork) with your own project, remembering to **not** click Discard Changes as you will lose your own.

If you have a template repository, you can add this template as a remote, [as discussed here](https://stackoverflow.com/questions/56577184/github-pull-changes-from-a-template-repository).

## Adding posts, notes, and tags

This theme uses [Content Collections](https://docs.astro.build/en/guides/content-collections/) to organise local Markdown and MDX files, as well as type-checking frontmatter with a schema -> `src/content.config.ts`.

Adding a post/note/tag is as simple as adding your .md(x) files to either `src/content/post`, `src/content/note`, and `src/content/tag` folders, the filename of which will be used as the slug/url.

The Tag collection allows you to override the content for generated tag pages. For example the template includes `src/content/tag/test.md` which overrides the content shown in `your-domain.com/tags/test`.

> **Note**
> For a tag page to work, the file name (`src/content/tag/*`) must also be in a post's [tags frontmatter.](#post-frontmatter)

The posts/notes/tags included with this template are there as an example of how to structure your frontmatter. Additionally, the [Astro docs](https://docs.astro.build/en/guides/markdown-content/) has a detailed section on markdown pages.

### Post Frontmatter

| Property (\* required) | Description                                                                                                                                                                                                                                                                                                  |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| title \*               | Self explanatory. Used as the text link to the post, the h1 on the posts' page, and the pages title property. Has a max length of 60 chars, set in `src/content/config.ts`                                                                                                                                   |
| description \*         | Similar to above, used as the seo description property. Has a min length of 50 and a max length of 160 chars, set in the post schema.                                                                                                                                                                        |
| publishDate \*         | Again pretty simple. To change the date format/locale, currently **en-GB**, update the date option in `src/site.config.ts`. Note you can also pass additional options to the component `<FormattedDate>` if required.                                                                                        |
| updatedDate            | This is an optional date representing when a post has been updated, in the same format as the publishDate.                                                                                                                                                                                                   |
| tags                   | Tags are optional with any created post. Any new tag(s) will be shown in `your-domain.com/posts` & `your-domain.com/tags`, and generate the page(s) `your-domain.com/tags/[yourTag]`                                                                                                                         |
| coverImage             | This is an optional object that will add a cover image to the top of a post. Include both a `src`: "_path-to-image_" and `alt`: "_image alt_". You can view an example in `src/content/post/cover-image.md`.                                                                                                 |
| ogImage                | This is an optional property. An OG Image will be generated automatically for every post where this property **isn't** provided. If you would like to create your own for a specific post, include this property and a link to your image, the theme will then skip automatically generating one.            |
| draft                  | This is an optional property as it is set to false by default in the schema. By adding true, the post will be filtered out of the production build in a number of places, inc. getAllPosts() calls, og-images, rss feeds, and generated page[s]. You can view an example in `src/content/post/draft-post.md` |

### Note Frontmatter

| Property (\* required) | Description                                                                                                           |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------- |
| title \*               | Used as the link text to the note, the pages title property, and the h1 of said note page. Has a max length 60 chars. |
| description            | Optional. Used for the head meta description property.                                                                |
| publishDate \*         | ISO 8601 format with offsets allowed.                                                                                 |

### Tag Frontmatter

| Property (\* required) | Description                                                                                             |
| ---------------------- | ------------------------------------------------------------------------------------------------------- |
| title                  | Optional. Used as the h1 on the tags' page, and the pages title property. Has a max length of 60 chars. |
| description            | Optional. Used for the head meta description and the first paragraph under the h1.                      |

### Frontmatter snippets

This project includes a helpful VSCode snippet which creates a frontmatter 'stub' for posts and notes, found at `.vscode/post.code-snippets`. Start typing the word `frontmatter` on your newly created .md(x) file to trigger it. Visual Studio Code snippets appear in IntelliSense via (⌃Space) on mac, (Ctrl+Space) on windows.

## Pagefind search

This integration brings a static search feature for searching blog posts and notes. In its current form, pagefind only works once the site has been built. This theme adds a postbuild script that should be run after Astro has built the site. You can preview locally by running both build && postbuild.

Search results only includes pages from posts and notes. If you would like to include other/all your pages, remove/re-locate the attribute `data-pagefind-body` to the article tag found in `src/layouts/BlogPost.astro` and `src/components/note/Note.astro`.

It also allows you to filter posts by tags added in the frontmatter of blog posts. If you would rather remove this, remove the data attribute `data-pagefind-filter="tag"` from the link in `src/components/blog/Masthead.astro`.

If you would rather not include this integration, simply remove the component `src/components/Search.astro`, and uninstall both `@pagefind/default-ui` & `pagefind` from package.json. You will also need to remove the postbuild script from here as well.

You can reduce the initial css payload of your css, [as demonstrated here](https://github.com/chrismwilliams/astro-theme-cactus/pull/145#issue-1943779868), by lazy loading the web components styles.

## Analytics

You may want to track the number of visitors you receive to your blog/website in order to understand trends and popular posts/pages you've created. There are a number of providers out there one could use, including web hosts such as [vercel](https://vercel.com/analytics), [netlify](https://www.netlify.com/products/analytics/), and [cloudflare](https://www.cloudflare.com/web-analytics/).

This theme/template doesn't include a specific solution due to there being a number of use cases and/or options which some people may or may not use.

You may be asked to included a snippet inside the **HEAD** tag of your website when setting it up, which can be found in `src/layouts/Base.astro`. Alternatively, you can add the snippet in `src/components/BaseHead.astro`.

## Deploy

[Astro docs](https://docs.astro.build/en/guides/deploy/) has a great section and breakdown of how to deploy your own Astro site on various platforms and their idiosyncrasies.

By default the site will be built (see [Commands](#commands) section above) to a `/dist` directory.

## Acknowledgment

This theme was inspired by [Hexo Theme Cactus](https://github.com/probberechts/hexo-theme-cactus)

## License

MIT
