# UIKit patterns reference

Consult this file when the task needs more detailed UIKit implementation guidance than the main skill instructions provide.

## Common screen archetypes

### Settings or preferences
- Use `UITableView` with grouped sections.
- Use standard cells, switches, disclosure indicators, and footer text.
- Push deeper configuration onto child controllers instead of overloading one page.

### Feed or inbox
- Use `UITableView` for a straightforward vertically ordered feed.
- Use `UICollectionView` only if cards, mixed sections, or horizontal carousels are essential.
- Keep primary actions visible but avoid too many row-level affordances.

### Dashboard or home hub
- Prefer `UICollectionView` with compositional layout.
- Break content into sections like summary, shortcuts, recent activity, and recommendations.
- Use supplementary headers when section identity matters.

### Form or creation flow
- Use table-based forms for long vertical input.
- Group related fields into sections.
- Keep validation, helper text, and keyboard handling explicit.
- Present short auxiliary pickers or filters in a sheet when suitable.

### Detail screen
- Use a `UIViewController` with a scroll view for static or mixed content.
- Use child views or stack views for modular sections.
- Use a table or collection view if the detail page is mostly repeated rows/items.

## Navigation guidance

### Tab-based apps
- Reserve tabs for top-level destinations only.
- Keep tab count focused.
- Each tab should generally own its own navigation controller.

### Push navigation
- Use for hierarchical drill-down.
- Keep the back path intuitive.
- Place screen-specific actions in the navigation bar only when truly global to that screen.

### Modal presentation
- Use sheets for temporary tasks, editing, filtering, picking, or confirmation flows.
- Use full-screen presentation when the task is immersive or forms a distinct workflow.
- Dismissal should always feel obvious and safe.

## Auto Layout reminders

- Pin to safe area, not the superview edges, for primary page structure.
- Prefer layout margins and readable content guides to arbitrary constants.
- Use stack views for simple composition but not as a substitute for proper screen architecture.
- Make scrolling containers own the scrolling experience; avoid nested vertical scrolling when possible.
- Use self-sizing cells and estimated sizes when text/content length varies.

## Accessibility reminders

- Every interactive element needs a clear accessible label.
- Preserve logical reading order.
- Ensure controls remain usable at larger text sizes.
- Avoid using color alone to communicate state.
- Keep tap targets comfortably large.

## Dark mode reminders

- Prefer semantic colors first.
- For branded colors, provide adaptive assets.
- Review separators, overlays, and elevated surfaces carefully in dark mode.
