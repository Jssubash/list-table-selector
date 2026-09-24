# List or Table Selector

Pick one or more objects as a **Dropdown**, an **inline List**, or a **Table**, all from one widget
and one configuration.

| | |
|---|---|
| **Version** | 1.0.0 |
| **Minimum Mendix version** | 9.24.0 |
| **Platform** | Web (classic client and React client) |
| **Category** | Input Elements |
| **Author** | Subash (MxTechies) |

---

## Description

List or Table Selector is a single pluggable input widget for Mendix with three interchangeable views: Dropdown, inline List, and Data Table. All three views share the same data source configuration, selection logic, search behaviour, and events, allowing developers to switch between them with a single property change while keeping every other setting intact.

It binds directly to a **Reference** (single select) or **Reference Set** (multi select) association, or to an **Enumeration** or **Boolean** attribute.

## Why use it

- **One widget, three views:** Change the visual presentation without reconfiguring the data source, associations, or events.
- **Replaces multiple built-in widgets:** Replaces the Reference Selector, Reference Set Selector, Input Reference Set Selector (Check boxes), Radio buttons, and Data Grid used for selection.
- **No helper entities required for multi-selection:** It reads and writes the reference set directly. A checkbox list needs no non-persistent helper entity, no boolean attribute, and no population/commit microflows.
- **Universal search built in:** Search operates on the actual caption values displayed to the user. In the Table view, it searches across all searchable columns simultaneously.
- **Rich custom content:** Options can host arbitrary Mendix widgets (cards, avatars, badges, images) instead of plain text captions.
- **Rich Table view with built-in selection:** Purpose-built for selection with sortable, filterable, resizable, reorderable, and hidable columns, container-click selection, and pagination/virtual scrolling.

## Views at a glance

| View | Best for | Highlights |
|------|----------|------------|
| **Dropdown** | Compact forms | Type-to-filter, clear button, multi-select shown as text or removable labels, Select All, optional footer |
| **List** | Always-visible options | Check boxes or radio buttons, vertical or multi-column CSS grid layout, search box, scroll cap |
| **Table** | Multi-attribute selection | Configurable columns, sorting, per-column filters, column resizing, column reordering, column visibility toggle, paging buttons or virtual scrolling, row click highlight |

## Features

- Single selection (Reference) and multi selection (Reference Set) in every view
- Enumeration and Boolean attribute support (Dropdown and List views)
- Universal search modes: Contains (ranked by relevance), Starts-with, or None
- Select All / Deselect All, including a three-state header checkbox in the Table view
- Custom content drop zones in options (or option list only), and per table column
- Dynamic styling: Conditional row class, dynamic cell class, and per-column tooltip expressions
- Events: **On change**, **On enter**, and **On leave** actions
- Full WCAG accessibility compliance: ARIA combobox/listbox/radiogroup/grid roles, keyboard navigation, screen reader announcements, and native form controls
- Translatable labels with English (en_US) and Dutch (nl_NL) built in
- Offline capable: Works in offline Mendix applications
- Rich Studio Pro integration: Structure mode previews, context-sensitive property visibility, and design-time validation

## Limitations

- The **Table** view requires an **Association** data source (reads columns from selectable objects). It does not support Enumeration or Boolean attributes.
- Web only. Native mobile is not supported.

## Installation

1. Download the widget from the Mendix Marketplace into your app.
2. In Studio Pro, choose **App > Synchronize App Directory**.
3. Find **List or Table Selector** under **Input Elements** in the toolbox.

## Quick start

1. Place the widget inside a data view.
2. **General tab:** set **Type**.
   - *Association:* choose the association, the **Selectable objects** source (database, microflow, or nanoflow), and a caption (Attribute or Expression).
   - *Enumeration / Boolean:* choose the attribute.
3. Set **Filter type** and **Clearable**, and configure **Custom content** if desired.
4. **View tab:** pick **Dropdown**, **List view**, or **Table**, then configure the settings for that view. For Table view, add columns.
5. **Events tab:** add an **On change** action if needed.
6. **Accessibility tab:** review and translate ARIA labels and status messages.

## Dependencies

None. The widget is self-contained and does not require additional modules or external CSS.

## Support

Report issues or ask questions through GitHub or contact MxTechies.
