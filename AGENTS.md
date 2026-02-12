# Ctxfy Documentation Site

Public documentation site for the **Ctxfy API** — AI context management. Built on Documentation.AI (Mintlify-style) with MDX, OpenAPI spec, and structured navigation.

## Purpose

Single public entry point for developers integrating with Ctxfy:

- **Documentation** — Introduction, Quickstart, Core Concepts
- **API Reference** — Auto-generated from OpenAPI spec
- **Help Center** — FAQs, guides, troubleshooting
- **Changelog** — API updates and release notes

## Public Documentation includes:

- Guidelines for the integration with the service.
- API documentation.
- Step-by-step guides for integration with the service.
- Helpful tips and tricks for the developers.
- Best practices for the development.
- Help Center topics, articles and FAQs.
- Changelog, release notes and other developer announcements.

## Public Documentation not includes:

- Business process documentation.
- System architecture principles.
- Storage strategy.
- Frontend integration specification.
- Reports.
- RMQ message contracts.

## Public Documentation Rules

When writing or updating content in the `docs/documentation-site` directory:

- **Language:** Docs must be written in English.
- **Service name:** Use **Ctxfy** (Contextify) as the service name. Do not use internal project names (e.g. ctxfy-vault) in user-facing content.
- **Authentication:** Do not describe JWT auth type. API auth for users is implemented using API keys only.
- **No internals:** Do not expose internal implementation details or inter-service interactions (e.g. RabbitMQ, Firebase, outbox, workflow pipelines). Document only the external API contract and integration flow.

## Structure

```
./
├── documentation.json   # Site config, navigation, branding
├── openapi.yaml        # API spec → API Reference tab
├── introduction.mdx    # Landing page
├── quickstart.mdx
├── concepts.mdx
├── authentication.mdx
├── changelog.mdx
├── help-center.mdx
├── notice.mdx
├── components.mdx
├── components/         # MDX component examples (Callout, Card, Steps, Tabs)
├── help-center/
│   ├── faq/            # Why Ctxfy, Getting Started, Use Cases, Pricing, Security
│   ├── guides/         # First request, Setup project
│   └── troubleshooting/
└── openapi.yaml
```

## Navigation (documentation.json)

| Tab | Content |
|-----|---------|
| **Documentation** | Start Here → Introduction, Quickstart, Core Concepts |
| **API Reference** | Authentication + Endpoints (from `openapi.yaml`) |
| **Help Center** | FAQs, Troubleshooting, Guides |
| **Changelog** | Release notes and API changes |

## Editing

### Page content
Edit `.mdx` files. Use MDX components: `<Callout>`, `<Card>`, `<Columns>`, `<Steps>`, `<Tabs>`, `<Update>`.

### Navigation
Update `documentation.json` — add/remove pages, groups, or tabs.

### API Reference
Regenerate from the source of truth:
1. Copy `../api-documentation.yaml` → `openapi.yaml`
2. Apply Public Doc rules: Ctxfy title, API keys only; remove internal references (RMQ, workflows, system services)
3. Fix `CollectionTreeResponse` circular ref if present

See `notice.mdx` for sync notes.

## Relation to Host Project (ctxfy-vault)

- **Source of truth for API:** `../service.md`, `../api-documentation.yaml`
- Docs site mirrors the public API contract; keep in sync on releases
- Public Docs rules (AGENTS.md): English, Ctxfy name, API keys only, no internals

## Relation to Marketing Hub (../marketing-hub)

Use messaging and terminology from `../marketing-hub/` for user-facing copy (value props, taglines, FAQs). Do not duplicate; reference or copy from the hub.
