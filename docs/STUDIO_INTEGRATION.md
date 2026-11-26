# Studio Integration: Moodboard to Mockups & Visual Makeover

This integration bridges the **Moodboard to Mockups Studio** with the **Visual Makeover** evidence-first architecture in `JussAndCo/visual-makeover1`.

## 1. Trust Model & Evidence Pipeline

- **Evidence Ingestion:** Browser captures generated via the Opera MCP adapter (`tab_content`, `screenshot`, `go_to_page`) can be directly imported into the studio's Step 1 (Mood Board) with validated byte signatures and SHA-256 hashes.
- **Consent Gate:** In full alignment with Visual Makeover's 4-layer trust model (Identity -> Notice -> Grant -> Receipt), uploaded images and captured tabs require affirmative user consent before being downscaled and sent to vision AI models.
- **Fail-Closed Fallback:** When image consent is absent or vision models are unavailable, the studio falls back gracefully to annotation-only synthesis without fabricating visual claims.

## 2. Four-Step Design Workflow

1. **Mood Board (`/`):** Multi-file ingestion (PNG, JPEG, WebP) up to 10MB, 24 curated SVG templates, masonry layout, notes, and tags.
2. **Design Brief (`/brief`):** Strict Zod schema validation producing 2–3 sentence art direction, 5–6 color swatches with semantic roles, and Google Font pairings.
3. **Your App (`/app`):** Core elevator pitch, 3–8 interactive feature specifications, and WCAG 2.2 AA accessibility profiles.
4. **Mockups & Storyboards (`/mockups`):** Feature-aware phone screen plans rendered using trusted React components (whitelisted tokens, no raw AI code execution) with client-side PNG ZIP export and Markdown brief downloads.

## 3. Schema Alignment

The studio's `Brief` schema (`src/lib/mm/schema.ts`) maps directly to `makeover.json`:
- `palette`: primary, secondary, accent, background, text, surface
- `typography`: heading, body font suggestions with explicit reasoning
- `rules`: layout, imagery, and things to avoid

## 4. Branch & Release Information

- Target Branch: `sync/moodboard-to-mockups`
- Base Commit: `e03bca9`
