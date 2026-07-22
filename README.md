[README.md](https://github.com/user-attachments/files/30273853/README.md)
# The League Ledger — Setup & Workflow

A single-page fantasy football league site: home standings, a beer mile
leaderboard, season rules, and 16 weekly recap tabs. No backend — it reads
`data.json` for anyone visiting, and saves your edits to your browser's
local storage until you export and publish them.

## One-time setup

1. **Rename the HTML file.**
   `fantasy-league-github.html` → `index.html`

2. **Create a GitHub repo** (if you don't have one yet) and add both files
   to the root:
   - `index.html`
   - `data.json`

3. **Enable GitHub Pages.**
   In the repo: **Settings → Pages → Build and deployment → Source** →
   select **Deploy from a branch**, pick your default branch (usually
   `main`) and the `/ (root)` folder → **Save**.

4. **Find your live URL.** GitHub shows it on that same Pages settings
   screen once it's built, usually:
   `https://<your-username>.github.io/<repo-name>/`
   First deploy can take a minute or two.

5. **Set your passphrase.** Open `index.html` in a text editor, find this
   line near the top of the `<script>` section:
   ```js
   const EDIT_PASSPHRASE = 'commissioner';
   ```
   Change `'commissioner'` to something only you know, save, and re-commit.

## Making edits (every time you update the league)

1. Go to your live GitHub Pages URL.
2. Click **🔒 Commissioner login** (top right), enter your passphrase.
3. Edit anything — scores, recaps, rules, beer miles. It autosaves to
   your browser as you go. The status line under the title will say
   *"Local draft has unexported changes"* while you have unpublished
   edits.
4. When you're ready to publish, click **⬇ Export JSON**. This downloads
   a fresh `data.json`.
5. Replace the `data.json` in your repo with the one you just downloaded.
6. Commit and push.
7. GitHub Pages redeploys automatically (usually under a minute). Refresh
   the live site to confirm your changes are there.

That's it — anyone who visits the URL, on any device, now sees the update.

## The other buttons

- **↻ Refresh** — re-checks `data.json` for a newer published version.
  Useful if you just pushed an update and want to confirm it went live,
  or if you're a visitor and think the page might be stale.
- **⬆ Import JSON** — loads a `data.json` file back in as your working
  draft. Useful if you want to keep editing something you already
  published, or you're picking up editing on a different browser/machine
  and want to start from the current published state instead of empty.
- **↺ Reset to published** — throws away your local draft and reloads
  straight from `data.json`. Click once to arm it, click again within a
  few seconds to confirm. Use this if your local draft and the published
  file have drifted apart and you'd rather just start clean.

## Things worth knowing

- **Only you can edit; everyone can view.** The commissioner lock is a
  courtesy gate, not real security — someone determined could bypass it
  via their browser's dev tools. The actual protection is that only you
  have push access to the repo.
- **Your local draft lives only in one browser, on one machine.** It's
  not backed up anywhere until you export it. If you clear your browser
  data, or edit from a different computer, that draft is gone — treat
  Export as your real save point, not autosave.
- **It's not live-sync.** Updates only appear for other people after you
  export → commit → push → Pages redeploys. Expect roughly a minute of
  lag, not instant.
- **Team names must match exactly across weeks** for the standings table
  to tally correctly (e.g. "Mud Hens" and "The Mud Hens" would be treated
  as two different teams).
