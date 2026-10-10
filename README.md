# Registry template

A Next.js and Tailwind CSS v4 template for hosting a custom shadcn/ui component registry. This fork includes placeholders consumed by [create-shadcn-registry](https://github.com/SpyC0der77/create-shadcn-registry).

## Scaffold a registry

The easiest setup is through the companion CLI:

```bash
npx create-shadcn-registry
```

Choose your registry name, project folder, style, and homepage. See the [CLI README](https://github.com/SpyC0der77/create-shadcn-registry#readme) for its flags and component commands.

## Manual setup

Use Node.js 22 and pnpm.

```bash
git clone https://github.com/SpyC0der77/registry-template.git
cd registry-template
pnpm install
```

Before building, replace `{{REGISTRY_NAME}}`, `{{HOMEPAGE}}`, and `{{STYLE_NAME}}` in the registry manifest and source paths. Make sure every file listed in `registry.json` exists and the demo page imports components you actually provide. The raw template is not ready to build without customization.

```bash
pnpm registry:build
pnpm build
pnpm start
```

For local development after customization, use `pnpm dev` and open [localhost:3000](http://localhost:3000).

## Registry files

- [`registry.json`](registry.json) defines item names, dependencies, types, and source files.
- [`registry/`](registry/) contains component sources.
- `pnpm registry:build` generates installable JSON under `public/r/`.
- [`app/`](app/) contains the demo page and registry route handler.

Deploy the generated app, then install a registry item into a consumer project using its public URL:

```bash
npx shadcn@latest add https://your-registry.example/r/example.json
```

Set `NEXT_PUBLIC_BASE_URL` to your deployment URL if you use the **Open in v0** button. The `lint` script calls the legacy `next lint` command. Review the lint configuration before using it with a newer Next.js release.

## References

[shadcn registry documentation](https://ui.shadcn.com/docs/registry). This fork is based on [shadcn-ui/registry-template](https://github.com/shadcn-ui/registry-template).
