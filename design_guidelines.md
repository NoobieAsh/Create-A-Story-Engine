# Creative Writing Analysis Engine - Design Guidelines

## Design Approach
**System Selected:** Linear + Notion hybrid approach
- **Rationale:** Utility-focused productivity tool requiring clean data visualization, strong typography for reading text entries, and an inspiring creative environment
- **Key Principles:** Clarity for analytics, breathing room for creative content, seamless content-first navigation

## Typography System

**Primary Font:** Inter (Google Fonts)
- Headers: 600-700 weight, tight tracking
- Body: 400-500 weight, comfortable line height (1.6-1.7)
- Code/Metadata: JetBrains Mono for timestamps, stats

**Hierarchy:**
- Page Titles: text-3xl to text-4xl, font-semibold
- Section Headers: text-xl to text-2xl, font-semibold
- Entry Titles: text-lg to text-xl, font-medium
- Body Text: text-base, comfortable reading width (max-w-3xl for long-form)
- Metadata/Labels: text-sm, font-medium, uppercase tracking-wide
- Stats/Numbers: text-2xl to text-5xl, font-bold for analytics

## Layout System

**Spacing Primitives:** Use Tailwind units of 2, 4, 6, 8, 12, 16
- Component padding: p-4, p-6, p-8
- Section gaps: gap-4, gap-6, gap-8
- Page margins: px-6 (mobile), px-8 to px-12 (desktop)

**Grid Structure:**
- Two-column split for main workspace: Sidebar (320px fixed) + Main content (flex-1)
- Entry grids: grid-cols-1 md:grid-cols-2 lg:grid-cols-3 for archive views
- Analytics: flex layouts for metric cards with gap-6

## Component Library

### Navigation & Layout
**Sidebar Navigation:**
- Fixed left sidebar with navigation sections
- Icon + label pattern throughout
- Active state: subtle background fill
- Collapsible sections for entry types, tags, characters

**Top Bar:**
- Search bar (prominent, max-w-md)
- Quick filters (entry type, date range)
- User profile/settings in top-right

### Content Components

**Entry Cards (Archive View):**
- Rounded corners (rounded-lg)
- Subtle border
- Structure: Entry type badge, title, excerpt (2-3 lines, line-clamp), metadata row (date, word count, detected mood)
- Hover: subtle elevation increase
- Click: Navigate to full entry

**Entry Editor:**
- Full-screen focused writing mode option
- Rich text toolbar: floating, context-aware
- Side panel for metadata (sentiment, motifs, characters)
- Auto-save indicator

**Analytics Cards:**
- Metric cards: Large number, label, trend indicator
- Chart containers: p-6, rounded-lg, adequate height (min-h-64)
- Grid layout: grid-cols-1 md:grid-cols-2 lg:grid-cols-3

**Character/Location Tracker:**
- List view with avatars (generated initials)
- Expandable details: occurrences list, relationship graph
- Add new: inline form

**Prompt Generator:**
- Card-based prompt display
- Refresh button, save to favorites
- Parameters: adjustable sliders/toggles (complexity, genre, theme)

### Forms & Inputs

**Text Inputs:**
- Border-based style (not filled)
- Focus: border emphasis (border-2)
- Labels: text-sm, font-medium, mb-2
- Helper text: text-xs below input

**Rich Text Editor:**
- Clean toolbar with icon buttons
- Formatting: bold, italic, headings, lists
- Minimal visual chrome - content-first
- Character count in bottom-right

**Filters & Search:**
- Multi-select chips for tags, types
- Date range picker: minimal calendar
- Clear all button

### Data Visualization

**Sentiment/Mood Display:**
- Horizontal bar indicator with label
- Emoji or icon representation
- Percentage or intensity scale (0-100)

**Motif Detection:**
- Tag cloud or list with frequency counts
- Click to filter entries by motif
- Visual weight based on occurrence

**Timeline/Trends:**
- Line charts for mood over time
- Bar charts for writing frequency
- Consistent axis labels, gridlines

**Relationship Graph (Characters):**
- Node-link diagram
- Interactive: hover for details, drag to rearrange
- Connection strength indicated by line weight

### Interactive Elements

**Buttons:**
- Primary: font-medium, px-4, py-2, rounded-md
- Secondary: border variant
- Icon buttons: p-2, rounded-md
- Floating action button for new entry (bottom-right)

**Modal Dialogs:**
- Centered overlay (max-w-2xl for content)
- Close button (top-right)
- Actions in footer (right-aligned)

**Tabs:**
- Underline style for entry type switching
- Active: border-b-2, font-semibold

## Accessibility

- Consistent focus rings across all interactive elements
- Semantic HTML throughout (nav, main, article, aside)
- ARIA labels for icon-only buttons
- Keyboard navigation: tab order, shortcuts for common actions
- Text contrast ratios meet WCAG AA
- Form validation: inline error messages

## Images

**No hero images** - This is a utility application, not marketing

**Avatar placeholders:**
- Character tracker: Colored circles with initials
- Generated based on first letter, consistent colors

**Empty states:**
- Illustrative icons (Heroicons) with helpful messaging
- "No entries yet" states with create prompts

**Icon Library:** Heroicons (outline style primary, solid for active states)

## Animations

**Minimal, purposeful motion:**
- List item stagger on load: 50ms delay between items
- Modal: fade in (150ms)
- Toast notifications: slide in from top
- No scroll-triggered animations
- No page transitions

## Responsive Behavior

**Mobile (< 768px):**
- Sidebar: Off-canvas drawer (hamburger toggle)
- Entry grid: Single column
- Analytics: Stack vertically
- Rich editor: Simplified toolbar

**Tablet (768px - 1024px):**
- Sidebar: Collapsible to icon-only
- Entry grid: 2 columns
- Analytics: 2 columns

**Desktop (> 1024px):**
- Full sidebar visible
- Entry grid: 3 columns
- Analytics: 3 columns
- Optional split-screen for writing + analytics