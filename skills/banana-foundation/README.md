# Banana Foundation Skill

This skill is installed at: `~/.claude/skills/banana-foundation/`

## What's Included

The banana-foundation skill includes comprehensive documentation for the Banana Foundation design system token architecture:

### Files

1. **SKILL.md** (Required)
   - Main skill definition with frontmatter
   - Complete 3-tier hierarchy reference
   - Token categories and usage guidelines
   - Best practices and decision frameworks
   - Modes & theming guidance
   - Migration mapping for deprecated tokens
   - Quick reference tables
   - Troubleshooting guide

2. **reference.md** (Advanced)
   - Deep-dive into token naming conventions
   - Aliasing patterns with examples
   - Component token inventory (45+ components)
   - Performance considerations
   - Maintenance procedures
   - Integration with other systems
   - Advanced troubleshooting scenarios

3. **examples.md** (Practical)
   - 10 real-world component examples
   - Button, input, toast, table, badge, card examples
   - Dark mode adaptation example
   - Component migration before/after
   - Quick reference by use case
   - Token decision tree

## How to Use

### Automatic Activation
The skill will automatically activate when you:
- Ask about design tokens
- Mention token architecture or naming
- Discuss Banana Foundation tokens
- Need guidance on which token tier to use

### Trigger Phrases
The skill responds to:
- "What token should I use for...?"
- "Which tier should this use?"
- "How do I migrate from...?"
- "Explain Semantics tokens"
- "What's the difference between Core and Theme?"
- "I need help with design tokens"

### Manual Access
To use the skill explicitly:
```
Use the banana-foundation skill to help with [your token question]
```

## Key Concepts

### 3-Tier Hierarchy
```
TIER 1: CORE (Primitives)
  └─ Raw colors, spacing, sizing
  └─ Never reference directly in designs

TIER 2: SEMANTICS (Platform-Agnostic)
  └─ Semantic abstraction layer
  └─ 7 categories: surface, status, content, icon, brand, border, interactive

TIER 3: THEME (Component-Specific)
  └─ Component-specific tokens
  └─ 40+ components covered
  └─ 76% alias Semantics, 24% alias Core
```

### Quick Decision Tree

**Styling generic text?** → Use `content/*` (Semantics)
**Styling a background?** → Use `surface/*` (Semantics)
**Showing status?** → Use `status/*` (Semantics)
**Component-specific styling?** → Use `theme/{component}/*` (Theme)
**Creating new token?** → Create in Semantics, reference from Theme
**Using Core directly?** → ❌ Never (use abstraction layers instead)

## System Metrics

- **Total Variables**: 721
- **Core**: 183 variables
- **Semantics**: 61 variables
- **Theme**: 440 variables
- **Semantic Coverage**: 76% of Theme tokens
- **Breaking Changes**: 0
- **Production Status**: ✅ Ready

## Recent Updates (Feb 4, 2026)

- ✅ Semantic Token Expansion: +28 tokens
- ✅ Theme Token Migration: 321 tokens → Semantics
- ✅ Token Consolidation: 20 deprecated tokens removed
- ✅ Architecture: Full 3-tier hierarchy established

## Common Tasks

### "I need to style a button"
See: examples.md → Example 1: Basic Button Component

### "What's the difference between CORE and THEME?"
See: SKILL.md → Token Architecture section

### "How do I handle dark mode?"
See: examples.md → Example 7: Dark Mode Adaptation

### "Which tokens were deprecated?"
See: SKILL.md → Token Migration & Deprecation section

### "I need the complete token inventory"
See: reference.md → Component Token Inventory

## Architecture

The skill covers:
- ✅ 3-tier token hierarchy (Core → Semantics → Theme)
- ✅ Token naming conventions
- ✅ Aliasing patterns and chains
- ✅ 44 semantic tokens across 7 categories
- ✅ 40+ component token patterns
- ✅ Light/Dark/Wireframe mode support
- ✅ Deprecated token migration mapping
- ✅ Best practices and anti-patterns
- ✅ Decision frameworks and trees
- ✅ Real-world component examples
- ✅ Performance considerations
- ✅ Troubleshooting guides

## Integration Points

This skill coordinates with:
- **Figma Design System**: 🍌 Foundation file
- **Component Library**: 🍌 Components file
- **Documentation**: Cover & Change log page in Figma
- **Design Team**: Token descriptions in component properties

## Support & Updates

- Last Updated: February 4, 2026
- Version: 2.0
- Status: Production Ready

For questions:
1. Check the SKILL.md main reference
2. See examples.md for practical cases
3. Review reference.md for deep dives
4. Contact Design Systems Team

## File Sizes

- SKILL.md: ~18 KB (main reference)
- reference.md: ~15 KB (advanced topics)
- examples.md: ~20 KB (practical examples)
- Total: ~53 KB of comprehensive token knowledge

---

Created: February 4, 2026
Maintained by: Design Systems Team
Status: ✅ Active & Production Ready
