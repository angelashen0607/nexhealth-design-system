# Table

Data table for lists of patients, appointments, payments, and other records. Supports sorting, filtering, pagination, and row actions.

## Features

- Column sorting (ascending / descending / none)
- Column resizing (drag handle)
- Row selection (checkbox column)
- Sticky header on scroll
- Pagination (page-based or cursor-based)
- Empty state with illustration
- Loading state with skeleton rows
- Responsive: horizontal scroll on narrow viewports, or card view on mobile

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `columns` | ColumnDef[] | — | Column definitions |
| `data` | array | — | Row data |
| `loading` | boolean | `false` | Shows skeleton rows |
| `selectable` | boolean | `false` | Adds checkbox column |
| `onSelect` | function | — | Called with selected row IDs |
| `sortable` | boolean | `true` | Enables column sorting |
| `pagination` | object | — | `{ page, pageSize, total, onChange }` |
| `emptyState` | ReactNode | — | Shown when data is empty |
| `onRowClick` | function | — | Row click handler |
| `stickyHeader` | boolean | `true` | Sticky header on scroll |

## ColumnDef

| Prop | Type | Description |
|---|---|---|
| `key` | string | Data field key |
| `header` | string | Column header text |
| `width` | string · number | Column width |
| `sortable` | boolean | Whether this column is sortable |
| `render` | function | Custom cell renderer `(value, row) => ReactNode` |
| `align` | `left` · `center` · `right` | Cell alignment |

## Specifications

- Header: `neutral.50` background, `bodySmall` text style, `semibold` weight
- Rows: 48px min height, `neutral.0` background
- Hover: `neutral.50` background
- Selected: `primary.50` background
- Border: 1px `neutral.200` between rows
- Padding: 12px horizontal per cell

## Accessibility

- Uses semantic `<table>`, `<thead>`, `<tbody>`, `<th>`, `<td>`
- Sort buttons have `aria-sort` attribute
- Pagination controls are keyboard navigable
- Row selection checkboxes have accessible labels
