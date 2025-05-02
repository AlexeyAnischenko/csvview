# CSV Viewer

A powerful, browser-based CSV file viewer with advanced filtering, sorting, and display options, able to handle huge 200K-lines CSV files. Built with React and Tailwind CSS, running entirely in the browser with no server-side dependencies.

## Features

### File Loading
- 📤 Upload CSV files from local computer
- 🔗 Load CSV files from URLs
- 🔄 URL parameter support for sharing (`?url=your-csv-url`)
- 📝 Multiple separator options (comma, dot, colon, semicolon, pipe, tab, space)

### Data Display
- 📊 Paginated data view with adjustable page size (10-1000 rows)
- ↔️ Adjustable column width (10-100 chars or unlimited)
- 🔍 Tooltips for truncated content
- 🌓 Dark/Light theme support with system preference detection
- 📱 Responsive design for all screen sizes

### Data Management
- 🔄 Drag-and-drop column reordering
- ⬆️ Column sorting (click headers to sort)
- ➡️ Horizontal scrolling with navigation buttons
- 🔍 Smart handling of malformed CSV data
  - Fills missing columns with N/A
  - Truncates excess columns
  - Skips empty lines and comments

### Advanced Filtering
- 🔍 AND filter: Show rows containing all specified terms
- 🔍 OR filter: Show rows containing any specified term
- 🚫 NOT filter: Exclude rows containing specified terms
- ⚡ Case-sensitive filtering option
- 🎯 Real-time filtering with debouncing

### Link Support
- 🔗 Automatic link detection in cells
- 🎯 Smart link truncation with tooltips
- 🔗 Safe external link handling (opens in new tab)

## Technical Implementation

### Core Technologies
- React 18 for UI components and state management
- Tailwind CSS for styling
- Vite for development and building

### State Management
- React hooks for local state management
- Debounced filters for performance
- Memoized data processing for efficient filtering and sorting

### Performance Optimizations
- Virtualized table rendering for large datasets
- Debounced filter updates
- Memoized data processing
- Efficient column reordering without full re-renders

### Security Features
- Safe external link handling
- HTML content sanitization
- URL parameter validation

### URL Parameters

Share CSV files by adding the `url` parameter:
```
http://your-domain/csvview.html?url=https://example.com/data.csv
```
