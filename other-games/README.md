# Other games list

`games.json` in this folder is the list behind the "Our Other games" page in Simple Farming IO. The game downloads it from `https://woodheadgames.co.za/other-games/games.json` each time the page opens, so changing the list needs **no app update**: edit the file, commit and push, and GitHub Pages serves the new list.

## Format (version 1)

```json
{
  "version": 1,
  "games": [
    {
      "id": "auto-empire-2",
      "title": "Auto Empire 2: Car Dealer",
      "thumbnail": "auto-empire-2.png",
      "storeUrl": "https://play.google.com/store/apps/details?id=com.woodheadgames.autoempire2"
    }
  ]
}
```

- `version`: always `1`.
- `games`: shown in this order, three per page.
- `id`: unique, lowercase, dashes. Required.
- `title`: shown under the thumbnail. Required.
- `storeUrl`: must start with `https://`. Opens in the Play Store app. Required.
- `thumbnail`: optional file name in this folder (a path relative to `games.json`). A game without one, or whose image fails to load, shows a title tile instead.

The app drops any entry with a missing `id` or `title`, or a `storeUrl` that is not `https`. Keep the file valid JSON: if it cannot be parsed, the app keeps showing its last good copy or its bundled list.

## Thumbnails

Put the image in this folder, next to `games.json`, and name it in the entry's `thumbnail`.

- Landscape, 1024x500 pixels, PNG or WebP.
- Under 200 KB.
- No text that is not part of the artwork itself. The app draws the title under the image.

## Adding a game

1. Add the thumbnail file to this folder.
2. Add an entry to `games` in `games.json` (the Play Store link is `https://play.google.com/store/apps/details?id=<package id>`).
3. Check the file parses, for example `python -c "import json;json.load(open('games.json'))"`.
4. Commit and push. The apps pick it up the next time the page opens.
