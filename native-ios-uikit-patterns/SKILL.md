---
name: native-ios-uikit-patterns
description: design and review native ios interfaces using uikit and apple human interface guidelines. use when chatgpt needs to turn product requirements, wireframes, screenshots, or feature ideas into ios information architecture, screen hierarchy, uikit component breakdowns, auto layout plans, navigation structures, or implementation guidance for uiviewcontroller, uitableview, uicollectionview, uinavigationcontroller, uitabbarcontroller, and container controllers. default to traditional mvc and explicitly avoid swiftui unless the user clearly asks for it.
---

# Native iOS UIKit Patterns

Design native iOS experiences and interface patterns in UIKit. Default to traditional MVC, Apple Human Interface Guidelines, semantic system styling, and production-minded UIKit recommendations.

## Default behavior

- Output UIKit only unless the user explicitly asks for SwiftUI.
- Default to traditional MVC.
- Explain navigation only in terms of `UINavigationController`, `UITabBarController`, modal presentation, and custom container controllers.
- Prefer native iOS patterns over cross-platform abstractions.
- Treat screenshots, rough specs, PRDs, and feature descriptions as enough input to propose a UIKit structure.
- Keep recommendations practical: favor system components, semantic colors, Dynamic Type, and accessible interaction patterns.

## Deliverables to produce

When the user asks for a screen, flow, or review, structure the answer around these sections when relevant:

1. **Information architecture**
   - Define the main objects, sections, and user goals.
   - Clarify what belongs on the current screen versus what should move to a child screen, modal, or tab.

2. **Page hierarchy**
   - Describe the controller hierarchy and navigation flow.
   - Name the root controller, pushed detail controllers, presented modals, and embedded child controllers.

3. **UIKit component breakdown**
   - Recommend concrete UIKit building blocks such as `UILabel`, `UIButton`, `UIImageView`, `UITextField`, `UISearchBar`, `UIStackView`, `UITableView`, `UICollectionView`, `UISegmentedControl`, `UIPageControl`, and `UISheetPresentationController`.
   - Prefer `UITableView` for vertically stacked, list-like, settings-like, or form-like content.
   - Prefer `UICollectionView` for grids, dashboards, mixed sections, carousels, cards, and compositional layouts.

4. **Auto Layout plan**
   - Describe the layout tree from top to bottom.
   - Prefer `UIStackView` for simple vertical and horizontal grouping.
   - Prefer content/layout guides, safe areas, readable width, and content insets instead of hard-coded frames.
   - Call out compression resistance and hugging priorities only when they matter.

5. **Implementation guidance**
   - Recommend controller boundaries, view ownership, and reusable cells/views.
   - For MVC, keep data formatting and presentation logic close to the controller/view layer, but push pure networking/storage concerns out of the view controller.
   - Mention `UITableViewDiffableDataSource` or `UICollectionViewDiffableDataSource` when dynamic sections or frequent updates are involved.

6. **Accessibility, Dynamic Type, and Dark Mode**
   - Check for VoiceOver labels/hints, hit targets, semantic colors, contrast, scalable text, and safe adaptation to light/dark appearances.

## Decision rules

### Choose the right controller structure

- Use a single `UIViewController` with subviews for simple static pages.
- Use `UITableViewController` or a `UIViewController` hosting a table view for forms, settings, feed-like lists, and grouped vertical content.
- Use `UICollectionViewController` or a `UIViewController` hosting a collection view when layout flexibility matters.
- Use a child-controller composition approach for dashboards or screens with clearly separable modules.
- Use `UITabBarController` only for top-level destinations.
- Use `UINavigationController` for drill-down flows and title/action ownership.
- Use modal sheets for short-lived tasks, picking, creation flows, filters, and confirmations.

### Choose between table view and collection view

Use `UITableView` when:
- the layout is primarily one-dimensional
- rows have predictable reading order
- editing, swipe actions, grouped settings, or forms are central

Use `UICollectionView` when:
- the screen mixes grids, lists, banners, and horizontally scrolling groups
- section-specific layouts differ
- card-based design or dashboards are needed
- compositional layout improves clarity

### Layout guidance

- Start from safe area, then define header/content/footer regions.
- Prefer scrollable content for anything that can exceed smaller iPhone heights.
- Use `contentInsetAdjustmentBehavior` intentionally.
- Avoid nesting multiple vertical scroll views.
- Use self-sizing cells when text length is variable and Dynamic Type matters.
- Respect readable content width on iPad and large devices.

## Output style

- Be concrete and implementation-oriented.
- Name classes and responsibilities when useful, for example `HomeViewController`, `ProfileHeaderView`, `SettingsSection`, `PaymentMethodCell`.
- Show hierarchy in bullets or ASCII trees when that improves clarity.
- Include short UIKit code snippets only when they materially help.
- Do not output SwiftUI APIs, SwiftUI code, `NavigationStack`, `TabView`, or SwiftUI layout terminology unless the user explicitly requests SwiftUI.

## Review checklist

For critiques, audits, and redesigns, check the following:

- Is the information hierarchy obvious at first glance?
- Is navigation predictable and native to iOS?
- Are controls using standard UIKit affordances?
- Is the choice of table view vs collection view justified?
- Is the Auto Layout plan resilient for small phones, large phones, and iPad?
- Does text scale with Dynamic Type without truncating critical content?
- Do colors rely on semantic system colors or adaptive assets?
- Are touch targets, labels, traits, and reading order accessible?
- Are modals, sheets, and full-screen flows used appropriately?
- Are reusable cells/views/components clearly separated?

## Preferred implementation patterns

- Use semantic fonts via `UIFont.preferredFont(forTextStyle:)`.
- Use semantic colors such as `label`, `secondaryLabel`, `systemBackground`, `secondarySystemBackground`, and asset colors with light/dark variants.
- Use SF Symbols when a system icon fits.
- Use modern cell content/configuration APIs when appropriate.
- Use diffable data sources for frequently changing data.
- Use compositional layout for multi-section collection screens.
- Use `UISheetPresentationController` for modern bottom-sheet flows where appropriate.

## Avoid

- Defaulting to SwiftUI.
- Recommending custom controls when standard UIKit components already solve the problem.
- Hard-coded spacing, colors, or font sizes without a clear reason.
- Deep navigation stacks for tasks that should be modal.
- Overloaded screens with too many unrelated actions.
