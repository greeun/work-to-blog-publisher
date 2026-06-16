# Changelog

## [1.1.0] — 2026-06-17

Infographic-first visualization directive added to Phase 3 (blog post authoring), plus
semantic versioning introduced (`VERSION` + `CHANGELOG.md`).

### Added
- **3.2 Infographic visualization (REQUIRED)** — per-section recommendation table (mind map,
  webtoon, architecture, flowchart, chart/graph, timeline, quadrant, and other creative
  visualizations beyond the listed types). Target one visual per major section, diversify types,
  judged by "Can the post be understood by skimming the images alone?"
- **Plugin-independent images only** — every infographic rendered to a self-contained static
  image (PNG/JPG/SVG) and embedded via core `wp:image`; no inline Mermaid, shortcodes, or JS
  chart libraries. Production follows `wp-blog-post`'s Infographic-First Principle (`mmdc` → PNG,
  webtoon/custom via image-gen → `upload_media.py`).
- Execution checklist Step 4 gains an infographic item.
- `VERSION` (1.1.0) and `CHANGELOG.md` introduced.

### Prior unversioned history
- `414444c` Initial commit: Add work-to-blog-publisher skill
