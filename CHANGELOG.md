# Changelog

## [0.2.0] - 2024-06-15

### Added Query Builder

![Query Builder](https://github.com/mjavint/pgmanager/blob/main/img/demo-query-builder.gif?raw=true)

- Visual query builder for constructing SQL queries without writing code
- Drag-and-drop tables/views from explorer to canvas
- Add/remove tables, joins, and conditions with UI controls
- Generate SQL from visual design and open in SQL editor
- Open query builder from table/view/schema/database context in explorer

## [0.1.0] - 2024-02-18

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

[Released]: https://github.com/mjavint/pg-manager/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/mjavint/pg-manager/releases/tag/v0.1.0
