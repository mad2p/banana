---
name: banana-docs
description: Write design system documentation following Banana standards. Use when creating or updating component descriptions, design guidelines, or usage documentation. Produces concise, designer-friendly content with clear "When to use" and "When NOT to use" guidance.
---

# Banana Design System Documentation

This skill defines the documentation format and writing style for the Banana design system component descriptions. Use this when writing or updating Figma component descriptions to ensure consistency across the design system.

## Description Template

Every component description follows this structure:

```
{One-sentence purpose statement}

When to use:
• {Use case 1}
• {Use case 2}
• {Use case 3}

When NOT to use:
• {Anti-pattern 1 — suggest alternative}
• {Anti-pattern 2 — suggest alternative}
```

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

### "When to use" Section
- List 3 specific, scenario-based use cases
- Use concrete examples in parentheses when helpful
- Start each bullet with a noun or gerund (e.g., "FAQs or help content," "Submitting forms")

### "When NOT to use" Section
- List 2-3 common misuse patterns
- **Always suggest the correct alternative** in parentheses
- Help designers make better choices, not just avoid mistakes

## Quality Checklist

Before finalizing a component description, verify:

- [ ] Purpose is clear in the first sentence
- [ ] Use cases are specific and scenario-based
- [ ] Anti-patterns include component alternatives
- [ ] Total length is scannable (~400 characters)
- [ ] Language is designer-friendly (no dev jargon)
- [ ] Uses bullet character (•) not dashes or asterisks

## Example Descriptions

### Input Components

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

**Radio button**
```
Lets users choose exactly ONE option from a mutually exclusive list. Selecting one automatically deselects others.

When to use:
• Single selection from 2-5 options
• When all options should be visible
• Payment methods, shipping options

When NOT to use:
• Multiple selections allowed (use Checkbox)
• More than 7 options (use Select dropdown)
• Binary on/off (use Toggle)
```

### Action Components

**Button (Primary/Secondary/Tertiary)**
```
Triggers user-initiated actions. Choose hierarchy based on importance: Primary for main actions, Secondary for alternatives, Tertiary for low-emphasis options.

When to use:
• Submitting forms or confirming actions
• Navigating to new views
• Triggering dialogs or workflows

When NOT to use:
• Navigation without action (use Link)
• Toggling states (use Toggle or Switch)
• Multiple primary buttons in same context
```

**Toggle**
```
Binary on/off switch for settings that take effect immediately. No form submission required.

When to use:
• Feature toggles (notifications, dark mode)
• Settings with instant effect
• Preferences with clear on/off states

When NOT to use:
• Settings requiring form submission (use Checkbox)
• Multiple options (use Radio or Select)
• Actions (use Button)
```

### Feedback Components

**Alert**
```
Communicates important messages that require user attention—errors, warnings, confirmations, or system information.

When to use:
• Form validation errors requiring user action
• Success confirmations for important operations
• System warnings about potential issues

When NOT to use:
• Transient feedback (use Toast instead)
• Routine or minor information
• Messages that don't need acknowledgment
```

**Toast**
```
Brief, non-blocking notifications that appear temporarily to confirm actions or show status updates.

When to use:
• Confirming successful actions
• Non-critical error notifications
• Background task completion

When NOT to use:
• Critical errors (use Alert or Dialog)
• Information users need to reference later
• Messages requiring user action
```

### Display Components

**Badge**
```
Small visual indicators that show status, counts, or categories. Non-interactive—for display only.

When to use:
• Status labels (New, Beta, Pro)
• Notification counts
• Category indicators

When NOT to use:
• Interactive elements (use Button or Chip)
• Critical information requiring action
• Long text content
```

**Tooltip**
```
Brief contextual hints that appear on hover, providing extra information without cluttering the interface.

When to use:
• Icon-only button labels
• Abbreviation explanations
• Keyboard shortcut hints

When NOT to use:
• Essential information (users might not hover)
• Complex content (use Popover)
• Touch-only interfaces (no hover)
```

## Reference Materials

See `references/example-descriptions.md` for the complete set of 27 component descriptions used in the Banana design system.
