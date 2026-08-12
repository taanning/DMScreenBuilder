<div align="center">
  <h1>DM Screen Builder</h1>
  <p><strong>Build a custom, printable Dungeon Master screen directly in your browser.</strong></p>
  <p>
    <a href="https://taanning.github.io/DMScreenBuilder"><strong>Open the DM Screen Builder</strong></a>
    &nbsp;&middot;&nbsp;
    <a href="https://github.com/taanning/DMScreenBuilder">View the source</a>
  </p>
</div>

<hr>

## What is it?

DM Screen Builder is a lightweight, browser-based tool for creating a reference screen tailored to your game. Start with the included rules reference, then edit, arrange and style the information you need at the table.

It is published as a static website, so there is no account, installation or server-side setup required.

## Features

- **Ready-to-use reference content** covering combat, conditions, adventuring, characters, encounters, world details and gear
- **Multiple pages** for organising your screen by theme
- **Flexible sections** with columns, tables and card-style layouts
- **Drag, resize and arrange** sections on a precise 40 × 40 grid
- **Custom styling** with colour concepts, section colours and global font sizes
- **Layers and visibility controls** for managing overlapping content
- **Undo and redo** while editing
- **Print-ready output** for taking your custom screen to the table

## Quick start

1. Open the [live DM Screen Builder](https://taanning.github.io/DMScreenBuilder).
2. Edit the starter pages or create a new blank page.
3. Select a section to change its title, subtitle, colour, content and layout.
4. Drag sections to reposition them, or use the resize handle to change their size.
5. Use **Print** when your screen is ready. For the cleanest output, set print margins to **None** in the browser print dialog.

## Saving your work

Your changes are automatically saved in a cookie in the browser you are using. This keeps your current screen available when you return to the site, but it is local to that browser and is not synced to an account or stored in the cloud.

For a permanent backup:

1. Open **Menu**.
2. Choose **Export as JSON**.
3. Keep the downloaded JSON file somewhere safe.
4. Later, use **Menu → Import JSON** to continue editing it.

Export your screen before clearing browser data, switching browsers or using private browsing. The exported JSON file is the portable copy of your work.

## Running locally

The project is intentionally dependency-free. To run it locally, serve the repository directory with any simple static web server and open `index.html` through that server. The app loads its starter content from `data.json`, so serving the files is preferable to opening the HTML file directly.

For example, with Python installed:

```bash
python -m http.server 8000
```

Then visit <http://localhost:8000> in your browser.

## Built with

- HTML
- CSS
- Vanilla JavaScript
- JSON template data

## License

This project is licensed under the [GNU General Public License v3.0](LICENSE).

<div align="center">
  <sub>Made by <a href="https://github.com/taanning">Taanning</a> for DMs who want their most-used rules close at hand.</sub>
</div>
