# Banana Component Descriptions

Complete reference of all 27 component descriptions in the Banana design system.

---

## Layout Components

### Accordion
```
Organizes content into collapsible panels that users can expand/collapse to save space and reduce visual clutter.

When to use:
• FAQs or help content with multiple topics
• Settings panels with grouped options
• Long pages where content can be progressively disclosed

When NOT to use:
• Critical information that must always be visible
• Content with only 1-2 short sections
• Nested inside other collapsible elements
```

### Tab bar
```
Organizes related content into separate panels. Users switch views without leaving the page.

When to use:
• Page sections (Settings, Profile, History)
• Content that divides into logical categories
• Reducing scrolling by sectioning content

When NOT to use:
• Sequential processes (use Stepper)
• Only 1-2 sections
• Content that depends on other tabs
```

---

## Feedback Components

### Alert
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

### Toast
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

### Progress bar
```
Shows completion status of a process or task, helping users understand how much work remains.

When to use:
• File uploads/downloads
• Multi-step form progress
• Loading with known duration

When NOT to use:
• Unknown duration (use Spinner)
• Very short operations (<1 second)
```

### Trend marker
```
Shows directional change (up/down/neutral) in metrics using arrows and color coding.

When to use:
• Dashboard metrics vs. previous period
• KPI displays showing performance
• Financial gains/losses

When NOT to use:
• Values without comparison context
• Non-time-based comparisons
```

---

## Display Components

### Badge
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

### Tooltip
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

### Tooltip Body
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

---

## Action Components

### Primary Button
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

### Secondary Button
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

### Tertiary Button
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

### Icon-only Button
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

### Inline Button
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

---

## Selection Components

### Checkbox
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

### Checkbox group
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

### Radio button
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

### Radio group
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

### Toggle
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

### Segmented control
```
Compact toggle between 2-5 mutually exclusive options, displayed as connected buttons. Only one can be active.

When to use:
• View switching (List/Grid/Map)
• Content filtering by category
• Settings with immediate effect

When NOT to use:
• More than 5 options (use Tabs)
• Independent selections (use Checkbox)
• Primary navigation
```

### Slider
```
Lets users select a value or range by dragging a thumb along a track. Ideal for settings with immediate visual feedback.

When to use:
• Volume, brightness, zoom controls
• Price range filters
• Settings where relative position matters

When NOT to use:
• Precise numeric input needed
• Binary choices (use Toggle)
• Large ranges requiring precision
```

---

## Input Components

### Input
```
Form fields for collecting user data. Choose the appropriate type based on the expected input format and validation needs.

When to use:
• Collecting text, numbers, dates, or selections
• Search functionality
• User authentication

When NOT to use:
• Binary choices (use Toggle or Checkbox)
• Selection from few options (use Radio)
• Read-only display (use text)
```

### Input + Button
```
Combines a text input with an attached action button for immediate submission—like search with submit or newsletter signup.

When to use:
• Search with explicit submit
• Newsletter email signup
• URL or code entry with validation

When NOT to use:
• Standard form fields (use Input alone)
• When Enter key should submit
```

### Date
```
Form fields for collecting user data. Choose the appropriate type based on the expected input format and validation needs.

When to use:
• Collecting text, numbers, dates, or selections
• Search functionality
• User authentication

When NOT to use:
• Binary choices (use Toggle or Checkbox)
• Selection from few options (use Radio)
• Read-only display (use text)
```

### Password
```
Form fields for collecting user data. Choose the appropriate type based on the expected input format and validation needs.

When to use:
• Collecting text, numbers, dates, or selections
• Search functionality
• User authentication

When NOT to use:
• Binary choices (use Toggle or Checkbox)
• Selection from few options (use Radio)
• Read-only display (use text)
```

### Select
```
Form fields for collecting user data. Choose the appropriate type based on the expected input format and validation needs.

When to use:
• Collecting text, numbers, dates, or selections
• Search functionality
• User authentication

When NOT to use:
• Binary choices (use Toggle or Checkbox)
• Selection from few options (use Radio)
• Read-only display (use text)
```

### Text area
```
Form fields for collecting user data. Choose the appropriate type based on the expected input format and validation needs.

When to use:
• Collecting text, numbers, dates, or selections
• Search functionality
• User authentication

When NOT to use:
• Binary choices (use Toggle or Checkbox)
• Selection from few options (use Radio)
• Read-only display (use text)
```

### Search
```
Form fields for collecting user data. Choose the appropriate type based on the expected input format and validation needs.

When to use:
• Collecting text, numbers, dates, or selections
• Search functionality
• User authentication

When NOT to use:
• Binary choices (use Toggle or Checkbox)
• Selection from few options (use Radio)
• Read-only display (use text)
```

---

## Menu Components

### Menu item
```
Individual selectable options within dropdown menus, context menus, or action menus.

When to use:
• Action menus (edit, delete, share)
• Navigation dropdowns
• Filter and sort options

When NOT to use:
• Primary navigation (use Nav bar)
• Form selections (use Select)
• Binary choices (use Toggle)
```

---

## Tag Components

### Asset tag
```
Interactive labels for grouping, classifying, or filtering items. Can be removable or toggleable.

When to use:
• Content categorization
• Active filter indicators
• Multi-select input values

When NOT to use:
• Static status (use Badge)
• Primary actions (use Button)
• Navigation
```

### Filter tag
```
Interactive labels for grouping, classifying, or filtering items. Can be removable or toggleable.

When to use:
• Content categorization
• Active filter indicators
• Multi-select input values

When NOT to use:
• Static status (use Badge)
• Primary actions (use Button)
• Navigation
```

### Input tag
```
Interactive labels for grouping, classifying, or filtering items. Can be removable or toggleable.

When to use:
• Content categorization
• Active filter indicators
• Multi-select input values

When NOT to use:
• Static status (use Badge)
• Primary actions (use Button)
• Navigation
```
