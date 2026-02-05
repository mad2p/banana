---
name: banana-foundation
description: Comprehensive reference for Banana Foundation design system token architecture, including 3-tier hierarchy (Core → Semantics → Theme), best practices, naming conventions, and migration guidance. Use this whenever working with design tokens, creating components, managing token migrations, or needing to understand which token tier to use in Figma designs.
---

# Banana Foundation - Token System Reference

Complete reference for the Banana Foundation 3-tier design token system. This skill provides instant access to token architecture, best practices, and decision frameworks for all token-related work.

## Quick Start

**The 3-Tier Hierarchy:**

```
TIER 1: CORE (Primitives)
├─ Raw colors, spacing, sizing
├─ Never reference directly in designs
└─ Used only by Semantics and Theme layers

TIER 2: SEMANTICS (Platform-Agnostic)
├─ Semantic abstraction of Core
├─ Use for text, backgrounds, status, icons, borders
├─ 8 categories with 65 tokens (added PERSISTENT)
└─ Routes through Core only

TIER 3: THEME (Component-Specific)
├─ Component-specific with state variations
├─ 40+ components covered
├─ 76% alias Semantics, 24% alias Core
└─ Apply to specific component implementations
```

**Decision Tree - Which tier to use:**

1. **Are you styling a generic UI element?** (text, background, status indicator)
   → Use **SEMANTICS**

2. **Are you styling a specific component?** (button, input, toast)
   → Use **THEME**

3. **Are you creating a new token?**
   → Create at **SEMANTICS** level, then alias from **THEME**

4. **Never use CORE directly** in designs

## Token Architecture

### TIER 1: CORE (Primitives) - 183 Variables

**Purpose**: Raw design primitives that form the foundation

**Collections**:
- **Colors**: neutral/*, blue/*, green/*, red/*, orange/*, gold/*, accent/*
- **Spacing**: space/0, space/4, space/8, ..., space/32 (4px increments)
- **Sizing**: size/0, size/8, size/16, ..., size/80 (8px increments)
- **Radius**: radius/none, radius/0x, radius/1x, radius/2x, radius/full

**Color Scale Logic**:
- Base scale: 100-800 (100-step increments)
  - Example: neutral/100, neutral/200, ..., neutral/800
- Opacity variants: X02, X03, X04 (e.g., accent/102 = 20% opacity)
- Extended shades: 850, 900, 950 (darker variants)

**When to use**: ONLY in token definitions, never directly in designs

---

### TIER 2: SEMANTICS (Platform-Agnostic) - 65 Variables

**Purpose**: Semantic abstraction that decouples from implementation

**8 Main Categories:**

#### SURFACE (6 tokens) - Content Layer
**Purpose**: Context-dependent backgrounds for content
- `surface/default` - Page backgrounds, card backgrounds
- `surface/raised` - Elevated surfaces (cards, panels)
- `surface/sunken` - Inset surfaces (wells, input fields)
- `surface/overlay` - Modals, dropdowns, popovers
- `surface/hover` - Interactive hover state on content surfaces
- `surface/pressed` - Interactive pressed state on content surfaces

**Key distinction**: SURFACE tokens follow the page background (light in light mode, dark in dark mode)

#### PERSISTENT (4 tokens) - Context-Agnostic Chrome Layer ✨ NEW
**Purpose**: UI chrome that works independently of surroundings
- `persistent/default` - Nav bars, toolbars (float over any background)
- `persistent/hover` - Interactive hover on context-agnostic UI
- `persistent/pressed` - Interactive pressed on context-agnostic UI
- `persistent/active` - Selected/active state on persistent UI

**Key distinction**: PERSISTENT tokens invert in dark mode (dark in light mode, light in dark mode) to maintain high contrast regardless of surroundings

#### STATUS (8 tokens)
- `status/info` - Information state
- `status/info-subtle` - Subtle info background
- `status/success` - Success state
- `status/success-subtle` - Subtle success background
- `status/warning` - Warning state
- `status/warning-subtle` - Subtle warning background
- `status/error` - Error state
- `status/error-subtle` - Subtle error background

#### CONTENT (8 tokens)
- `content/primary` - High contrast text (main body)
- `content/secondary` - Medium contrast text
- `content/tertiary` - Low contrast text (subtle)
- `content/disabled` - Disabled text
- `content/inverse` - Text on dark backgrounds
- `content/brand` - Brand-colored text
- `content/link` - Hyperlink text
- `content/link-hover` - Hyperlink hover state

#### ICON (5 tokens)
- `icon/primary` - Default icons
- `icon/secondary` - Subtle icons
- `icon/disabled` - Disabled icons
- `icon/inverse` - Icons on dark backgrounds
- `icon/brand` - Brand-colored icons

#### BRAND (4 tokens)
- `brand/primary` - Primary brand color
- `brand/primary-hover` - Brand hover state
- `brand/primary-active` - Brand active state
- `brand/accent` - Accent brand color

#### BORDER (5 tokens)
- `border/default` - Standard borders
- `border/strong` - Emphasized borders
- `border/subtle` - Subtle borders
- `border/interactive` - Interactive borders
- `border/focus` - Focus state borders

#### INTERACTIVE (4 tokens)
- `interactive/primary` - Primary interactions
- `interactive/primary-hover` - Hover state
- `interactive/primary-active` - Active state
- `interactive/disabled` - Disabled state

**When to use**:
- ✅ Text colors (content/*)
- ✅ Background colors (surface/* for content, persistent/* for chrome)
- ✅ Status indicators (status/*)
- ✅ Icons (icon/*)
- ✅ Borders (border/*)
- ✅ Generic interactive states (interactive/*)
- ✅ Navigation/toolbar backgrounds (persistent/*)

**Key principle**: Use Semantics as the primary layer for component styling

**Decision: SURFACE vs PERSISTENT**
- **SURFACE**: Context-dependent (cards, inputs, modals, sidebars, headers, footers)
  - Follow page background (light in light mode, dark in dark mode)
  - Use when element depends on parent context

- **PERSISTENT**: Context-agnostic (nav bars, floating toolbars)
  - Invert in dark mode (dark in light mode, light in dark mode)
  - Use when element works independently of surroundings
  - Rule: "Can this overlay anything and stay visible?"

---

### TIER 3: THEME (Component-Specific) - 440 Variables

**Purpose**: Component-specific tokens with full state coverage

**Aliasing Pattern**:
- **76% alias Semantics** (preferred) - Maintains semantic meaning
- **24% alias Core** (layout/sizing appropriate) - Maintains consistency

**40+ Components Covered:**

**Forms**:
- button/* - Button states, variants, sizing
- input/* - Input field states, focus, validation
- dropdown/* - Dropdown states, item styling
- checkbox/* - Checkbox states, sizes
- radio/* - Radio button states, sizes
- toggle/* - Toggle states, colors
- select/* - Select field styling
- textarea/* - Textarea styling

**Navigation**:
- nav/* - Navigation bar styling
- breadcrumbs/* - Breadcrumb colors and states
- pagination/* - Pagination controls
- tab/* - Tab states and colors

**Feedback**:
- toast/* - Toast notifications
- alert/* - Alert styling (success, warning, error, info)
- modal/* - Modal backdrop and content
- tooltip/* - Tooltip styling
- badge/* - Badge colors and states

**Data Display**:
- table/* - Table row, cell, header colors
- tag/* - Tag background and text colors
- progress-bar/* - Progress bar colors
- card/* - Card background, border, shadow

**AI-Specific**:
- ai/response/* - Response message styling
- ai/card/* - AI card styling
- ai/prompt/* - Prompt input styling

**When to use**:
- ✅ Apply to specific component instances
- ✅ Component-specific state handling
- ✅ Component part styling (button/primary/background)
- ❌ Don't bypass Semantics when appropriate

**Example Token Path**: `button/primary/background` → aliases → `interactive/primary` → aliases → `brand/primary` → aliases → `blue/600`

---

## Best Practices

### ✅ DO:
1. **Use Semantics for generic styling**
   - Text: Use `content/*`
   - Backgrounds: Use `surface/*`
   - Status: Use `status/*`
   - Icons: Use `icon/*`

2. **Use Theme for component-specific work**
   - Component states: button/primary, input/focused
   - Component parts: button/primary/background, button/primary/text
   - State variations: hover, active, disabled, focus

3. **Maintain the 3-tier hierarchy**
   - Theme → Semantics → Core (no shortcuts)
   - Each layer has a specific purpose
   - Route through Semantics when possible

4. **Document token usage**
   - Add descriptions in component properties
   - Explain why a token choice was made
   - Reference this guide in documentation

5. **Create new tokens strategically**
   - First check if a Semantics token exists
   - Create at Semantics level, not Theme
   - Use consistent naming conventions
   - Avoid single-use tokens

### ❌ DON'T:
1. **Reference Core directly in designs**
   - ❌ Don't use `neutral/600`
   - ✅ Do use `content/primary` (which aliases Core)

2. **Create circular token references**
   - Theme → Semantics → Theme ❌
   - Theme → Semantics → Core ✅

3. **Bypass Semantics inappropriately**
   - ❌ Use `theme/button/text` → `accent/600`
   - ✅ Use `theme/button/text` → `content/brand` → `accent/600`

4. **Use hardcoded colors in designs**
   - Always use tokens
   - Enables dark mode and theming
   - Maintains consistency

5. **Create tokens for one-off uses**
   - Reuse existing tokens
   - Only create new tokens if multiple components need it
   - Avoid token proliferation

---

## Modes & Theming

### Collections and Modes

**Semantics Collection**:
- Light mode (default)
- Dark mode

**Theme Collection**:
- Light mode (default)
- Dark mode
- Wireframe mode (prototyping/testing)

### How Modes Work

1. **Light mode**: Full-color system
2. **Dark mode**: Inverted colors, adjusted contrast
3. **Wireframe mode**: Simplified grayscale for rapid prototyping

**All tokens automatically adapt** to the currently selected mode

### Using Modes in Designs

1. Select a frame or component
2. Right-click → Set theme mode
3. All child elements respect the mode
4. Perfect for testing both themes simultaneously

---

## Token Migration & Deprecation

### Deprecated Token Mapping (Feb 2026)

These tokens were consolidated and removed. If you encounter them elsewhere, migrate using this mapping:

```
BACKGROUND → SURFACE
├─ background/primary → surface/default
├─ background/secondary → surface/raised
├─ background/tertiary → surface/sunken
├─ background/inverse → surface/inverse
└─ background/overlay → surface/overlay

TEXT → CONTENT
├─ text/primary → content/primary
├─ text/secondary → content/secondary
├─ text/tertiary → content/tertiary
├─ text/disabled → content/disabled
├─ text/inverse → content/inverse
├─ text/link → content/link
└─ text/link-hover → content/link-hover

FEEDBACK → STATUS
├─ feedback/success → status/success
├─ feedback/success-subtle → status/success-subtle
├─ feedback/warning → status/warning
├─ feedback/warning-subtle → status/warning-subtle
├─ feedback/error → status/error
├─ feedback/error-subtle → status/error-subtle
├─ feedback/info → status/info
└─ feedback/info-subtle → status/info-subtle
```

### Why Tokens Were Consolidated

- **Clearer naming**: Semantic categories are more intuitive
- **Reduced confusion**: Fewer similar token names
- **Better organization**: Logical token grouping
- **Easier maintenance**: Consolidated token management
- **76% semantic coverage**: More tokens route through semantics layer

### Impact Assessment

- **Internal**: Zero breaking changes (all migrations completed)
- **External**: Low risk - 1:1 migration mapping available
- **Consuming files**: May show warnings for deprecated tokens (easy fix)

---

## Common Usage Patterns

### Pattern 1: Basic Text Styling

```
Element: Body text
Tier to use: SEMANTICS
Token: content/secondary
Why: Generic secondary text needs semantic abstraction
```

### Pattern 2: Component Button

```
Element: Primary button (hover state)
Tier to use: THEME
Token: button/primary/background (hover)
Aliases: interactive/primary-hover → brand/primary-hover → blue/500
Why: Button-specific state requires Theme layer
```

### Pattern 3: Status Badge

```
Element: Error status badge
Tier to use: SEMANTICS
Token: status/error-subtle (background), status/error (text)
Why: Status is semantic concept, not component-specific
```

### Pattern 4: Form Input Focus

```
Element: Input field focused state
Tier to use: THEME
Token: input/focused/border
Aliases: border/focus → accent/600
Why: Component-specific state handling in Theme
```

### Pattern 5: Disabled State

```
Element: Disabled button
Tier to use: THEME + SEMANTICS
Background: theme/button/disabled/background → content/disabled
Text: theme/button/disabled/text → content/disabled
Why: Uses semantic content for text, theme for structure
```

---

## System Metrics

### Variables Inventory
- **Total**: 725 variables (updated with PERSISTENT)
- **Core**: 183 variables (primitives)
- **Semantics**: 65 variables (abstraction layer - added 4 PERSISTENT tokens)
- **Theme**: 440 variables (component-specific - updated to use PERSISTENT)
- **Typography**: 12 variables (fonts)
- **Layout**: 25 variables (spacing/sizing helpers)

### Semantic Coverage
- **Theme tokens aliasing Semantics**: 321 (76%)
- **Theme tokens aliasing Core**: 104 (24% - layout/sizing, appropriate)
- **Zero circular references**: Verified
- **Zero visual regressions**: Tested in both modes

### Architecture Health
- **Breaking changes**: 0
- **Visual regressions**: 0
- **Deprecated tokens**: 20 (all with 1:1 migration paths)
- **Production status**: ✅ Ready

---

## Decision Framework

### Step-by-Step: Choosing the Right Token

```
1. WHAT are you styling?
   ├─ Text/content? → SEMANTICS (content/*)
   ├─ Background? → SEMANTICS (surface/*)
   ├─ Status indicator? → SEMANTICS (status/*)
   ├─ Icon? → SEMANTICS (icon/*)
   ├─ Border? → SEMANTICS (border/*)
   └─ Component-specific? → THEME

2. IS there an existing token?
   ├─ Yes → Use it
   └─ No → Check Semantics first

3. CREATE new token?
   ├─ At Semantics level (more reusable)
   ├─ Reference from Theme
   └─ Verify 3+ components will use it

4. VERIFY aliasing chain
   ├─ Theme → Semantics → Core ✅
   └─ No shortcuts or circular refs
```

---

## Quick Reference Tables

### Text Color Decision Matrix

| Content Type | Token | Color | Use Case |
|---|---|---|---|
| Primary/Body text | `content/primary` | High contrast | Main content |
| Secondary text | `content/secondary` | Medium contrast | Metadata, labels |
| Subtle/Tertiary | `content/tertiary` | Low contrast | Disabled hints |
| Links | `content/link` | Brand color | Hyperlinks |
| Link hover | `content/link-hover` | Darker brand | Link interaction |
| Disabled | `content/disabled` | Gray | Disabled fields |
| Brand emphasis | `content/brand` | Brand color | Important emphasis |
| Inverse (dark bg) | `content/inverse` | Light color | Text on dark |

### Background Color Decision Matrix

| Surface Type | Token | Use Case |
|---|---|---|
| Default | `surface/default` | Main page background |
| Raised | `surface/raised` | Cards, panels, elevated |
| Sunken | `surface/sunken` | Input fields, wells |
| Overlay | `surface/overlay` | Modals, dropdowns, popovers |
| Hover | `surface/hover` | Interactive hover state |
| Pressed | `surface/pressed` | Interactive pressed state |
| Inverse | `surface/inverse` | Inverse contrast surfaces |

### Status Color Decision Matrix

| Status Type | Main Token | Subtle Token | Use Case |
|---|---|---|---|
| Success | `status/success` | `status/success-subtle` | Success messages, validated |
| Error | `status/error` | `status/error-subtle` | Error messages, validation |
| Warning | `status/warning` | `status/warning-subtle` | Warnings, cautions |
| Info | `status/info` | `status/info-subtle` | Informational messages |

---

## Troubleshooting

### Token Not Found
- Check token spelling (hyphens, lowercase)
- Verify you're in correct Figma file
- Check if token was deprecated (see migration mapping)
- Ask: Are you looking in right Collection? (Core/Semantics/Theme)

### Visual Mismatch Between Modes
- Ensure component uses tokens (not hardcoded colors)
- Verify mode is set correctly
- Check token has values in both modes
- Test in both Light and Dark mode

### Too Many Tokens in a Category
- Consider consolidating similar tokens
- Check if tokens are actually being used
- Review against deprecation mapping
- May indicate over-specification

### Component Not Respecting Mode
- Check if all colors use tokens (not fills/strokes)
- Verify tokens point to correct mode-aware values
- Ensure no hardcoded hex colors
- Test with fresh component instance

### Semantic vs. Theme Confusion
- Use decision framework (above)
- Ask: "Is this reused across 3+ components?" → Semantics
- Ask: "Is this specific to one component?" → Theme
- When in doubt, use Semantics first

---

## Advanced Topics

### Creating a New Token (Rare)

Only create new tokens if:
1. ✅ Used by 3+ components
2. ✅ Fills a clear semantic gap
3. ✅ No existing token covers the use case

**Process**:
1. Create at Semantics level (not Theme)
2. Add to appropriate category
3. Create alias in Theme (if component-specific)
4. Document with clear description
5. Test in both Light and Dark modes
6. Update this reference guide

### Custom Theme Variants

The Wireframe mode is available for prototyping. For custom themes:
1. Duplicate an existing mode (Light or Dark)
2. Update token values in the new mode
3. Name clearly (e.g., "High Contrast")
4. Test for sufficient contrast ratios
5. Document use case

### Token Dependencies and Relationships

All tokens follow this strict hierarchy:
```
Theme tokens → Semantics tokens → Core tokens
No shortcuts. No circular references. One direction only.
```

This ensures:
- Consistency across the system
- Easy maintenance and updates
- Clear token lineage
- Predictable cascading changes

---

## Resources

### Related Documentation
- **Design System Documentation**: See "📖 BANANA FOUNDATION - TOKEN SYSTEM DOCUMENTATION" frame in Figma
- **Changelog**: See "CHANGELOG - Semantic Token System Update" frame for migration details
- **Component Library**: Check 🍌 Component Library file for component-specific tokens

### File Locations
- **Main Design System**: 🍌 Foundation (Figma)
- **Component Library**: 🍌 Components (Figma)
- **Documentation**: Cover & Change log page, "📖 Documentation" section

### Getting Help
- Review this skill for quick answers
- Check Figma frame documentation for visual reference
- Refer to component descriptions in Component Library
- Contact Design Systems Team for complex questions

---

## Version History

| Date | Version | Changes |
|---|---|---|
| Feb 4, 2026 | 2.1 | PERSISTENT category added (4 tokens) for context-agnostic UI chrome, nav/toolbar tokens migrated to PERSISTENT, refined SURFACE category documentation |
| Feb 4, 2026 | 2.0 | Semantic token expansion (+28 tokens), Theme token migration (321 tokens), deprecated token consolidation (20 tokens removed), 76% semantic coverage achieved |
| Earlier | 1.0 | Initial token system architecture |

**Current Status**: ✅ Production Ready (Feb 4, 2026)

Last updated: February 4, 2026
