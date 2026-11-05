# Changelog

## 1.2.1-jisko.1

### User facing changes

- Create a note from a board row using a configured QuickAdd choice; the row and column values are passed to the form automatically.
- Delete a card's underlying note from its context menu, using Obsidian's configured deletion and trash behavior.
- Keep the board responsive after opening a card's context menu, and cancel QuickAdd forms without creating a note.
- Install this personal fork separately from the official plugin and receive its releases through BRAT.

### Technical details

- First release of the personal fork, based on Bases Board 1.2.1 and the local QuickAdd and card-deletion changes.
- The plugin ID is `bases-board-jisko`; existing `board-view` configurations remain compatible. Copy the original plugin's `data.json` when migrating its settings, and do not enable both variants at once.
- When a QuickAdd choice is configured, it owns note creation; the board's own folder, template, and open-after-creation settings do not apply. The choice must use the passed property names for row and column values.
- Verified with the 132-test suite, a production build, lint, and formatting checks.
