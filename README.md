# Nvestigation

A one-page timeline built by Jekyll on GitHub Pages and served at nvestigation.com.
Everything that changes regularly lives in the `_data` folder.

Opening `index.html` on your own computer shows template code such as `{% for ... %}`.
That is normal: GitHub builds the finished page, so check changes on the live site.

## Files

| File | What it controls |
| --- | --- |
| `_data/timeline.yml` | The main timeline, newest first |
| `_data/background.yml` | "Before the story broke", the earlier part of the timeline |
| `_data/sources.yml` | The source list and its numbering |
| `_data/status.yml` | The "Who runs Nvidia" panel and the "Last updated" date |
| `index.html` | Layout, styling, the summary at the top and the About section |
| `CNAME` | The custom domain. Leave it in place. |

## Add a timeline entry

Open `_data/timeline.yml` on GitHub, click the pencil, and paste a block at the top:

```yaml
- date: 2026-11-12
  headline: "Huang agrees to brief Congress"
  points:
    - tag: record
      text: "He accepts the 18 November closed-door session."
      sources: [house-request]
```

- `tag` is `record` (on the record), `reported` (unnamed sources, not proven) or `denied`.
- `sources` are ids from `_data/sources.yml`. Add new sources at the bottom of that file
  so the existing numbers stay the same.
- Keep text inside double quotes, and keep the indentation exactly as shown (spaces, not tabs).
- For a date range, add a line such as `label: "5–6 November 2026"` under `date`.
- Then update `updated:` in `_data/status.yml` so the "Last updated" date moves on.

Commit, and the site rebuilds in about a minute.

## Edit the summary or the About section

Both are plain text in `index.html`. The summary is the paragraph with `class="lede"`;
the About placeholders are the paragraphs with `class="placeholder"`. Replace a
placeholder with `<p>Your text.</p>` (dropping `class="placeholder"`) to remove the dashed box.

## If a change does not show up

A typo in a `.yml` file stops the build, and the site keeps showing the last good
version. The repository's **Actions** tab shows the failed build and the line it tripped on.
