# Next.js Docker Template

A production-ready starter template for building Next.js applications containerized with Docker. Includes a multi-stage Dockerfile for both development and production, a structured `src/` layout, and a pre-configured toolchain.

## Tech Stack

| Tool         | Version |
| ------------ | ------- |
| Next.js      | 16      |
| React        | 19      |
| TypeScript   | 5       |
| Tailwind CSS | 4       |
| pnpm         | latest  |

## Features

- **Multi-stage Docker build** — separate `dev` and `production` targets in a single Dockerfile using Node 24 Alpine
- **Standalone output** — Next.js is configured with `output: "standalone"` for minimal production images
- **Docker Compose** — `docker-compose.dev.yaml` for local development and `docker-compose.yaml` for production deployment via a pre-built image
- **Structured `src/` layout** — organized folders for `components`, `hooks`, `lib`, `schemas`, `scripts`, `stores`, and `types`, each with a barrel `index.ts`
- **ESLint** — configured with `eslint-config-next` (Core Web Vitals), `eslint-config-prettier`, and `eslint-plugin-check-file` enforcing kebab-case filenames
- **Prettier** — with `prettier-plugin-tailwindcss` for class sorting and `@trivago/prettier-plugin-sort-imports` for import ordering

## Getting Started

### Local development (without Docker)

```bash
pnpm install
pnpm dev
```

### Local development (with Docker)

```bash
docker compose -f docker-compose.dev.yaml up --build
```

The app will be available at [http://localhost:3000](http://localhost:3000).

### Production

Build and run the production image:

```bash
docker build --target runner -t next-docker-template .
docker run -p 3000:3000 --env-file .env next-docker-template
```

Or pull and run the pre-built image via Docker Compose:

```bash
docker compose up
```

## Project Structure

```plain
src/
├── app/            # Next.js App Router (layout, pages, global styles)
├── components/     # Shared UI components
├── hooks/          # Custom React hooks
├── lib/            # Utility functions and shared logic
├── schemas/        # Validation schemas (e.g. Zod)
├── scripts/        # Standalone scripts
├── stores/         # State management stores
└── types/          # Shared TypeScript types and interfaces
```

## Scripts

```bash
pnpm dev       # Start development server
pnpm build     # Build for production
pnpm start     # Start production server
pnpm lint      # Run ESLint
pnpm format    # Format source files with Prettier
```

## License

[MIT](LICENSE)
