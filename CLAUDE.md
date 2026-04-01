# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file static HTML storefront for **BrightSprout Kids**, a fictional baby/toddler toy brand. No build system, no dependencies, no framework — just `baby-store.html`.

Open `baby-store.html` directly in a browser to view the site.

## Architecture

Everything lives in `baby-store.html`:

- **CSS** — CSS custom properties (`--bg`, `--card`, `--ink`, `--accent`, etc.) defined in `:root` drive the entire color system. Responsive breakpoint at `760px`.
- **Product data** — Hardcoded as a `products` array in the `<script>` block. Each product has: `id`, `name`, `category`, `art`, `price`, `tagline`, `description`, `features[]`, `pills[]`.
- **Rendering** — `renderProducts()` generates product cards via template literals injected into `<section class="grid" id="shop">`.
- **Product modal** — A native `<dialog>` element (`#productDialog`) is populated and opened by `openProduct(id)`. Closes on backdrop click or the × button.
- **Art field** — Can be either an `<img>` tag string (for products with images) or an emoji string (for products without images).

## Image Paths

Product images in the `art` field currently use absolute `file:///C:/images/` paths, which only work if the images exist at `C:\images\` on the local machine. The repo's `images/` folder contains the actual image files (`chewer.png`, `mobile.png`, `onesie.png`, `gambler.png`). If updating image references, use relative paths like `images/chewer.png` instead.
