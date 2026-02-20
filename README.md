# PostgreSQL Manager

<p align="center">
  <img src="img/icon.png" alt="PostgreSQL Manager Logo" width="128" height="128"/>
</p>

<p align="center">
  <a href="https://marketplace.visualstudio.com/items?itemName=mvintg.pg-manager">
    <img src="https://img.shields.io/visual-studio-marketplace/v/mvintg.pg-manager.svg" alt="Version"/>
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=mvintg.pg-manager">
    <img src="https://img.shields.io/visual-studio-marketplace/rating/mvintg.pg-manager.svg" alt="Rating"/>
  </a>
  <a href="LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License"/>
  </a>
</p>

Complete PostgreSQL database management for VS Code: explorer, connection profiles, SQL editor, query execution, table data viewer, roles, and database operations.

## Features

### 1) Database Explorer
- Browse servers, databases, schemas, tables, views, functions, sequences, and roles
- Expand/collapse hierarchy with context-aware actions per node
- Filter objects by name and clear filters quickly
- Refresh explorer and node states on demand

### 2) Connection Management
- Add, edit, test, connect, disconnect, and remove PostgreSQL connections
- Store multiple connection profiles (`pg.connections`)
- Save passwords securely using VS Code `SecretStorage`
- SSL/TLS support in profile configuration
- Connection management from both explorer context menu and connections UI panel

### 3) SQL Query Editor
- Open SQL editor from connected server/database/schema nodes
- Run query (`Ctrl+Enter` / `Cmd+Enter`)
- Cancel running query (`Ctrl+Shift+C` / `Cmd+Shift+C`)
- Save SQL to file (`Ctrl+S` / `Cmd+S`)
- Request and use schema metadata in-editor for better authoring

### 4) Query Results Panel
- Multi-result rendering with column metadata
- Row count and elapsed time
- SQL notices/errors surfaced in UI

### 5) Table Data Viewer
- View table/view data in a paginated grid
- Server-side page fetch with sort and filter support
- In-grid cell editing and save/discard workflow
- Row selection and row delete workflow
- Foreign key lookup popover for FK columns
- Global text search in loaded page
- CSV export of visible/selected rows

### 6) Table Structure & Alter Table
- Open table structure panel with:
  - Column list (type, nullability, default, PK)
  - Indexes (unique/primary)
  - Constraints
- Alter table actions:
  - Rename column
  - Change column type
  - Add column
  - Drop column

### 7) Role/User Management
- View roles/users list
- Create role/user
- Alter role/user
- Drop role/user
- Manage role privileges

### 8) Database Operations
- Create database
- Drop database

### 9) SQL Code Generation
- Generate `SELECT TOP 1000`
- Generate `INSERT`
- Generate `CREATE TABLE`

### 10) SQL Autocompletion
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
