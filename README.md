# Weekly QA Counter v800 - Interactive

Built on top of v700 (full restored feature set). Same data, same tables,
no destructive changes - this adds four things on top:

- **Weekly trend chart** - a line chart (Chart.js) of completed totals per
  QA member over the last 12 weeks. Admins see every QA as a separate line;
  QAs see just their own.
- **Fail-rate history** - a table ranking agents by how often they've had a
  fail count of 1+ over the last 12 weeks, so you can spot chronically
  failing agents instead of only seeing this week's snapshot.
- **Target streaks + confetti** - a "consecutive completed weeks" streak per
  QA, and a confetti burst the moment an agent's row flips to Done.
- **Dark mode** - a sun/moon button in the header, saved in the browser
  (localStorage), applies instantly.

Nothing about logins, roles, admin controls, leave/PTO, assignments, or
history was changed - all existing v700 behavior still works the same way.

Config is already filled in with your Supabase project
(`gvporifcjbenmhuewzqb.supabase.co`) and anon key, so you should not need to
edit `config.js` unless you're pointing this at a different Supabase project.

## How many weeks the new analytics look back

Open `app.js` and find this near the top:

```js
const ANALYTICS_WEEKS = 12;
```

Change `12` to whatever lookback you want (e.g. `26` for ~6 months). No SQL
changes needed either way.

## Setup

1. **Supabase SQL**: only needed if this is a brand-new Supabase project, or
   you're not sure the v700 tables already exist. Open your Supabase
   project -> SQL Editor -> paste in `supabase-setup-v700.sql` -> Run. It's
   written to be safe to re-run (every table/insert is guarded with
   `if not exists` / `where not exists`), so running it again on a project
   that already has this schema is harmless and won't duplicate data.
   If you already ran this for v700 on this same project, you can skip this
   step entirely.
2. Upload all files (`index.html`, `styles.css`, `app.js`, `config.js`,
   `supabase-setup-v700.sql`) to your GitHub repo, replacing the old ones.
3. Enable GitHub Pages: Settings -> Pages -> Source: Deploy from a branch ->
   Branch: `main` / root.
4. Open: `https://YOUR-GITHUB-USERNAME.github.io/YOUR-REPO-NAME/?v=800`
