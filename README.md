# CSV Viewer

A powerful, browser-based CSV file viewer with advanced filtering, sorting, and display options, able to handle huge 200K-lines CSV files. Built with React and Tailwind CSS, running entirely in the browser with no server-side dependencies.

## Features

### File Loading
- Upload CSV files from local computer
- Load CSV files from URLs with expandable input field
- Paste CSV data directly from clipboard
- Multiple separator options (comma, dot, colon, semicolon, pipe, tab, space)
- Automatic CSV parsing with smart error handling

### Data Display
- Paginated data view with adjustable page size (10-1000 rows)
- Adjustable column width (10-100 chars or unlimited)
- Column shrinking feature - minimize columns to 5 characters with expand/restore toggle
- Tooltips for truncated content and collapsed columns
- Dark/Light theme support with system preference detection
- Responsive design for all screen sizes

### Data Management
- Drag-and-drop column reordering
- Column sorting (click headers to sort ascending/descending)
- Horizontal scrolling with navigation buttons
- Smart handling of malformed CSV data
  - Fills missing columns with N/A
  - Truncates excess columns
  - Skips empty lines and comments

### Advanced Filtering
- AND filter: Show rows containing all specified terms (space-separated)
- OR filter: Show rows containing any specified term (space-separated)
- NOT filter: Exclude rows containing specified terms (space-separated)
- Case-sensitive filtering option
- Real-time filtering with debouncing for performance

### Link Support
- Automatic link detection in cells with HTML anchor tags
- Smart link truncation with tooltips
- Safe external link handling (opens in new tab)
- Preserves text before and after links in cells

### State Persistence and Sharing
- Complete URL parameter support for sharing viewer state
- Share button copies current URL with all settings to clipboard
- All settings preserved in URL: filters, sorting, pagination, theme, column state
- Bookmark-friendly URLs that restore exact viewer state

## URL Parameters

The viewer supports comprehensive URL parameter sharing for all settings:

### Basic Usage
Share CSV files by adding the `url` parameter:
```
http://your-domain/csvview.html?url=https://example.com/data.csv
```

### Complete Parameter List
- `url` - CSV file URL to load
- `separator` - Column separator character (default: comma)
- `pageSize` - Rows per page (default: 50)
- `currentPage` - Current page number (default: 1)
- `theme` - UI theme: 'light' or 'dark' (default: system preference)
- `maxColumnWidth` - Maximum column width in characters or 'Infinity'
- `andFilter` - AND filter terms (space-separated)
- `orFilter` - OR filter terms (space-separated)
- `notFilter` - NOT filter terms (space-separated)
- `caseSensitive` - Case-sensitive filtering: 'true' or 'false'
- `sortColumn` - Column index for sorting (-1 for no sorting)
- `sortDirection` - Sort direction: 'asc' or 'desc'
- `collapsedCols` - Comma-separated list of collapsed column indices

### Example with Multiple Parameters
```
http://your-domain/csvview.html?url=https://example.com/data.csv&separator=;&pageSize=100&theme=dark&andFilter=john%20doe&sortColumn=0&sortDirection=desc&collapsedCols=2,3,5
```

## Technical Implementation

### Core Technologies
- React 18 for UI components and state management
- Tailwind CSS for responsive styling and dark mode
- Babel for JSX transformation in browser

### State Management
- React hooks for local state management
- URL synchronization for all application state
- Debounced filters for performance optimization
- Memoized data processing for efficient filtering and sorting

### Performance Optimizations
- Debounced filter updates (500ms delay)
- Memoized data processing for large datasets
- Efficient column reordering without full re-renders
- Smart pagination to handle large CSV files

### Security Features
- Safe external link handling with rel="noopener noreferrer"
- HTML content sanitization for link detection
- URL parameter validation and sanitization
- Clipboard API with fallback for older browsers

### Browser Compatibility
- Modern Clipboard API with fallback methods
- Cross-browser drag and drop support
- Responsive design for mobile and desktop
- Dark mode with system preference detection

## Usage Instructions

### Loading Data
1. **Upload File**: Click "Upload CSV" to select a local file
2. **Load from URL**: Click "Load CSV from URL" to reveal input field, enter URL and click "Load"
3. **Paste Data**: Click "Paste CSV" to paste data directly from clipboard

### Customizing Display
1. **Separator**: Select appropriate column separator from dropdown
2. **Column Width**: Choose maximum character limit per column
3. **Page Size**: Set number of rows to display per page
4. **Theme**: Toggle between light and dark modes

### Managing Columns
1. **Reorder**: Drag column headers to rearrange
2. **Sort**: Click column headers to sort (click again to reverse)
3. **Collapse**: Click "5ch" button in header to minimize column width
4. **Expand**: Click expand arrow button to restore column width

### Filtering Data
1. **AND Filter**: Enter space-separated terms that must all be present
2. **OR Filter**: Enter space-separated terms where any can be present
3. **NOT Filter**: Enter space-separated terms to exclude
4. **Case Sensitive**: Toggle to match exact case

### Sharing
1. **Share Button**: Copies current URL with all settings to clipboard
2. **Bookmarks**: Save URLs to preserve exact viewer state
3. **Direct Links**: Share URLs with colleagues to show specific data views
