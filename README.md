# Bases Board — personal fork

Personal distribution of [Bases Board](https://github.com/flowing-abyss/obsidian-bases-board), with QuickAdd note creation and card deletion.

<p align="center">
  <img src="assets/board-dark.png" alt="A research board in the dark theme, with experiments grouped by stage into columns and by area into rows" width="49%">
  <img src="assets/board-light.png" alt="The same research board in the light theme" width="49%">
</p>

Bases Board adds a board view to Obsidian Bases. Your notes become cards laid out in
columns and rows, and moving a card updates the note's properties. Use it as a Kanban
board or as a gallery.

## Building a board

1. Open a base, add a view and choose **Board**.
2. Pick a **Group property** to sort notes into columns.
3. Add a **Sub-group property** if you want each column split into rows.

With only a sub-group property set, the cards form a gallery instead.

## Cards

You can edit properties right on the card, and links keep their Supercharged Links
styling.

- **Image property** adds a cover image or video from a URL, a link or a file in your
  vault.
- **Icon property** puts a [Lucide](https://lucide.dev/icons/) icon before the title.
- **ID property** shows an ID above the title that copies on click.
- **Hide empty properties** keeps cards short.
- **Card size** switches between small, medium and large cards.

**Icon mapping** picks an icon for each value of the icon property.

```
idea=lightbulb
training=cpu
bug=bug
```

To find icon names, run **Browse icons** from the command palette.

## Columns and rows

- Rename a column or row without changing the property value behind it.
- Reorder, hide and color them from the header menu.
- Choose whether colors apply to headers, cells or cards.
- Fold rows to hide their cards.
- Keep empty columns on the board by listing them in **Column order**.
- Set **Row order** to arrange sub-groups.

In Board views, `groupOrder` is now `columnOrder` and `subGroupOrder` is `rowOrder`.
Existing orders are migrated automatically in `.base` files and embedded `base`
blocks, including files added later through sync.
Board hides the native Group menu unless native grouping is already configured for
that view, so existing group filters remain accessible. When a view has native
`groupBy`, its `groupOrder` stays a native filter; set **Column order** separately.

## New notes

The **New note** button in each cell creates a note with that cell's column and row
values already set. Choose a **Folder** and a **Template** for new notes, including
Templater templates.

To use a [QuickAdd](https://github.com/chhoumann/quickadd) choice instead, enable
QuickAdd and set **New note → QuickAdd choice** to the choice name. When configured,
the choice handles note creation; Board's Folder, Template and Open settings are ignored.
The column and row values are passed as QuickAdd variables named after their note
properties. Reference those variables in your choice's template to use the cell values.
For example, for a `status` row and a QuickAdd Template choice, use
`{{VALUE:Todo,Doing,Done|name:status|label:Status}}` for the status property. Opening the
choice outside the board still asks for a status. Empty groups and calculated or file
properties are not passed as variables.

Right-click a card and choose **Delete file** to delete its underlying file. Obsidian's
file deletion and trash settings apply.

## Installation

This personal fork uses the distinct plugin ID `bases-board-jisko` so that updates to the
official **Bases Board** plugin cannot replace it. Install and update it with
[BRAT](https://github.com/TfTHacker/obsidian42-brat), using
`JSchoreels/obsidian-bases-board` as the repository. The plugin needs Obsidian 1.10.3 or
later.

When switching an existing vault from `bases-board` to this fork, copy the original
plugin's `data.json` into the new plugin folder to retain its settings. Disable the
original before enabling the fork: both register the same `board-view` type, so only one
should be active at a time. Existing Bases and notes keep their view configuration.

The fork follows its own GitHub releases. Before releasing, commit curated notes for the
exact version to `CHANGELOG.md` and run the checks. Include `[skip ci]` in the release
commit message to skip the inherited upstream tag workflow. Push the release commit and
its matching tag to this fork, then create the GitHub release with the curated changelog
entry as its description and `manifest.json`, `main.js`, and `styles.css` as assets.

## Contributing

Issues and pull requests are welcome. Please read [Contributing](CONTRIBUTING.md) before
you start.

## License

[MIT](LICENSE)
