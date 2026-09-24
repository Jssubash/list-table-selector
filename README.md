# List or Table Selector

A comprehensive, pluggable Mendix web widget providing three interchangeable views — **Dropdown**, **Inline List**, and **Data Table** — for selecting one or more objects, all sharing a single data source configuration, search behavior, and event setup.

Switch between a dropdown, an inline checkbox/radio list, or a full-featured data table by changing a single property on the View tab, without reconfiguring entities, data sources, or actions.

[![Mendix Version](https://img.shields.io/badge/Mendix-9.24.0+-blue.svg)](https://marketplace.mendix.com/)
[![Platform](https://img.shields.io/badge/Platform-Web%20%7C%20Offline%20Capable-orange.svg)]()

---

## Widget Package (.mpk)

The pre-compiled, ready-to-use Mendix widget package is included directly in this repository:

📦 **[com.mxtechies.widget.web.ListTableSelector.mpk](com.mxtechies.widget.web.ListTableSelector.mpk)**

### Quick Installation:
1. Download or copy `com.mxtechies.widget.web.ListTableSelector.mpk` into your Mendix project's `widgets/` folder.
2. In Mendix Studio Pro, click **App > Synchronize App Directory** (or press `F4`).
3. Find **List or Table Selector** under the **Input Elements** section in your page editor toolbox.

---

## 1. Overview

The **List or Table Selector** is a pluggable web widget designed for Mendix (supporting both the classic web client and the modern React client). It unifies multiple object selection patterns into a single configurable widget.

### Supported Data Sources
- **Association:** Reference (single selection) or Reference Set (multi selection)
- **Enumeration:** Direct binding with localized captions (Dropdown and List views)
- **Boolean:** Direct binding with localized True/False captions (Dropdown and List views)

---

## 2. Key Features at a Glance

| Feature | Dropdown | List View | Table View |
|---|:---:|:---:|:---:|
| **Single selection (Reference)** | Yes | Yes | Yes |
| **Multi selection (Reference Set)** | Yes | Yes | Yes |
| **Enumeration / Boolean support** | Yes | Yes | No |
| **Search / filter** | Yes | Yes | Yes (Global + Per-Column) |
| **Custom content in options** | Yes | Yes | Yes (per column) |
| **Clearable selection** | Yes | Yes | Yes |
| **Keyboard navigation** | Yes (Downshift ARIA) | Yes | Yes |
| **Select All** | Yes | Yes | Yes (3-state header checkbox) |
| **Pagination** | N/A | Page size scroll cap | Paging buttons or virtual scrolling |
| **Column sorting** | N/A | N/A | Yes (3-state: asc, desc, unsorted) |
| **Column filtering** | N/A | N/A | Yes |
| **Column resizing** | N/A | N/A | Yes (drag header border) |
| **Column reordering** | N/A | N/A | Yes (drag and drop) |
| **Column visibility toggle** | N/A | N/A | Yes (runtime column picker) |
| **Offline capable** | Yes | Yes | Yes |

---

## 3. Data Source Types

### 3.1 Association
The primary and most versatile data source type.
- **Entity:** The association connecting the page context object to the selectable entity (Reference or Reference Set).
- **Selectable objects:** Database, microflow, or nanoflow retrieving available options.
- **Caption type:** Attribute (string attribute on selectable entity) or Expression (evaluated per object).

### 3.2 Enumeration
Binds directly to an enumeration attribute. Displays localized captions for enumeration values. Supported in **Dropdown** and **List** views.

### 3.3 Boolean
Binds directly to a boolean attribute, presenting localized `True` and `False` options. Supported in **Dropdown** and **List** views.

> **Note:** The **Table** view requires an Association data source to populate columns from selectable objects. Combining Table view with Enumeration or Boolean will trigger a Studio Pro validation error.

---

## 4. View Types

### 4.1 Dropdown View
A modern combo box selector that displays options in an ARIA-compliant floating menu.
- **Filtering:** Type-to-filter with configurable filter matching (Contains, Starts-with, or None).
- **Multi-select Display:** Render selected items as plain comma-separated text or removable pill badges with an "X" button.
- **Selection Methods:** Checkbox mode (options stay in the list) or Row click mode (selected options are removed from the dropdown list).
- **Select All:** Optional Select All button in the menu header.
- **Footer Drop Zone:** Optional footer area to host arbitrary Mendix widgets (e.g., a "Create New" button or action link).
- **Keyboard Navigation:** Fully powered by Downshift for ARIA 1.2 compliance (Arrow keys, Enter, Escape, Home, End).

### 4.2 List View
An inline, always-visible selection list without a dropdown menu.
- **Selection Controls:** Native radio buttons (single selection) or checkboxes (multi selection or configurable).
- **Layout Options:** Vertical (one option per row) or Horizontal multi-column CSS Grid.
- **Search Box:** Optional dedicated search input above the list.
- **Page Size:** Visual cap on visible rows with smooth scrolling (set to `0` to display all without scrolling).
- **Toolbar Actions:** Clear selection button and Select All toggle for multi-selection.

### 4.3 Table View
A rich, purpose-built data table combining multi-column presentation with selection.
- **Row Selection:** 
  - **Checkbox mode:** Leading column with checkboxes or radio buttons.
  - **Container mode:** Whole row is clickable, with configurable background highlight color or dynamic CSS class.
- **Search & Filtering:**
  - **Global search box:** Matches across all columns marked as searchable simultaneously.
  - **Per-column filters:** Input field under each column header for targeted narrowing.
- **Interactive Columns:** Drag-to-resize column borders, drag-and-drop header reordering, 3-state sorting, and runtime column visibility toggle.
- **Pagination:** Classic paging buttons (Above, Below, Both, Always, or Auto) or infinite virtual scrolling.
- **Custom Empty Message:** Optional widget drop zone when no records match.
- **Conditional Styling:** Dynamic row class and dynamic cell class expressions.

#### Column Properties
Each column supports:
- **Content type:** Attribute, Dynamic Text (template), or Custom Content (Mendix widget drop zone).
- **Alignment:** Left, Center, Right.
- **Sizing:** Auto-fill, Auto-fit content, or Manual fractional units, plus minimum width controls.
- **Features:** Per-column toggles for Search, Sort, Filter, Resize, Reorder, and Hide.
- **Tooltips & Dynamic Classes:** Configurable expressions per column/cell.

---

## 5. Selection Modes

### 5.1 Single Selection (Reference)
Backed by a Mendix Reference association or attribute. Selecting a new option replaces the previous one.
- **Dropdown:** Standard single selection.
- **List:** Native radio buttons (or checkboxes in single-select mode).
- **Table:** Radio buttons in leading column or full-row click.

### 5.2 Multi Selection (Reference Set)
Backed by a Mendix Reference Set association. Multiple options can be selected simultaneously.
- **Dropdown:** Badges/labels or comma-separated text; Checkbox or Row-click selection.
- **List:** Checkboxes with Select All toggle.
- **Table:** Leading checkboxes with 3-state header checkbox (All / Some / None), or full-row click.

---

## 6. Search and Filtering

- **Filter Modes:**
  - `Contains`: Matches when typed text appears anywhere in caption (ranked: exact match > starts-with > contains > acronym).
  - `Starts-with`: Matches when typed text appears at the start of any word.
  - `None`: Disables filtering (makes Dropdown read-only, hides search input in List and Table).
- **Global Table Search:** Searches across all searchable columns at once without requiring column selection.

---

## 7. Custom Content & Widget Embedding

Embed rich Mendix widgets directly inside options:
- Product cards with pricing, images, and ratings.
- User avatars with roles and status badges.
- Table columns with action buttons or status chips.
- Configurable display: "Yes" (everywhere) or "List items only" (custom widgets in options list, clean text in the selected value field).

---

## 8. Accessibility (WCAG Compliant)

- **ARIA Roles:** `combobox`/`listbox` (Dropdown), `radiogroup`/`group` (List), `grid`/`rowgroup`/`row`/`gridcell` (Table).
- **Full Keyboard Navigation:** Tab, Arrow keys, Enter, Space, Escape.
- **Screen Reader Announcements:** Configurable status messages for selection changes, option counts, and instructions.
- **Native Form Controls:** Utilizes native `<input type="checkbox">` and `<input type="radio">` elements for maximum accessibility and auto-fill compatibility.
- **Localization:** All labels and messages support Mendix translation (English and Dutch included out of the box).

---

## 9. Key Advantages

1. **Three Views, One Configuration:** Switch visual presentation from Dropdown to List or Table with a single property change on the View tab.
2. **Replaces Multiple Built-in Widgets:** Replaces Reference Selector, Reference Set Selector, Input Reference Set Selector (Checkboxes), Radio Buttons, and Data Grid + Listen widget.
3. **No Helper Entity Needed for Multi-Select Checkboxes:** Reads and writes directly to the Reference Set association without requiring non-persistent helper entities, boolean flags, or microflow synchronizers.
4. **Universal Caption Filtering:** Filters on what the user actually sees, across any attribute or expression caption, without complex XPath or search microflows.
5. **Offline Capable:** Fully operational in offline-first Mendix web applications.
6. **Design-Time Intelligence:** Structure-mode previews in Studio Pro, dynamic property visibility, and validation checks before runtime.

---

## 10. Quick Start

1. Place the **List or Table Selector** inside a Data View context.
2. **General Tab:**
   - Select **Type** (`Association`, `Enumeration`, or `Boolean`).
   - For Association, set the **Entity**, choose **Selectable objects**, and define the **Caption**.
   - Configure **Filter type** and **Clearable**.
3. **View Tab:**
   - Choose **Dropdown**, **List view**, or **Table**.
   - For **List view**: configure layout (Vertical/Horizontal) and page size.
   - For **Table**: add columns and enable capabilities (sorting, filtering, pagination).
4. **Events Tab:** Configure **On change**, **On enter**, or **On leave** actions as needed.
5. **Accessibility Tab:** Review and translate ARIA labels for your target languages.

---

## 11. Technical Specifications

| Specification | Value |
|---|---|
| **Widget ID** | `com.mxtechies.widget.web.listtableselector.ListTableSelector` |
| **Version** | 1.0.0 |
| **Target Platform** | Web (Classic client and React client) |
| **Minimum Mendix Version** | 9.24.0 |
| **Dropdown Engine** | Downshift |
| **Search Engine** | Match-sorter |
| **Offline Capable** | Yes |
| **External CSS Dependencies** | None (self-contained) |

---

## 12. Browser Support

- Google Chrome (latest)
- Mozilla Firefox (latest)
- Microsoft Edge (latest)
- Apple Safari (latest)

---

## Author & Support

- **Author:** Subash (MxTechies)
- **Documentation:** See detailed technical specifications in [`docs/ListTableSelector-Documentation.md`](docs/ListTableSelector-Documentation.md).
