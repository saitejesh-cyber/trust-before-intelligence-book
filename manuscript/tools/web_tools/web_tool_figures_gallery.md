# Figures Gallery - Digital Tool Specification

## Overview

**Tool Name:** Trust Before Intelligence - Figures Gallery
**Purpose:** Provide readers with a centralized, searchable collection of all 112 figures from the book
**URL:** /figures or /gallery

---

## Value Proposition

- **Print book readers:** Access high-resolution versions of figures
- **Digital readers:** Quick reference without flipping through chapters
- **Presenters:** Download figures for presentations and training
- **Practitioners:** Visual reference for implementation

---

## Content Inventory

### Total Figures: 112

| Chapter | Count | Figure Range | In Print |
|---------|-------|--------------|----------|
| Chapter 0: Trust Before Intelligence | 4 | 0.0 - 0.3 | Yes |
| Chapter 1: Why Agents Fail | 6 | 1.0 - 1.5 | Yes |
| Chapter 2: INPACT Framework | 12 | 2.0 - 2.11 | Yes |
| Chapter 3: From BI to Agent | 4 | 3.0 - 3.3 | Yes |
| Chapter 4: Foundation Layers | 11 | 4.0 - 4.10 | Yes |
| Chapter 5: Intelligence Layers | 13 | 5.1 - 5.13 | Yes |
| Chapter 6: Transparency & Orchestration | 14 | 6.1 - 6.14 | Yes |
| Chapter 7: GOALS Framework | 14 | 7.1 - 7.14 | Yes |
| Chapter 8: Architecture in Action | 10 | 8.1 - 8.10 | Yes |
| Chapter 9: Measuring Readiness | 6 | 9.1 - 9.6 | Yes |
| Chapter 10: Week-by-Week Implementation | 7 | 10.1 - 10.7 | Digital |
| Chapter 11: Technology Selection | 5 | 11.1 - 11.5 | Digital |
| Chapter 12: Running Agents at Scale | 6 | 12.1 - 12.6 | Digital |

---

## User Interface

### Navigation Options

**1. Browse by Chapter**
- Accordion or tab view
- Chapter name + figure count
- Thumbnail grid within each chapter

**2. Browse by Category**
- Architecture Diagrams
- Framework Visualizations (INPACT, GOALS)
- Transformation Timelines
- Before/After Comparisons
- Data Flow Diagrams
- Implementation Roadmaps

**3. Search**
- Search by figure number (e.g., "Figure 5.7")
- Search by keyword (e.g., "ABAC", "Layer 3", "semantic")
- Search by chapter name

### Figure Display

**Thumbnail View:**
- Grid of figure thumbnails
- Figure number + short title
- Chapter indicator

**Detail View (on click):**
- Full-size figure
- Figure number and title
- Chapter reference with page number
- Brief description/context
- Download button (PNG, PDF)
- "View in Book" link (digital readers)

---

## Features

### Core Features

1. **Responsive Gallery**
   - Desktop: 4-column grid
   - Tablet: 2-column grid
   - Mobile: 1-column list

2. **Lightbox View**
   - Click to enlarge
   - Keyboard navigation (arrows)
   - Zoom capability

3. **Download Options**
   - Individual figure (PNG, PDF)
   - Download all figures in chapter (ZIP)
   - Download all figures (ZIP)

4. **Filtering**
   - By chapter
   - By category/type
   - Print book only vs. all

### Enhanced Features (Phase 2)

1. **Favorites**
   - Save frequently used figures
   - Personal collection

2. **Presentation Mode**
   - Slideshow view
   - Full-screen display

3. **Share**
   - Direct link to specific figure
   - Social sharing

---

## Figure Categories

For filtering and organization:

| Category | Description | Example Figures |
|----------|-------------|-----------------|
| **Architecture** | System architecture diagrams | 4.2, 5.3, 6.13 |
| **Framework** | INPACT and GOALS visuals | 2.0, 7.1, 7.12 |
| **Transformation** | Before/after, journey maps | 0.0, 2.5, 8.10 |
| **Timeline** | Implementation timelines | 4.8, 5.11, 6.11 |
| **Data Flow** | Process and data flows | 6.10, 7.7, 8.3 |
| **Comparison** | Side-by-side comparisons | 2.6-2.11, 3.2 |
| **Assessment** | Scoring, dashboards | 7.4, 8.1, 9.3 |
| **Layer Detail** | Individual layer deep-dives | 4.4, 5.5, 6.4 |

---

## Technical Implementation

### Image Requirements

- **Source format:** SVG (preferred) or high-res PNG
- **Display format:** WebP with PNG fallback
- **Thumbnail size:** 300x200px
- **Full size:** 1200x800px (minimum)
- **Retina support:** 2x images

### Page Structure

```
/figures
├── /chapter/0
├── /chapter/1
├── ...
├── /chapter/12
├── /category/architecture
├── /category/framework
└── /figure/5-7 (direct link to Figure 5.7)
```

### SEO

- Page title: "Figures Gallery | Trust Before Intelligence"
- Meta description: "Browse all 112 figures from Trust Before Intelligence. Architecture diagrams, frameworks, and implementation guides for AI agent infrastructure."
- Alt text for all images
- Structured data for image gallery

---

## Integration with Book

### Print Book Reference

Add to back matter (Digital Companion section):

> **Figures Gallery:** View and download all figures at [URL]/figures

### Chapter Cross-References

Each chapter's "Online Resources" section can reference:

> *High-resolution versions of all figures in this chapter are available in the Figures Gallery at [URL]/figures/chapter/X*

---

## Content Extraction Process

### Steps to Build Gallery

1. **Extract figure titles** from all chapter markdown files
2. **Generate/export figures** from Mermaid code blocks
3. **Create thumbnails** at 300x200px
4. **Write descriptions** (1-2 sentences per figure)
5. **Categorize** each figure
6. **Build gallery pages**

### Figure Title Format in Book

```markdown
**Figure X.Y: Title Here**
```

All 112 figures follow this format and can be programmatically extracted.

---

## Success Metrics

- Page views
- Downloads per figure
- Most viewed figures
- Search queries (to understand what readers look for)
- Time on page

---

## Timeline

| Phase | Scope | Effort |
|-------|-------|--------|
| **Phase 1** | Basic gallery with chapter navigation, search, download | 2-3 days |
| **Phase 2** | Categories, filtering, favorites | 1-2 days |
| **Phase 3** | Presentation mode, sharing | 1 day |

---

## Dependencies

- Final figures exported from book
- Consistent naming convention
- Hosting for image files
- Integration with main book website