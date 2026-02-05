# Banana Foundation - Advanced Reference

Detailed reference for complex token scenarios and advanced usage patterns.

## Token Naming Conventions

### Tier-Specific Naming

**CORE** (Primitives):
- Color: `{color-family}/{shade}` e.g., `neutral/600`, `blue/400`
- Spacing: `space/{value}` e.g., `space/8`, `space/24`
- Sizing: `size/{value}` e.g., `size/16`, `size/40`
- Radius: `radius/{variant}` e.g., `radius/1x`, `radius/full`

**SEMANTICS** (Platform-Agnostic):
- Format: `{category}/{token-name}`
- Categories: surface, status, content, icon, brand, border, interactive
- Example: `content/primary`, `status/error-subtle`
- Pattern: Describes meaning, not implementation

**THEME** (Component-Specific):
- Format: `{component}/{variant}/{property}`
- Component: button, input, dropdown, etc.
- Variant: primary, secondary, disabled, etc.
- Property: background, text, border, etc.
- Example: `button/primary/background`, `input/focused/border`

### Color Family Reference

**Primary Colors**:
- Neutral: Gray scale (100-950)
- Blue: Primary interactive color
- Green: Success states
- Red: Error states
- Orange: Warning states
- Gold: Special emphasis

**Shade Values**: 100, 200, 300, 400, 500, 600, 700, 800, 850, 900, 950
- 100-300: Light shades
- 400-500: Mid tones
- 600-700: Main shades
- 800+: Dark shades

**Opacity Variants**: X02, X03, X04 (e.g., blue/102 = 20% opacity)

---

## Aliasing Patterns & Examples

### Pattern 1: Simple Content Text

```
component/element/text
    ↓ aliases
content/primary
    ↓ aliases
neutral/900
    ↓ aliases
Core primitive
```

### Pattern 2: Status Badge

```
badge/success/background
    ↓ aliases
status/success-subtle
    ↓ aliases
green/100
    ↓ aliases
Core primitive
```

### Pattern 3: Interactive Button

```
button/primary/background
    ↓ aliases
interactive/primary
    ↓ aliases
brand/primary
    ↓ aliases
blue/600
    ↓ aliases
Core primitive
```

### Pattern 4: Disabled State

```
input/disabled/background
    ↓ aliases
surface/default (with opacity)
    ↓ aliases
neutral/100
    ↓ aliases
Core primitive
```

### Pattern 5: Focus Ring

```
button/primary/focus-ring
    ↓ aliases
border/focus
    ↓ aliases
accent/600
    ↓ aliases
Core primitive
```

---

## Component Token Inventory

### Forms (45 tokens)

**Button** (12 tokens):
- primary/background, primary/text, primary/border
- secondary/background, secondary/text, secondary/border
- disabled/background, disabled/text, disabled/border
- hover states for each variant

**Input** (10 tokens):
- default/background, default/border, default/text
- focused/background, focused/border, focused/ring
- error/background, error/border, error/text
- placeholder/text

**Dropdown** (8 tokens):
- trigger/background, trigger/border, trigger/text
- menu/background, menu/border
- item/default, item/hover, item/selected

**Checkbox & Radio** (6 tokens):
- unchecked/background, unchecked/border
- checked/background, checked/border
- disabled/background, disabled/border

**Toggle** (5 tokens):
- off/background, off/handle
- on/background, on/handle
- disabled/background

### Navigation (18 tokens)

**Nav Bar** (6 tokens):
- background, text, hover
- active/background, active/text
- border

**Breadcrumbs** (4 tokens):
- text, separator
- link/default, link/hover

**Pagination** (4 tokens):
- button/default, button/hover
- button/active, button/disabled

**Tabs** (4 tokens):
- inactive/text, inactive/border
- active/text, active/border

### Feedback (28 tokens)

**Toast** (12 tokens):
- success/background, success/text, success/border, success/icon
- error/background, error/text, error/border, error/icon
- warning/background, warning/text, warning/border, warning/icon

**Alert** (8 tokens):
- success/background, success/text
- error/background, error/text
- warning/background, warning/text
- info/background, info/text

**Modal** (4 tokens):
- overlay/background, content/background
- header/border, footer/border

**Tooltip** (4 tokens):
- background, text, border, arrow

### Data Display (24 tokens)

**Table** (8 tokens):
- header/background, header/text
- row/default, row/hover
- row/stripe, row/selected
- border/default, border/divider

**Badge** (4 tokens):
- default/background, default/text
- subtle/background, subtle/text

**Tag** (6 tokens):
- default/background, default/text, default/border
- hover/background, hover/text, hover/border

**Progress Bar** (6 tokens):
- background, fill, border
- success/fill, warning/fill, error/fill

### AI-Specific (15 tokens)

**AI Response** (5 tokens):
- background, border, text
- code-block/background, code-block/text

**AI Card** (5 tokens):
- background, border, header/background
- hover/background, active/background

**AI Prompt** (5 tokens):
- input/background, input/border, input/text
- button/background, button/text

---

## Semantic Token Deep Dive

### SURFACE Category Rationale (Content Layer)

**Why 6 surface tokens?**
- Allows expressing depth and hierarchy for content
- Each serves specific interaction patterns
- Supports both light and dark modes
- Context-dependent (follows page background)

**Surface Hierarchy**:
```
surface/overlay (topmost)
    ↓
surface/raised
    ↓
surface/default
    ↓
surface/sunken (lowest)
```

**When to use each**:
- `default`: Main page/background, content areas
- `raised`: Cards, panels, lifted elements, elevated content
- `sunken`: Input wells, contained spaces, recessed areas
- `overlay`: Modals, dropdowns, popovers, floating content
- `hover`/`pressed`: Interactive state changes on content

**Key**: SURFACE follows page background in both modes
- Light mode: Light colors (neutral/0-200)
- Dark mode: Dark colors (neutral/950-800)
- Use for: Cards, inputs, modals, sidebars, headers, footers (context-dependent)

### PERSISTENT Category Rationale ✨ (Chrome Layer)

**Why 4 persistent tokens?**
- UI chrome that works independently of surroundings
- Context-agnostic (inverts in dark mode for high contrast)
- Enables platform-specific adjustments without affecting content

**When to use each**:
- `default`: Nav bars, toolbars, persistent UI elements
- `hover`/`pressed`: Interactive state changes on persistent UI
- `active`: Selected/active state on persistent UI

**Key**: PERSISTENT inverts in dark mode
- Light mode: Dark colors (neutral/900-700, high contrast)
- Dark mode: Light colors (neutral/100-300, high contrast)
- Use for: Navigation bars, floating toolbars (context-agnostic)

**Decision Rule: "Can this element overlay anything and stay visible?"**
- YES → Use PERSISTENT (nav bar floats over video, image, content, dark page)
- NO → Use SURFACE (card depends on page background to be visible)

### CONTENT Category Hierarchy

**Text hierarchy by priority**:
1. `content/primary` - Main information (headlines, body)
2. `content/secondary` - Supporting info (metadata, captions)
3. `content/tertiary` - Supplementary (hints, small text)
4. `content/disabled` - Non-interactive (disabled fields)

**Special cases**:
- `content/brand` - Branded emphasis (logos, CTAs)
- `content/link` - Interactive links
- `content/link-hover` - Link interaction feedback
- `content/inverse` - Text on dark backgrounds

### STATUS Category Organization

**4 status types with subtle variants**:
- `status/success` & `status/success-subtle` - Positive outcomes
- `status/error` & `status/error-subtle` - Problems/failures
- `status/warning` & `status/warning-subtle` - Cautions
- `status/info` & `status/info-subtle` - Informational

**Usage pattern**:
- Main token: For text/icon color
- Subtle token: For background color (usually with opacity)

---

## Mode-Specific Behavior

### Light Mode (Default)

**Characteristics**:
- Light backgrounds (white/near-white)
- Dark text (black/near-black for contrast)
- Saturated colors
- Full-opacity primary tokens

**Token adjustments**:
- `surface/default` → `neutral/0` or `white`
- `content/primary` → `neutral/900`
- Status colors → Full saturation

### Dark Mode

**Characteristics**:
- Dark backgrounds (dark gray/black)
- Light text (light gray/white for contrast)
- Desaturated colors
- Adjusted opacity for some colors

**Token adjustments**:
- `surface/default` → `neutral/950`
- `content/primary` → `neutral/50` or `white`
- Status colors → Shifted hues and saturation
- Reduced opacity on some overlays

### Wireframe Mode (Optional)

**Characteristics**:
- Grayscale only
- Low contrast for quick scanning
- Focus on layout, not visual design
- All colors map to neutral scale

**Typical values**:
- Backgrounds → `neutral/100`, `neutral/200`
- Text → `neutral/800`, `neutral/900`
- Borders → `neutral/300`, `neutral/400`
- Interactive states → Slightly darker grays

---

## Common Mistakes & Solutions

### Mistake 1: Using Core Directly

❌ **Wrong**:
```
Fill: neutral/600
Stroke: blue/400
```

✅ **Right**:
```
Fill: surface/default (which aliases neutral/100 in light mode)
Stroke: border/default (which aliases neutral/300)
Text: content/primary (which aliases neutral/900)
```

**Why**: Core tokens don't adapt to mode changes

### Mistake 2: Skipping Semantics

❌ **Wrong**:
```
button/primary/background → blue/600 (Theme directly to Core)
```

✅ **Right**:
```
button/primary/background → interactive/primary → brand/primary → blue/600
(Theme → Semantics → Semantics → Core)
```

**Why**: Maintains semantic meaning and enables theming

### Mistake 3: Circular References

❌ **Wrong**:
```
button/background → button/hover/background (circular)
theme/button/text → theme/input/text (cross-component dependency)
```

✅ **Right**:
```
button/primary/background → interactive/primary → brand/primary
button/primary/hover → interactive/primary-hover → brand/primary-hover
(One-way hierarchy only)
```

**Why**: Prevents aliasing loops and circular updates

### Mistake 4: Hardcoding Values

❌ **Wrong**:
```
Fill: #3B82F6 (hardcoded hex)
Stroke: #FFFFFF (hardcoded hex)
```

✅ **Right**:
```
Fill: brand/primary (which uses blue/600 token)
Stroke: surface/overlay (which adapts to mode)
```

**Why**: Hardcoded values don't support dark mode or future changes

### Mistake 5: Over-Specification

❌ **Wrong** (too many tokens):
```
button/primary/background
button/primary/background-hover
button/primary/background-active
button/primary/background-focus
button/primary/background-disabled
(5 variants for one element)
```

✅ **Right** (leverage states):
```
button/primary/background (applies in all states)
Use interactive/primary-hover, interactive/primary-active, etc. for variants
(2-3 main tokens, states handled by component states)
```

**Why**: Reduces token count and complexity

---

## Performance Considerations

### Token Organization for Scale

**Current system**:
- 721 total tokens (manageable)
- 3-tier structure (fast lookup)
- Organized by category (logical grouping)

**As system grows**:
- Add sub-categories if count exceeds 100 per category
- Use naming prefixes for grouping (e.g., `surface/interactive/...`)
- Consider splitting into sub-collections if >1000 tokens

### Aliasing Performance

**Current aliasing depth**:
- Max 4 levels deep (Theme → Semantics → Semantics → Core)
- No circular references
- One-directional hierarchy

**Performance impact**:
- Minimal: Figma resolves aliases instantly
- Each token lookup is O(1) - constant time
- No performance penalty for aliasing depth

### Mode Switching Performance

**Light/Dark/Wireframe modes**:
- Instant switching (Figma native feature)
- No re-rendering lag observed
- All 721 tokens update immediately
- Tested and verified in production

---

## Maintenance Procedures

### Monthly Token Review

1. **Check for unused tokens**
   - Query Figma: which tokens have zero references
   - Deprecate if no longer needed
   - Document deprecation

2. **Monitor token coverage**
   - New components added?
   - Are they using existing tokens?
   - Missing semantic tokens?

3. **Update documentation**
   - Add new tokens to this reference
   - Deprecate old tokens
   - Update examples

### Quarterly System Audit

1. **Verify aliasing integrity**
   - Check for circular references
   - Verify all chains are 1-directional
   - Test in all modes

2. **Test mode switching**
   - Light mode baseline
   - Dark mode contrast checks
   - Wireframe mode legibility

3. **Semantic coverage analysis**
   - Calculate % of tokens using Semantics
   - Identify improvements
   - Plan optimizations

### When Adding New Tokens

1. **Justify the addition**
   - Used by 3+ components?
   - Fills semantic gap?
   - Can't reuse existing token?

2. **Choose correct tier**
   - Most tokens go to Semantics
   - Component-specific? → Theme
   - Never create at Core (reserved for primitives)

3. **Set up aliasing**
   - Theme → Semantics → Core (one direction)
   - Test in all modes
   - Verify visual parity

4. **Document thoroughly**
   - Add to this reference
   - Update component descriptions
   - Create examples
   - Link to Figma documentation

---

## Troubleshooting Advanced Scenarios

### Scenario 1: Color Looks Different in Light vs. Dark Mode

**Diagnosis**:
- Token is not mode-aware (hardcoded)
- Or token aliases are inconsistent

**Solution**:
1. Verify token uses Figma variables (not hex)
2. Check token has values in both modes
3. Verify aliases resolve in both modes
4. Test with component in both themes

### Scenario 2: Component Doesn't Update When Token Changes

**Diagnosis**:
- Component uses hardcoded value (not token)
- Token alias is broken
- Component is detached instance

**Solution**:
1. Check fills/strokes use tokens (not hex)
2. Verify token path is correct
3. Test token directly (toggle mode)
4. Re-attach component if needed

### Scenario 3: Aliasing Chain Broken

**Diagnosis**:
- Mid-chain token was deleted
- Token renamed without updating references
- Circular reference created

**Solution**:
1. Identify broken link in chain
2. Verify all tokens in chain exist
3. Check for circular references
4. Repair by updating aliases
5. Test in all modes

### Scenario 4: Conflicting Token Names

**Diagnosis**:
- Same token name in multiple collections
- Ambiguous token references
- Confusion in documentation

**Solution**:
1. Review naming conventions
2. Rename tokens for clarity
3. Update all references
4. Document change
5. Add migration guide

---

## Integration with Other Systems

### Design to Development Handoff

**For developers using tokens**:
- Token names are consistent (Core → Semantics → Theme)
- JSON exports available from Figma
- CSS/SCSS/Tailwind formats supported
- TypeScript types auto-generated

**Process**:
1. Export tokens from Figma
2. Generate code (CSS custom properties)
3. Verify in storybook
4. Integrate into codebase
5. Test in app (light/dark modes)

### Component Documentation

**Each component should document**:
- Which tokens it uses
- Tier used (Theme/Semantics)
- Why specific tokens chosen
- State variations and tokens
- Mode behavior

**Format**:
```
Component: Button Primary
Main tokens:
  - background: button/primary/background → interactive/primary
  - text: button/primary/text → content/primary
  - border: button/primary/border → border/default

States:
  - hover: button/primary/hover → interactive/primary-hover
  - active: button/primary/active → interactive/primary-active
  - disabled: button/primary/disabled → interactive/disabled
  - focus: button/primary/focus-ring → border/focus

Modes: Supports Light, Dark, Wireframe
```

---

## Version Changelog

### Version 2.0 (Feb 4, 2026)
- **Semantic Token Expansion**: +28 new semantic tokens
- **Theme Token Migration**: 321 tokens now alias through Semantics
- **Deprecated Token Consolidation**: 20 old tokens removed
- **Semantic Coverage**: 76% of Theme tokens now semantic
- **Architecture**: Full 3-tier hierarchy established
- **Breaking changes**: 0 (all migrations backward compatible)

### Version 1.0
- Initial 3-tier token architecture
- Core primitives (183 tokens)
- Theme layer (440 tokens)
- Basic semantic structure

---

## Contact & Support

For questions beyond this reference:
- Check main SKILL.md for quick answers
- Review Figma documentation frames
- Contact Design Systems Team
- Create GitHub issue for system improvements
