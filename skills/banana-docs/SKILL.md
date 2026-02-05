---
name: banana-docs
description: Write design system documentation following Banana standards. Use when creating or updating component descriptions, design guidelines, or usage documentation. Produces comprehensive, deduplication-aware content with distinct "When to Use," "Do's/Don'ts," and implementation guidance.
---

# Banana Design System Documentation

This skill defines the documentation format and writing style for the Banana design system component descriptions. Use this when writing or updating component documentation to ensure consistency across the design system.

## Documentation Structure

Component documentation follows a comprehensive structure with four distinct sections. Each section serves a specific purpose and avoids duplication:

### 1. Figma Component Description (Short Form)
Used in Figma component panel (~400 characters):

```
{One-sentence purpose statement}

When to use:
• {Scenario 1}
• {Scenario 2}

When NOT to use:
• {Anti-pattern 1 — suggest alternative}
```

### 2. Full Documentation (Extended Form)
Used in markdown documentation files with complete deduplication:

```
## Usage Guidelines

### When to Use
• {Context/scenario 1}
• {Use case description 2}
• {Problem the component solves 3}

### When Not to Use
• {Situation to avoid 1}
• {Alternative component needed 2}

### Do's
• {Implementation guideline 1}
• {Quality standard/best practice 2}

### Don'ts
• {Common mistake to avoid 1}
• {Execution error to prevent 2}
```

## Deduplication Principle

The key to clear component documentation is maintaining distinct purposes for each section. **Never duplicate the same guidance in multiple sections.**

### Section Purposes

**"When to Use / When Not to Use"** = **WHEN (Context/Scenarios)**
- Describes situations and contexts where the component fits
- Focuses on use cases and problems the component solves
- Includes alternative components for different scenarios
- Answers: "In what situations should I use this component?"

**"Do's / Don'ts"** = **HOW (Implementation/Execution)**
- Describes how to implement the component correctly
- Focuses on configuration, design, and quality standards
- Includes accessibility, interaction patterns, and best practices
- Answers: "How should I configure/design with this component?"

### Deduplication Rules

1. **Remove scenario duplicates**: If "When to Use" describes "For FAQs", don't repeat it in Do's
2. **Keep implementation in Do's only**: Don't mention "clear labels" in "When to Use"
3. **Situational context stays in When**: Component alternatives and situations belong here
4. **Execution details go in Do's**: How to configure, design, and implement

## Writing Style Guidelines

### Voice & Tone
- **Designer-focused**: Write for Product Designers, not developers. Avoid technical jargon like "props," "state management," or "event handlers."
- **Active voice**: "Triggers user-initiated actions" not "Can be used to trigger actions"
- **Prescriptive**: "Use for..." not "Can be used for..."
- **Concise**: Target ~400 characters total for quick scanning in Figma's component panel

### Purpose Statement
- One sentence that explains what the component does
- Focus on the user outcome, not implementation
- Include the key differentiator if relevant (e.g., "Non-interactive—for display only")

### "When to Use" Section (Scenarios)
- List specific, scenario-based use cases and contexts
- Use concrete examples in parentheses when helpful
- Start each bullet with a noun or gerund (e.g., "FAQs or help content," "Submitting forms")
- Focus on WHEN and WHERE, not HOW

### "When Not to Use" Section (Scenarios)
- List 2-3 common misuse patterns or inappropriate contexts
- **Always suggest the correct alternative** in parentheses
- Help designers make better choices by showing what component fits better
- Focus on scenarios to AVOID, not implementation mistakes

### "Do's" Section (Implementation)
- List best practices for implementing the component correctly
- Include quality standards, accessibility requirements, and interaction patterns
- Focus on HOW to use the component properly
- Include specifics: labeling conventions, sizing, positioning, interaction behavior

### "Don'ts" Section (Implementation)
- List common implementation mistakes and anti-patterns
- Focus on EXECUTION errors, not use case mistakes
- Describe what not to do in implementation, not when to avoid the component

## Quality Checklist

### For Figma Component Panel Descriptions

Before finalizing a component description in Figma, verify:

- [ ] Purpose is clear in the first sentence
- [ ] Use cases are specific and scenario-based (not implementation details)
- [ ] Anti-patterns include component alternatives
- [ ] Total length is scannable (~400 characters)
- [ ] Language is designer-friendly (no dev jargon)
- [ ] Uses bullet character (•) not dashes or asterisks

### For Full Markdown Documentation

Before finalizing a component's markdown documentation, verify deduplication:

**"When to Use" Section**
- [ ] Describes scenarios and contexts (WHEN)
- [ ] Does not mention implementation details (move to Do's if present)
- [ ] Provides concrete use case examples
- [ ] Lists when NOT to use with alternatives

**"Do's / Don'ts" Section**
- [ ] Describes implementation best practices (HOW)
- [ ] Does not duplicate scenario descriptions (remove if present)
- [ ] Focuses on quality standards, accessibility, interaction patterns
- [ ] Provides specific, actionable guidance

**Overall Documentation**
- [ ] No concept appears in both "When" and "Do's" sections
- [ ] Scenarios in "When to Use/Not to Use" only
- [ ] Implementation details in "Do's/Don'ts" only
- [ ] Each section is independently useful and complete

## Example Descriptions

### Figma Component Panel (Short Form)

These examples show the concise descriptions used in Figma's component panel (~400 characters).

**Checkbox**
```
Allows selection of one or more independent options from a list. Each choice is independent—selecting one doesn't affect others.

When to use:
• Multiple selections from a list
• Binary yes/no choices
• Terms acceptance or opt-in settings

When NOT to use:
• Mutually exclusive options (use Radio)
• Immediate on/off actions (use Toggle)
• Very long lists (use multi-select dropdown)
```

**Accordion**
```
Hides optional or secondary content in collapsible panels, keeping pages scannable and space-efficient.

When to use:
• FAQs where users scan for topics
• Settings panels with many categories
• Hiding secondary content to save space

When NOT to use:
• Critical information that must be visible
• Primary navigation (use Tabs)
• Content too short to justify hiding
```

### Extended Markdown Documentation (Full Form)

These examples show how deduplication works in full documentation files. Note how "When to Use" focuses on scenarios and "Do's" focuses on implementation—no overlap.

**Accordion (Full Documentation Example)**
```markdown
## Usage Guidelines

### When to Use
- For FAQs or help content where users scan for specific topics
- In settings or preference panels with multiple categories
- To hide optional or secondary information while keeping primary content visible
- When screen space is limited and content needs progressive disclosure
- For hierarchical content that can be organized into logical sections

### When Not to Use
- When information is critical and must always be visible
- For primary navigation or key actions
- When content is short enough to display without hiding
- For deeply nested or complex hierarchies (limit to 1-2 levels)
- When most users would need all sections expanded at once

### Do's
- Provide clear, descriptive labels that indicate panel content
- Use consistent hierarchy for section titles across all panels
- Limit the number of panels to avoid overwhelming users (typically 5-10)
- Allow only one panel to be expanded at a time when appropriate
- Ensure panel headers are keyboard accessible
- Pre-select an important or logical panel when helpful

### Don'ts
- Don't nest accordions inside other collapsible elements (max 1 level deep)
- Don't truncate labels; they must clearly describe hidden content
- Don't use accordions without proper ARIA labels and states
- Don't auto-expand all panels on page load
- Don't hide critical information behind accordion panels
```

**Key Deduplication Points:**
- "When to Use" = Scenarios (FAQs, settings, space). Never appears in Do's.
- "Do's" = Implementation (labels, hierarchy, keyboard). Never appears in When to Use.
- No duplication of "hide optional content" in both sections.
- No repetition of "limit panels" appearing twice.

**Badge (Full Documentation Example)**
```markdown
## Usage Guidelines

### When to Use
- To highlight statuses, versions, or tiers (e.g., "New", "Beta", "Pro")
- To display counts or notifications (e.g., unread message numbers)
- To categorize or label items (e.g., "Featured", "Sale", "Limited Edition")
- As supplementary information paired with another element
- For quick-scan categorization where text alone isn't sufficient

### When Not to Use
- For critical error messages or warnings (use Alert instead)
- For interactive elements or actions (badges are display-only)
- For information that requires explanation or context
- For lengthy content that needs user attention
- As standalone indicators without associated context

### Do's
- Keep badge text short (1-2 words or 3 digits maximum)
- Position badges consistently relative to their associated element
- Use semantic colors appropriately (green for success, red for errors)
- Use singular labels that clearly indicate meaning
- Pair with icons when helpful for visual recognition

### Don'ts
- Don't use badges as interactive elements
- Don't add multiple badges to a single element (too distracting)
- Don't truncate or wrap badge text; redesign if it doesn't fit
- Don't use for information requiring explanation or user action
- Don't rely solely on color to convey meaning
```

**Key Deduplication Points:**
- "When to Use" describes use cases (status, counts, categories).
- "Do's" describes implementation (length, positioning, colors).
- "When NOT to Use" suggests alternatives (Alert, interactive elements).
- "Don'ts" describes implementation errors (truncation, color-only).
- No scenario description appears in Do's/Don'ts.

## Reference Materials

### Published Banana Component Documentation

All 17 Banana component documentation files now follow the deduplication standards:

1. **Accordion** - Collapsible content organization
2. **Alert** - Important persistent messages
3. **Badge** - Display-only status indicators
4. **Buttons** - Primary actions and navigation
5. **Checkbox** - Multi-select form inputs
6. **Dropdown/Menu Items** - Action menus and navigation
7. **Input, Select, Autocomplete** - Form input components
8. **Progress Bar** - Operation completion tracking
9. **Radio Button** - Single-selection form inputs
10. **Segmented Control** - View/filter switching
11. **Slider** - Continuous value adjustment
12. **Tabs** - Content section organization
13. **Tags** - Categorization and filtering labels
14. **Toast** - Transient feedback notifications
15. **Toggle** - Binary on/off settings
16. **Tooltip** - Contextual hover hints
17. **Trend Marker** - Metric change indicators

Each file contains separate, deduplication-aware "When to Use," "Do's," and "Don'ts" sections following this skill's guidelines.

### Key Resources

- **Plan Document**: `/Users/peter.posa/Documents/dev-generic/` - Original deduplication plan and rationale
- **Updated Documentation**: All component files in `/Users/peter.posa/Documents/dev-generic/banana-library-docs/`
- **Skill Location**: `/Users/peter.posa/.claude/skills/banana-docs/SKILL.md`

See `references/example-descriptions.md` for additional component description examples and patterns.
