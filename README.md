# zotero-open

A tiny redirect page to open a PDF (with its annotations) in Zotero from Notion.

Notion blocks `zotero://` links. This page acts as a go-between: it takes a Zotero attachment key from the URL and redirects to `zotero://open-pdf/library/items/<key>`.

## Usage with Notero

1. In the Notion database synced by [Notero](https://github.com/dvanoni/notero), add a `File Path` property (Text), then resync your items from Zotero.
2. Add a Formula property with:

```
if(empty(prop("File Path")), "", link("📄 Open PDF", "https://your-username.github.io/zotero-open/?" + prop("File Path").match("[A-Z0-9]{8}").first()))
```

The formula extracts the 8-character key from the file path (e.g. `...\Zotero\storage\32PUWSGN\article.pdf`) and builds the link.

## Requirements

- Zotero installed on the device, with file syncing enabled if you use several devices.
- Allow your browser to open Zotero on the first click.

No personal data is stored here: only the attachment key passes through the URL.
