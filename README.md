# kentra-agentic-plugins

The **branded catalog** of kentra's agentic coding primitives, distributed as Claude Code
plugins. This repo holds no skills of its own — it is a thin
[`marketplace.json`](./.claude-plugin/marketplace.json) that lists each primitive plugin by
its own repository.

## Why a catalog (and not per-primitive marketplaces)

Kentra's primitives are **neutral, reusable, MIT** and each lives in its own repo
(`adr-sourced-constitution`, `spec-lifecycle`, …). They carry only `plugin.json` + `skills/`
— no branding, no `kentra-` prefix.

This catalog is where the branding lives. It is to **distribution** what
[`kentra-sdlc`](../kentra-sdlc.md) is to **methodology**: the branded composition of neutral
primitives. Registering it once surfaces the whole suite, and adding a new primitive is a
one-line change here rather than a new marketplace registration on every machine.

## Register (once, user scope)

```
/plugin marketplace add kentra-io/kentra-agentic-plugins
/plugin install adr-sourced-constitution@kentra-agentic-plugins   # choose "User" scope
```

Because the host `~/.claude` is shared into every claudebox container, a user-scope
registration propagates everywhere automatically.

Installed skills are namespaced by plugin, e.g. `adr-sourced-constitution:adr-draft`,
`adr-sourced-constitution:plan-gate`.

### Local development

The catalog resolves primitives by their pushed GitHub state. While iterating on a primitive
before pushing, register its working tree directly instead:

```
/plugin marketplace add ./adr-sourced-constitution
```

## Catalog status

| Plugin | Status |
| --- | --- |
| `adr-sourced-constitution` | Manifest scaffolded on branch `plugin/claude-code-manifest`; installs once that branch is merged + pushed to `main`. |
| `spec-lifecycle` | Pending — add once its skills land. |
