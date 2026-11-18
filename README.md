# Dashjoin Music Store

<img width="1263" height="777" alt="image" src="https://github.com/user-attachments/assets/785a0556-4e54-4e45-a3d6-f8f013d07ce5" />

A small music store app built on the [Chinook](https://github.com/lerocha/chinook-database) sample database
(`chinook.db`, SQLite). It shows off the Dashjoin Low Code Platform with as little configuration as possible:
every page is a short JSON file in `model/`.

```
docker run -p 8080:8080 -e DJ_ADMIN_PASS=djdjdj -e DASHJOIN_HOME=djapp-music -e DASHJOIN_APPURL=https://github.com/dashjoin/djapp-music dashjoin/platform
```

## What's inside

| Where | Shows |
|-------|-------|
| [Home](model/page/Home.json) | an animated [html hero](model/page/Home.hero.html) (spinning record, "now playing", counters), KPI tiles, line and doughnut charts, a map, a table with record links |
| [Explore](model/page/Explore.json) | session variables (`variable` widget) driving charts and tables, the `analytics` report builder |
| [Catalog](model/page/Catalog.json) | `tabs` with an editable `datagrid`, an `actionTable` (albums → playlist), and a custom `html` [album wall](model/page/Catalog.album-wall.html) |
| [Playlists](model/page/Playlists.json) | `stepper` wizard with button forms (`string`, `multi select`) |
| [Team](model/page/Team.json) | `diagram` org chart, chart, `graph` in an `expansion` panel |
| [record pages](model/dj-database/dj%2Fchinook.json) | custom layouts for Artist, Album, Genre, Customer (map, "buy an album" button), Invoice and Playlist (`editRelated`) |
| [queries](model/dj-query-catalog) | SQL catalog queries with optional `year` / `genre` parameters |
| triggers | Invoice `before-create` fills date and billing address, InvoiceLine `after-create` recomputes the invoice total |
| [library](model/dj-library/duration.json) | reusable JSONata function with unit tests |
| [menu](model/widget/dj-sidenav.menu.jsonata) and [theme](model/dj-config/theme.json) | custom side navigation and colors |

## Roles

- `manager`: may change all data
- `sales`: reads everything, may create invoices and playlists
- everyone logged in can read the database and run the queries

For local testing, add users to `djusers.properties` / `djroles.properties` (see the `roles-and-permissions` skill).

## Checking the app

Open `/#/page/Lint` or run `$djLint()`: it checks all configuration and runs the library unit tests.
