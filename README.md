# Nuxt.js template

A Nuxt 4 starter template by [Viora Studio](https://github.com/viora-studio), built with [shadcn-vue](https://www.shadcn-vue.com/) and [Tailwind CSS](https://tailwindcss.com/).

## Features

- [Nuxt 4](https://nuxt.com/) with Vue 3
- [shadcn-vue](https://www.shadcn-vue.com/) components powered by Reka UI
- [Tailwind CSS v4](https://tailwindcss.com/)
- [Lucide](https://lucide.dev/) icons
- TypeScript support
- Vite-powered development experience

## Getting started

### Prerequisites

- [Node.js](https://nodejs.org/) (LTS recommended)
- [pnpm](https://pnpm.io/) (recommended) or another package manager

### Installation

Clone the repository and install its dependencies:

```bash
git clone https://github.com/viora-studio/nuxtjs-template.git
cd nuxtjs-template
pnpm install
```

### Development

Start the local development server:

```bash
pnpm dev
```

Nuxt will make the application available at [http://localhost:3000](http://localhost:3000).

## Adding components

This template uses shadcn-vue. To add a component, use the shadcn-vue CLI:

```bash
pnpm dlx shadcn-vue@latest add button
```

The generated components are placed in the `components/ui` directory, as configured in `nuxt.config.ts`.

## Using components

Components are registered with the `Ui` prefix. For example, you can use the button component in a Vue template:

```vue
<template>
  <UiButton>Click me</UiButton>
</template>
```

You can also import components explicitly:

```vue
<script setup lang="ts">
import { Button } from '@/components/ui/button'
</script>

<template>
  <Button>Click me</Button>
</template>
```

## Available scripts

| Command | Description |
| --- | --- |
| `pnpm dev` | Start the development server |
| `pnpm build` | Build the application for production |
| `pnpm generate` | Generate a static version of the application |
| `pnpm preview` | Preview the production build locally |
| `pnpm postinstall` | Prepare Nuxt and generate types |

## Production

Build the application for production:

```bash
pnpm build
```

To preview the production build locally:

```bash
pnpm preview
```

For static hosting, generate the application with:

```bash
pnpm generate
```

Learn more about deployment in the [Nuxt deployment documentation](https://nuxt.com/docs/getting-started/deployment).

## License

This project is licensed under the [MIT License](LICENSE).

Copyright (c) 2026 Viora Studio
