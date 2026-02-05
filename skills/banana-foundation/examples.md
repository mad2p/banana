# Banana Foundation - Examples & Scenarios

Real-world examples showing correct token usage across different design scenarios.

## Example 1: Navigation Bar with PERSISTENT Tokens ✨ NEW

### Scenario
Navigation bar that needs to work on any background (light/dark content, images, etc.)

### Correct Token Usage

**Nav Bar (default state)**:
```
Background: theme/nav/background
            → aliases → persistent/default
            → aliases → neutral/900 (light mode - dark nav)
                      → neutral/100 (dark mode - light nav)

Text: content/inverse (text adapts to nav background)
      → aliases → neutral/0 (light mode)
                → neutral/900 (dark mode)

Hover State: theme/nav/hover
             → aliases → persistent/hover
             → aliases → neutral/800 (light mode)
                       → neutral/200 (dark mode)

Active Item: theme/nav/active
             → aliases → persistent/active
             → aliases → brand/primary (consistent across modes)
```

**Key Difference from SURFACE:**
- Nav bar is context-agnostic (works over any background)
- Uses PERSISTENT instead of SURFACE
- Inverts in dark mode (dark in light mode, light in dark mode)
- Text uses content/inverse to adapt to nav background

### Why PERSISTENT?

Nav bar needs to:
- Float over any content (video, image, light, dark)
- Maintain high contrast regardless of background
- Invert automatically in dark mode
- Work independently of page context

If we used SURFACE:
- ❌ Light mode page → light surface background
- ❌ Can't float over light page background (invisible)
- ❌ No contrast with page content

With PERSISTENT:
- ✅ Light mode → dark nav (contrasts with light page)
- ✅ Dark mode → light nav (contrasts with dark page)
- ✅ Floats over anything and stays visible

---

## Example 2: Toolbar Floating Over Content ✨ NEW

### Scenario
Floating toolbar that appears over a video or image background

### Correct Token Usage

**Toolbar (default)**:
```
Background: persistent/default
            → neutral/900 (light mode - always dark for contrast)
            → neutral/100 (dark mode - always light for contrast)

Button (toolbar action):
  Background: persistent/hover (on hover)
  Text: content/inverse
  Icon: icon/inverse

Divider: border/default (adapts to mode)
```

### Why This Works

The toolbar uses `persistent/default` which:
- Is always high-contrast (dark on light, light on dark)
- Doesn't care what's behind it (video, image, content)
- Automatically inverts when theme changes
- No hardcoded colors or mode-specific hacks

If we used SURFACE:
- Light mode: Light background (invisible on light page/image)
- Dark mode: Dark background (invisible on dark page/video)
- Doesn't work for floating elements

---

## Example 3: Basic Button Component

### Scenario
Creating a primary button with hover and disabled states.

### Correct Token Usage

**Primary Button (default state)**:
```
Background: theme/button/primary/background
            → aliases → interactive/primary
            → aliases → brand/primary
            → aliases → blue/600

Text: theme/button/primary/text
      → aliases → content/primary
      → aliases → neutral/900

Border: theme/button/primary/border
        → aliases → border/default
        → aliases → neutral/300
```

**Primary Button (hover state)**:
```
Background: theme/button/primary/hover
            → aliases → interactive/primary-hover
            → aliases → brand/primary-hover
            → aliases → blue/500

Text: content/primary (unchanged)

Border: border/default (unchanged)
```

**Primary Button (disabled state)**:
```
Background: theme/button/primary/disabled
            → aliases → interactive/disabled
            → aliases → neutral/200

Text: content/disabled
      → aliases → neutral/500

Border: border/default (unchanged, but lower opacity)
```

### Key Decisions

1. **Why Theme tier?** Button-specific tokens with multiple variants
2. **Why alias Semantics?** Maintains semantic meaning through the chain
3. **State management** Separate tokens for each state (hover, disabled)
4. **Text color** Uses semantic content token (reused everywhere)

### ❌ What NOT to do

```
❌ Background: #3B82F6 (hardcoded hex - won't support dark mode)
❌ Background: blue/600 (Core tier - not semantic)
❌ Background: button/background (skips semantic intermediate)
❌ All states same token (no state differentiation)
```

---

## Example 2: Form Input with Validation

### Scenario
Input field with default, focused, and error states.

### Correct Token Usage

**Input (default state)**:
```
Background: theme/input/default/background
            → aliases → surface/sunken
            → aliases → neutral/50

Border: theme/input/default/border
        → aliases → border/default
        → aliases → neutral/300

Text: content/primary
      → aliases → neutral/900

Placeholder: content/tertiary
             → aliases → neutral/500
```

**Input (focused state)**:
```
Background: theme/input/focused/background
            → aliases → surface/default
            → aliases → neutral/100

Border: theme/input/focused/border
        → aliases → border/interactive
        → aliases → blue/500

Focus Ring: theme/input/focused/ring
            → aliases → border/focus
            → aliases → accent/600

Text: content/primary (unchanged)
```

**Input (error state)**:
```
Background: theme/input/error/background
            → aliases → surface/sunken (same as default)
            → aliases → neutral/50

Border: theme/input/error/border
        → aliases → status/error
        → aliases → red/600

Error Text: status/error
            → aliases → red/700

Placeholder: content/tertiary (unchanged)
```

**Input (disabled state)**:
```
Background: theme/input/disabled/background
            → aliases → surface/default (slightly grayed)
            → aliases → neutral/100

Border: theme/input/disabled/border
        → aliases → border/default (lower opacity)
        → aliases → neutral/300

Text: content/disabled
      → aliases → neutral/400
```

### Key Decisions

1. **Why different backgrounds for each state?** Visual feedback is important
2. **Why surface/sunken for default?** Indicates input well/inset area
3. **Why status/error for validation?** Semantic meaning (status category)
4. **Why separate focus ring?** Supports accessibility (distinct focus indicator)

---

## Example 3: Toast Notification System

### Scenario
Dismissible toast notifications with 4 states: success, error, warning, info.

### Correct Token Usage

**Success Toast**:
```
Container Background: theme/toast/success/background
                      → aliases → status/success-subtle
                      → aliases → green/50

Container Border: theme/toast/success/border
                  → aliases → status/success
                  → aliases → green/600

Icon: theme/toast/success/icon
      → aliases → status/success
      → aliases → green/600

Text: content/primary
      → aliases → neutral/900

Close Button: theme/button/secondary/background (reuses button tokens)
```

**Error Toast**:
```
Container Background: theme/toast/error/background
                      → aliases → status/error-subtle
                      → aliases → red/50

Container Border: theme/toast/error/border
                  → aliases → status/error
                  → aliases → red/600

Icon: icon/primary with status/error override
      → aliases → red/600

Text: content/primary (unchanged)
```

**Warning Toast**:
```
Container Background: status/warning-subtle
                      → aliases → orange/50

Container Border: status/warning
                  → aliases → orange/600

Icon: status/warning
      → aliases → orange/600

Text: content/primary
```

**Info Toast**:
```
Container Background: status/info-subtle
                      → aliases → blue/50

Container Border: status/info
                  → aliases → blue/600

Icon: status/info
      → aliases → blue/600

Text: content/primary
```

### Key Decisions

1. **Why use status/* tokens?** Toasts communicate status (success/error/warning/info)
2. **Why subtle backgrounds?** Subtle variant provides low-contrast background
3. **Why reuse button tokens for close?** Buttons are buttons everywhere
4. **Why content/primary for text?** Text is text - use semantic text colors

---

## Example 4: Data Table Headers & Rows

### Scenario
Displaying data in a table with hover states and interactive rows.

### Correct Token Usage

**Table Header (default)**:
```
Background: theme/table/header/background
            → aliases → surface/raised
            → aliases → neutral/100

Text: content/secondary (slightly subtle for headers)
      → aliases → neutral/700

Border: border/default
        → aliases → neutral/300

Divider: border/subtle
         → aliases → neutral/200
```

**Table Row (default)**:
```
Background: surface/default
            → aliases → neutral/0

Text: content/primary
      → aliases → neutral/900

Border: border/subtle
        → aliases → neutral/200
```

**Table Row (hover)**:
```
Background: theme/table/row/hover
            → aliases → surface/hover
            → aliases → neutral/50

Text: content/primary (unchanged)

Border: border/subtle (unchanged)
```

**Table Row (selected)**:
```
Background: theme/table/row/selected
            → aliases → interactive/primary (subtle)
            → aliases → blue/100

Text: content/primary (unchanged)

Border: border/interactive
        → aliases → blue/500
```

**Table Row (striped - every other row)**:
```
Background: theme/table/row/stripe
            → aliases → surface/default with slight opacity
            → aliases → neutral/50

Text: content/primary (unchanged)

Border: border/subtle (unchanged)
```

### Key Decisions

1. **Why surface/raised for header?** Headers are elevated/distinguished
2. **Why surface/hover for row hover?** Semantic surface token for interaction
3. **Why separate stripe token?** Improves readability without being intrusive
4. **Why text doesn't change on hover?** Text remains readable regardless of background

---

## Example 5: Badge Component

### Scenario
Multi-purpose badges for status, tags, and labels.

### Correct Token Usage

**Badge - Success/Positive**:
```
Background: theme/badge/success/background
            → aliases → status/success-subtle
            → aliases → green/100

Text: theme/badge/success/text
      → aliases → status/success
      → aliases → green/700

Border: theme/badge/success/border
        → aliases → status/success
        → aliases → green/600
```

**Badge - Error/Negative**:
```
Background: status/error-subtle
            → aliases → red/100

Text: status/error
      → aliases → red/700

Border: status/error
        → aliases → red/600
```

**Badge - Warning**:
```
Background: status/warning-subtle
            → aliases → orange/100

Text: status/warning
      → aliases → orange/700

Border: status/warning
        → aliases → orange/600
```

**Badge - Neutral/Default**:
```
Background: surface/raised (or surface/default with opacity)
            → aliases → neutral/100

Text: content/secondary
      → aliases → neutral/700

Border: border/subtle
        → aliases → neutral/300
```

**Badge - Brand/Custom**:
```
Background: brand/primary (subtle opacity)
            → aliases → blue/100

Text: brand/primary
      → aliases → blue/700

Border: brand/primary
        → aliases → blue/600
```

### Key Decisions

1. **Why status tokens?** Badges communicate status
2. **Why subtle backgrounds?** Status-subtle for background keeps visual weight low
3. **Why matching border and text?** Creates visual cohesion
4. **Why separate brand variant?** For custom/highlighted badges

---

## Example 6: Card Component

### Scenario
Reusable card for displaying grouped content.

### Correct Token Usage

**Card (default)**:
```
Container Background: theme/card/background
                      → aliases → surface/raised
                      → aliases → neutral/0 (or white)

Border: theme/card/border
        → aliases → border/default
        → aliases → neutral/200

Shadow: Figma layer shadow (not token-driven)
        → Used for elevation

Text: content/primary (inside card)

Dividers: border/subtle
          → aliases → neutral/100
```

**Card (hover state)**:
```
Container Background: theme/card/hover
                      → aliases → surface/raised
                      → aliases → neutral/50 (subtle change)

Border: border/default (unchanged or slightly darkened)

Shadow: Elevated shadow (more pronounced)

Text: content/primary (unchanged)
```

**Card Header**:
```
Background: theme/card/header
            → aliases → surface/default
            → aliases → neutral/100

Text: content/secondary (header text is often secondary)
      → aliases → neutral/700

Border: border/subtle
        → aliases → neutral/200
```

**Card Footer**:
```
Background: theme/card/footer
            → aliases → surface/default
            → aliases → neutral/50

Text: content/tertiary (footer is subtle)
      → aliases → neutral/600

Border: border/subtle
        → aliases → neutral/100
```

### Key Decisions

1. **Why surface/raised for card?** Card is elevated from background
2. **Why darker background for header?** Visual distinction between sections
3. **Why lighter footer?** Deemphasizes secondary information
4. **Why layered surfaces?** Creates visual hierarchy

---

## Example 7: Dark Mode Adaptation

### Scenario
Same component switching from light to dark mode.

### Light Mode

```
Button Primary (light mode):
  Background: blue/600
  Text: neutral/0 (white/light)
  Border: blue/700 (darker blue)
```

### Dark Mode (Same Tokens!)

```
Button Primary (dark mode):
  Background: blue/500 (lighter blue for contrast on dark)
  Text: neutral/950 (darker/near-black for contrast on light bg)
  Border: blue/400 (lighter blue for visibility)
```

### How This Works

The tokens stay the same:
- `theme/button/primary/background`
- `theme/button/primary/text`
- `theme/button/primary/border`

But their VALUES change based on mode:

**Light Mode**:
- `blue/600` = `#2563EB`
- `neutral/0` = `#FFFFFF`
- `blue/700` = `#1D4ED8`

**Dark Mode** (mode variable):
- `blue/600` = `#3B82F6` (lighter for contrast)
- `neutral/0` = `#111111` (nearly black)
- `blue/700` = `#60A5FA` (lighter blue)

### Key Learning

1. **Same token reference** across modes
2. **Different values** per mode
3. **Designer responsibility** to set mode-appropriate values
4. **Developer benefit** - single token set works everywhere

---

## Example 8: Component Migration (Before → After)

### Scenario
Updating an old component to use new semantic tokens.

### ❌ BEFORE (Old System)

```
Button Component:
  Background: blue/600 (Core directly - no semantic meaning)
  Text: text/primary (deprecated category)
  Hover: blue/500 (hardcoded state)
  Disabled: gray/300 (inconsistent)
  Border: none (no border token)
```

**Problems**:
- Uses Core directly (no abstraction)
- Uses deprecated text/* category
- Inconsistent disabled treatment
- No focus state
- No dark mode support

### ✅ AFTER (New System)

```
Button Component:
  Background: theme/button/primary/background
              → interactive/primary
              → brand/primary
              → blue/600

  Text: theme/button/primary/text
        → content/primary
        → neutral/900 (light) / neutral/50 (dark)

  Hover: theme/button/primary/hover
         → interactive/primary-hover
         → brand/primary-hover
         → blue/500 (light) / blue/400 (dark)

  Active: theme/button/primary/active
          → interactive/primary-active
          → brand/primary-active
          → blue/700 (light) / blue/300 (dark)

  Disabled: theme/button/primary/disabled
            → interactive/disabled
            → neutral/300 (light) / neutral/600 (dark)

  Focus Ring: border/focus
              → accent/600 (light) / accent/400 (dark)
```

**Improvements**:
- ✅ Semantic abstraction (interactive/primary)
- ✅ Tier-based hierarchy (Theme → Semantics → Core)
- ✅ Mode-aware (works in light/dark)
- ✅ Consistent disabled treatment
- ✅ Accessible focus state
- ✅ All states covered

### Migration Path

1. **Map old tokens to new**:
   - `text/primary` → `content/primary`
   - `blue/600` → `brand/primary` → `blue/600`
   - `gray/300` → `interactive/disabled`

2. **Create Theme tokens** for component
   - `button/primary/background`
   - `button/primary/text`
   - `button/primary/hover`
   - etc.

3. **Update component** to use new tokens

4. **Test** in both light and dark modes

5. **Document** in component description

---

## Example 9: Link with Hover & Visited States

### Scenario
Hyperlink that indicates visited state.

### Correct Token Usage

**Link (default)**:
```
Text: content/link
      → aliases → blue/600

Underline: content/link (or border/interactive)
           → aliases → blue/600
```

**Link (hover)**:
```
Text: content/link-hover
      → aliases → blue/500

Underline: content/link-hover
           → aliases → blue/500

Background: surface/hover (optional subtle background)
            → aliases → neutral/100
```

**Link (visited)** ⚠️ (Use with caution):
```
Text: Need visited token? Create if necessary
      Suggestion: content/link-visited
                  → aliases → purple/600

Underline: Same as text color
```

### Key Decisions

1. **Why separate link tokens?** Links are semantic (not just text)
2. **Why different hover color?** Indicates interactivity
3. **Why visited is optional?** Can be controversial UX
4. **Why avoid hardcoded colors?** Supports theming

---

## Example 10: Modal / Dialog Component

### Scenario
Modal dialog with overlay, content, and action buttons.

### Correct Token Usage

**Overlay (backdrop)**:
```
Background: surface/overlay
            → aliases → neutral/900 with 60% opacity

Opacity: Adjust Semantics token to include opacity value
         or layer opacity adjustment
```

**Modal Content Background**:
```
Background: theme/modal/content/background
            → aliases → surface/default
            → aliases → neutral/0 (white in light mode)

Border: theme/modal/content/border
        → aliases → border/default
        → aliases → neutral/200

Shadow: Elevation shadow (not token-driven in Figma)
```

**Modal Header**:
```
Background: theme/modal/header/background
            → aliases → surface/raised
            → aliases → neutral/50

Text: content/primary
      → aliases → neutral/900

Border: border/subtle
        → aliases → neutral/200
```

**Modal Footer**:
```
Background: theme/modal/footer/background
            → aliases → surface/default
            → aliases → neutral/0

Border: border/subtle
        → aliases → neutral/100

Button: theme/button/primary (for primary action)
        theme/button/secondary (for secondary action)
```

**Close Button (X in corner)**:
```
Background: Transparent or surface/hover on hover

Icon: icon/primary or icon/secondary
      → aliases → neutral/700

Hover State: surface/hover
             → aliases → neutral/100
```

### Key Decisions

1. **Why surface/overlay for backdrop?** Semantic meaning (overlay concept)
2. **Why surface/raised for header?** Visual distinction from content
3. **Why shadow elevation?** Not token-driven (layer-based)
4. **Why reuse button tokens?** Buttons are buttons

---

## Quick Reference by Use Case

### "I need to style TEXT"
→ Use `content/*` tokens:
- `content/primary` - main text
- `content/secondary` - supporting
- `content/tertiary` - subtle
- `content/brand` - branded text
- `content/link` - links

### "I need to style a BACKGROUND"
→ Use `surface/*` tokens:
- `surface/default` - main background
- `surface/raised` - elevated areas
- `surface/sunken` - input areas
- `surface/overlay` - modals/dropdowns

### "I need to show STATUS"
→ Use `status/*` tokens:
- `status/success`, `status/success-subtle`
- `status/error`, `status/error-subtle`
- `status/warning`, `status/warning-subtle`
- `status/info`, `status/info-subtle`

### "I need to style BORDERS"
→ Use `border/*` tokens:
- `border/default` - standard borders
- `border/strong` - emphasized
- `border/subtle` - delicate
- `border/interactive` - interactive states
- `border/focus` - focus ring

### "I need to style ICONS"
→ Use `icon/*` tokens:
- `icon/primary` - main icons
- `icon/secondary` - supporting
- `icon/disabled` - disabled
- `icon/brand` - branded icons
- `icon/inverse` - on dark backgrounds

### "I need a COMPONENT TOKEN"
→ Use `theme/{component}/*`:
- `button/primary/background`
- `input/focused/border`
- `card/hover/background`
- `toast/success/background`
- etc.

---

## Testing Token Changes

### When You Update a Token Value

1. **Test in Light Mode**
   - Does color have sufficient contrast?
   - Visual hierarchy maintained?

2. **Test in Dark Mode**
   - Does color adapt correctly?
   - Sufficient contrast on dark backgrounds?

3. **Test All Components Using Token**
   - Search for token references
   - Check each component in both modes
   - Verify visual consistency

4. **Test Edge Cases**
   - Disabled states
   - Hover states
   - Focus states
   - Interaction feedback

5. **Document Changes**
   - Update changelog
   - Notify design team
   - Update component descriptions

---

## Token Decision Tree (Visual)

```
"I need a color token for X"
    ↓
"Is X a UI element property?"
    ├─ YES → "Is it component-specific?"
    │        ├─ NO (generic) → "Is it a persistent UI element?"
    │        │                 ├─ YES (nav/toolbar) → Use PERSISTENT
    │        │                 └─ NO → Use SEMANTICS (surface/*, content/*, status/*, icon/*, border/*)
    │        └─ YES → Use THEME (theme/{component}/...)
    └─ NO → Use CORE (only in token definitions)

"Is this persistent UI?" (Nav bar, toolbar, sidebar that floats independently)
    ├─ "Can it overlay anything and stay visible?"
    │  ├─ YES → Use PERSISTENT (persistent/default, persistent/hover, persistent/pressed, persistent/active)
    │  └─ NO → Use SURFACE (surface/default, surface/raised, surface/hover, surface/pressed)

"Should I create a new token?"
    ├─ "Used by 3+ components?"
    │  └─ YES → Create at SEMANTICS level (SURFACE or PERSISTENT)
    ├─ "Component-specific state?"
    │  └─ YES → Create at THEME level
    └─ NO → Reuse existing token
```

### SURFACE vs PERSISTENT Quick Ref

**Use SURFACE when:**
- ✅ Content layer (cards, inputs, modals)
- ✅ Depends on page/parent background
- ✅ Light in light mode, dark in dark mode
- ✅ Can't float independently

**Use PERSISTENT when:**
- ✅ Chrome layer (nav, toolbars)
- ✅ Works independently of background
- ✅ Dark in light mode, light in dark mode
- ✅ Always maintains high contrast

