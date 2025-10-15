# BBC News Display - Design Guidelines

## Design Approach
**System**: Material Design with BBC News visual language inspiration
**Justification**: News consumption requires clarity, hierarchy, and quick scanning. The 16:9 display format suggests this is for viewing from a distance (TV/monitor), demanding bold typography and clear visual structure.

## Core Design Elements

### A. Color Palette
**Dark Mode Primary**:
- Background: 12 8% 8% (deep charcoal)
- Surface cards: 12 8% 12% (elevated charcoal)
- BBC brand accent: 0 100% 50% (signature red - use sparingly for category tags/live indicators)
- Text primary: 0 0% 98%
- Text secondary: 0 0% 70%

**Light Mode** (if needed):
- Background: 0 0% 98%
- Cards: 0 0% 100%
- Text: 12 8% 15%

### B. Typography
**Fonts**: 
- Headlines: "Inter" or "Roboto" at 700 weight
- Body: "Inter" or "Roboto" at 400 weight

**Scale for 16:9 Display**:
- Main headlines: text-xl to text-2xl (readable from distance)
- Category/timestamp: text-sm
- Maintain 1.5 line-height for readability

### C. Layout System
**Grid Structure**: 4 columns × 2 rows (8 tiles total)
**Spacing primitives**: Tailwind units of 2, 4, 6, and 8
- Outer container: p-6 to p-8
- Card padding: p-4 to p-6
- Gap between tiles: gap-4 to gap-6

**Card aspect ratio**: 16:9 per tile (matches screen format)

### D. Component Library

**News Tile Cards**:
- Full-bleed news image (65% of card height)
- Overlay gradient on image bottom (for headline readability)
- Headline overlaid on image bottom OR below image
- Category tag (top-left corner): Small pill with accent color
- Timestamp: Bottom-right, subtle
- Hover state: Subtle scale (1.02) or glow effect

**Information Hierarchy**:
1. News image (primary visual anchor)
2. Headline (bold, high contrast)
3. Category tag (contextual identifier)
4. Timestamp (tertiary information)

### E. Imagery Strategy

**News Images**:
- All 8 tiles must include compelling news photography
- Images should fill card area edge-to-edge
- Overlay dark gradient (bottom 40%) to ensure text readability: `bg-gradient-to-t from-black/80 to-transparent`
- Fallback: BBC logo watermark on neutral background if image unavailable

**Image Placement**:
Each of the 8 tiles requires a distinct news image showcasing the story visually.

### F. Special Considerations

**16:9 Optimization**:
- Full viewport usage without scrolling
- Larger text sizes for distance viewing
- High contrast ratios (WCAG AAA for large text)
- Minimal animations (static display focused)

**BBC Branding Elements**:
- Optional BBC logo in top-left corner
- Red accent sparingly (live indicators, breaking news tags)
- Clean, journalistic aesthetic
- Trust-building through clarity and organization

**Data Display**:
- Live update indicator (pulsing red dot for breaking news)
- "Updated X minutes ago" timestamp
- Clear category labels (Politics, Business, Tech, etc.)
- No clutter - focus on essential information only

### G. Interaction Model
Since this is a display screen (not interactive in traditional sense):
- Auto-refresh every 5-10 minutes
- Smooth fade transitions between content updates
- If interactive: Click entire card to open story detail
- Minimal hover effects (may not be applicable for TV displays)

**Performance**: Optimize for static display with periodic API polling, preload images, lazy load if scrolling is implemented (though 8 tiles should fit in viewport).