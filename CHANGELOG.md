# Changelog

## [0.6.1] - 2026-03-23

### Fixed — Database Schema Modeler

- **FK constraints for `one2many` relationships were never generated**: the `generateDDL` logic looked for the FK column in the source node (the "one" table), but for `one2many` the FK column lives in the target node (the "many" table). The direction of the `ALTER TABLE ... ADD CONSTRAINT FOREIGN KEY` is now corrected for this relationship type.
- **Relationships were not displayed when reopening the modeler**: layout edges were overwriting the edges just loaded from the database. The layout file now saves and restores **only node positions**, never edges.
- **Relationships were not refreshed after "Apply to DB"**: after executing the DDL successfully, the backend now automatically reloads the schema from the DB and sends the updated data to the webview.
- **Loading without feedback**: added loading overlay with spinner while fetching and rendering the schema, both on initial load and after applying changes.

### Added — Modeler Toolbar

- Complete redesign of the toolbar with representative SVG icons for each action
- Buttons grouped with visual separators: **New Table** | **Undo / Redo** | **LR / TB / Auto Layout** | **Save / Apply to DB**
- Visual toggle for layout direction (LR / TB) with highlighted active state
- Icon-only buttons for Undo/Redo with descriptive tooltips

### Added — Selective Explorer Refresh

Feature proposed by [Esteban Acevedo Santana](https://github.com/acevedoesteban999) in [#3](https://github.com/mjavint/pgmanager/issues/3)

- **Refresh Database** (`pg.refreshDatabase`): reloads only the subtree of a database without affecting the rest of the explorer. Available in the context menu and as an inline button when hovering over a database node.
- **Refresh Schema** (`pg.refreshSchema`): reloads only the tables, views, functions, and sequences of a specific schema.
- **Refresh Table / View** (`pg.refreshTable`): reloads only the columns of a specific table or view.

## [0.6.0] - 2026-03-22

### Added Database Schema Modeler

![Database Schema Modeler](https://github.com/mjavint/pgmanager/blob/main/img/db-modeler.gif?raw=true)

A full visual schema designer for PostgreSQL, accessible via right-click on any database or schema in the explorer.

#### Visual Canvas
- Interactive ERD canvas powered by ReactFlow with pan, zoom, and drag
- Auto-layout engine using **dagre** (Left→Right or Top→Bottom direction)
- Minimap for quick navigation on large schemas
- Reverse-engineer existing schemas into diagrams automatically

#### Table Design
- Create new tables graphically with the **+ New Table** button
- Double-click any table node to open the column editor
- Full column editor: name, type, length, precision/scale, PK, Unique, Nullable, Default, Check constraint
- 30+ supported PostgreSQL data types in dropdown
- Visual indicators on nodes: `🔑` Primary Key, `🔗` Foreign Key, `U` Unique, `?` Nullable

#### Relationship Types
- Draw connections between tables to define relationships
- **Many to One (N:1)**: automatically adds a FK column (`{target}_id`) to the source table
- **One to Many (1:N)**: automatically adds a FK column (`{source}_id`) to the target table
- **Many to Many (M:N)**: automatically creates a junction table (`{a}_{b}_rel`) with composite PK and two FK columns
- Relationship type dialog shown on every new connection

#### FK Edge Properties
- Click any relationship edge to open the FK properties panel
- Edit constraint name, ON DELETE action, and ON UPDATE action
- Supported actions: NO ACTION, RESTRICT, CASCADE, SET NULL, SET DEFAULT
- Delete relationships directly from the panel

#### DDL Generation & Apply
- **Save Changes**: generates complete DDL (`CREATE TABLE`, `ALTER TABLE ... ADD CONSTRAINT FOREIGN KEY`, `CREATE INDEX` for FK columns) and opens it in a SQL editor tab
- **Apply to DB**: executes the generated DDL directly against the connected database inside a transaction — with confirmation dialog and rollback on error
- Type modifiers included: `varchar(n)`, `numeric(p,s)`, etc.
- `NOT NULL`, `DEFAULT`, `CHECK`, `PRIMARY KEY`, `UNIQUE` constraints generated correctly

#### Undo / Redo & Persistence
- Full undo/redo stack (`Ctrl+Z` / `Ctrl+Y` or `Ctrl+Shift+Z`)
- Diagram layout auto-saved to `.vscode/pg-modeler/{schema}.layout.json`
- Node positions restored automatically on next open

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
