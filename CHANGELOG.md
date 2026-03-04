# Changelog

## [0.5.0] - 2026-03-04

### Added Truncate Table

![Truncate Table](https://github.com/mjavint/pgmanager/blob/main/img/00-truncate-table.png?raw=true)
![Truncate Table](https://github.com/mjavint/pgmanager/blob/main/img/01-truncate-table.png?raw=true)

- Truncate tables directly from the explorer context menu
- Options dialog with RESTART IDENTITY and CASCADE checkboxes
- Confirmation modal before executing truncation

### Added Show DDL

![Show DDL](https://github.com/mjavint/pgmanager/blob/main/img/show-ddl.png?raw=true)

- View DDL (Data Definition Language) for tables, views, functions, and sequences
- Available from the explorer context menu on supported node types
- Opens generated SQL in a new editor tab

## [0.4.0] - 2026-02-26

### Added Favorite Queries

![Favorite Queries](https://github.com/mjavint/pgmanager/blob/main/img/sql-favorites.png?raw=true)

- Save SQL queries to favorites directly from the SQL Editor toolbar
- Collapsible side panel to browse, search, and manage favorite queries
- Card-based UI for each favorite with name, date, and full SQL preview
- Click a favorite card to load the query into the editor instantly
- Search/filter favorites by any keyword in name or SQL content
- Favorites are persisted in user settings (`pg.favoriteQueries`)

### Added Database Owner Management

- Change database owner from the explorer context menu

![Database Owner Management](https://github.com/mjavint/pgmanager/blob/main/img/change-owner.png?raw=true)

### Improved

- SQL Editor now adapts to the active VS Code color theme (light, dark, high contrast)

## [0.3.1] - 2026-02-22

### Added SQL Editor Improvements

 Copy, Paste, Cut, and Select All buttons in SQL Editor toolbar
 Keyboard shortcuts: Ctrl+C, Ctrl+V, Ctrl+X, Ctrl+A
 Context menu enabled for Monaco editor
 Copy with syntax highlighting support

### Added Autocomplete Enhancements

 PostgreSQL operators autocomplete (=, !=, <, >, <=, >=, AND, OR, BETWEEN, IN, LIKE, ILIKE, etc.)
 SQL clause snippets (SELECT, INSERT, UPDATE, DELETE, JOIN, CREATE TABLE, etc.)
 Context-aware completions for ORDER BY, GROUP BY, HAVING, LIMIT, OFFSET clauses
 Table alias support: auto-detect aliases and suggest columns with prefix
 Improved column suggestions with PK badges
 Snippet priority and better sorting

## [0.3.0] - 2026-02-22

### Added Table Structure Designer

![Table Structure Designer](https://github.com/mjavint/pgmanager/blob/main/img/design-table.png?raw=true)

- New table structure panel for visualizing and modifying table schema
- Tabbed interface for columns, indexes, foreign keys, and constraints
- Inline editing for columns (name, type, nullable, default value)
- SQL preview before applying changes
- Add, modify, and delete columns directly from the UI
- Rename column, change column type, and column operations
- Set column nullable and default values
- Better error handling and loading states
- Improved alter table operations with transaction support

## [0.2.0] - 2026-02-21

### Added Query Builder

![Query Builder](https://github.com/mjavint/pgmanager/blob/main/img/demo-query-builder.gif?raw=true)

- Visual query builder for constructing SQL queries without writing code
- Drag-and-drop tables/views from explorer to canvas
- Add/remove tables, joins, and conditions with UI controls
- Generate SQL from visual design and open in SQL editor
- Open query builder from table/view/schema/database context in explorer

## [0.1.0] - 2026-02-20

### Added

- **Database Explorer**: Browse PostgreSQL servers, databases, schemas, tables, views, functions, and sequences
- **Connection Management**: Add, edit, remove, and manage multiple PostgreSQL connections
- **Query Editor**: Execute SQL queries with keyboard shortcuts (Ctrl+Enter)
- **Save Queries**: Save SQL files with Ctrl+S
- **Cancel Queries**: Cancel running queries with Ctrl+Shift+C
- **EXPLAIN Queries**: Analyze query execution plans
- **Table Data Viewer**: View and edit table data in a paginated grid
- **Role/User Management**: Create, alter, drop roles, and manage privileges
- **Database Operations**: Create and drop databases
- **SQL Code Generation**: Generate SELECT TOP 1000, INSERT, and CREATE TABLE statements
- **SQL Autocompletion**: Intelligent SQL completion based on database schema
- **Object Filtering**: Filter tables, views, functions in explorer
- **Copy Name**: Copy table/column names to clipboard
- **SSL Support**: Connect to PostgreSQL servers using SSL/TLS
- **Secure Storage**: Passwords stored securely using VS Code SecretStorage

### Features

- PostgreSQL icon in activity bar
- Context menu actions in explorer
- Keyboard shortcuts for common operations
- Configurable query timeouts and connection pools
