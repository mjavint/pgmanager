# PostgreSQL Manager

<p align="center">
  <img src="https://github.com/mjavint/pgmanager/blob/main/img/icon.png?raw=true" alt="PostgreSQL Manager Logo" width="128" height="128"/>
</p>

<p align="center">
  <a href="https://marketplace.visualstudio.com/items?itemName=mvintg.pg-manager">
    <img src="https://img.shields.io/visual-studio-marketplace/v/mvintg.pg-manager" alt="Version"/>
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=mvintg.pg-manager">
    <img src="https://img.shields.io/visual-studio-marketplace/i/mvintg.pg-manager" alt="Installs"/>
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=mvintg.pg-manager&ssr=false#review-details">
    <img src="https://img.shields.io/visual-studio-marketplace/r/mvintg.pg-manager" alt="Rating"/>
  </a>
</p>

Complete PostgreSQL database management for VS Code: explorer, connection profiles, SQL editor, query execution, table data viewer, roles, and database operations.

## Features

### 1) Query Builder

![Query Builder](https://github.com/mjavint/pgmanager/blob/main/img/demo-query-builder.gif?raw=true)

- Visual query builder for constructing SQL queries without writing code
- Drag-and-drop tables/views from explorer to canvas
- Add/remove tables, joins, and conditions with UI controls
- Generate SQL from visual design and open in SQL editor
- Open query builder from table/view/schema/database context in explorer

### 2) Database Explorer

![Database Explorer](https://github.com/mjavint/pgmanager/blob/main/img/04-sql-editor.png?raw=true)

- Browse servers, databases, schemas, tables, views, functions, sequences, and roles
- Expand/collapse hierarchy with context-aware actions per node
- Filter objects by name and clear filters quickly
- Refresh explorer and node states on demand

### 3) Connection Management

![Connection Management 1](https://github.com/mjavint/pgmanager/blob/main/img/01-connect-form.png?raw=true)

![Connection Management 2](https://github.com/mjavint/pgmanager/blob/main/img/02-connect-string.png?raw=true)

![Connection Management 3](https://github.com/mjavint/pgmanager/blob/main/img/03-connect-list.png?raw=true)

- Add, edit, test, connect, disconnect, and remove PostgreSQL connections
- Store multiple connection profiles (`pg.connections`)
- Save passwords securely using VS Code `SecretStorage`
- SSL/TLS support in profile configuration
- Connection management from both explorer context menu and connections UI panel

### 4) SQL Query Editor

![SQL Query Editor](https://github.com/mjavint/pgmanager/blob/main/img/06-query-results.png?raw=true)

- Open SQL editor from connected server/database/schema nodes
- Run query (`Ctrl+Enter` / `Cmd+Enter`)
- Cancel running query (`Ctrl+Shift+C` / `Cmd+Shift+C`)
- Save SQL to file (`Ctrl+S` / `Cmd+S`)
- Request and use schema metadata in-editor for better authoring

### 5) Query Results Panel

- Multi-result rendering with column metadata
- Row count and elapsed time
- SQL notices/errors surfaced in UI

### 6) Table Data Viewer

- View table/view data in a paginated grid
- Server-side page fetch with sort and filter support
- In-grid cell editing and save/discard workflow
- Row selection and row delete workflow
- Foreign key lookup popover for FK columns
- Global text search in loaded page
- CSV export of visible/selected rows

### 7) Table Structure & Alter Table

![Table Structure & Alter Table](https://github.com/mjavint/pgmanager/blob/main/img/view-data.gif?raw=true)

- Open table structure panel with:
  - Column list (type, nullability, default, PK)
  - Indexes (unique/primary)
  - Constraints
- Alter table actions:
  - Rename column
  - Change column type
  - Add column
  - Drop column

### 8) Role/User Management

![Role](https://github.com/mjavint/pgmanager/blob/main/img/07-create-role.png?raw=true)

- View roles/users list
- Create role/user
- Alter role/user
- Drop role/user
- Manage role privileges

### 9) Database Operations

- Create database
- Drop database

### 10) SQL Code Generation

![SQL Code Generation](https://github.com/mjavint/pgmanager/blob/main/img/05-sql-completion.png?raw=true)

- Generate `SELECT TOP 1000`
- Generate `INSERT`
- Generate `CREATE TABLE`

### 11) SQL Autocompletion

- Context-aware completions based on schema metadata
- Suggestions for schemas, tables, columns, keywords, built-in functions, and types

## Command Reference

| Command | Description |
|---|---|
| `pg.showConnections` | Open connections panel |
| `pg.addConnection` / `pg.editConnection` / `pg.removeConnection` | Manage profiles |
| `pg.connect` / `pg.disconnect` | Connect or disconnect server |
| `pg.refreshExplorer` | Refresh explorer tree |
| `pg.filterTables` / `pg.clearTableFilter` | Filter/clear explorer objects |
| `pg.newQuery` | Open SQL editor |
| `pg.runQuery` / `pg.cancelQuery` / `pg.saveQuery` | Query execution controls |
| `pg.explainQuery` | Run EXPLAIN for SQL |
| `pg.viewTableData` | Open table data grid |
| `pg.viewTableStructure` | Open table structure view |
| `pg.alterTable` | Open alter table actions |
| `pg.createDatabase` / `pg.dropDatabase` | Database lifecycle |
| `pg.createRole` / `pg.alterRole` / `pg.dropRole` | Role lifecycle |
| `pg.managePrivileges` / `pg.viewRoles` / `pg.refreshRoles` | Role administration |
| `pg.generateSelectTop` / `pg.generateInsert` / `pg.generateCreateTable` | SQL generators |
| `pg.copyName` | Copy selected object name |

## Requirements

- Visual Studio Code `1.85.0+`
- PostgreSQL `9.0+`
- Node.js `18+` (development only)

## Installation

1. Open VS Code
2. Go to Extensions (`Ctrl+Shift+X`)
3. Search for `PostgreSQL Manager`
4. Click Install

Marketplace: https://marketplace.visualstudio.com/items?itemName=mvintg.pg-manager

## Getting Started

1. Open the PostgreSQL Manager activity bar view
2. Click `Add Connection`
3. Enter host, port, user, database, password, and SSL options
4. Connect from the server node
5. Start with `New SQL Query` or `View Data` on a table/view

## Configuration

| Setting | Default | Description |
|---|---|---|
| `pg.connections` | `[]` | Saved connection profiles (passwords are stored in SecretStorage) |
| `pg.queryRowLimit` | `1000` | Default maximum rows in query results |
| `pg.tablePageSize` | `100` | Rows per page in table viewer |
| `pg.statementTimeout` | `30000` | Statement timeout in ms (`0` disables timeout) |
| `pg.poolMax` | `5` | Maximum pool size per connection |
| `pg.poolIdleTimeout` | `30000` | Pool idle timeout in ms |

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl+Enter` / `Cmd+Enter` | Run SQL query |
| `Ctrl+S` / `Cmd+S` | Save SQL file |
| `Ctrl+Shift+C` / `Cmd+Shift+C` | Cancel running query |

## Notes

- The table data viewer currently supports edit/delete workflows in-grid.
- If you need to add records, use SQL editor (`INSERT ...`) or generated insert templates.

## Development

```bash
npm install
npm run compile
npm run watch
```

## License

MIT. See [LICENSE](LICENSE).

## Support

Issues and feature requests: https://github.com/mjavint/pg-manager/issues

---

<p align="center">Made with ❤️ for PostgreSQL developers</p>
