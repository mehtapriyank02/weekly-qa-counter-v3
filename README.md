# Weekly QA Counter v900 - Redesigned

Same features and data as v800 (trend chart, fail-rate history, streaks +
confetti, dark mode, plus everything from v700: leave/PTO, assignments,
agents, settings, history, admin/QA roles). This pass is purely visual/UX -
no Supabase queries, tables, or admin/QA logic changed.

Built using the `ui-ux-pro-max` design skill, matched to this app's product
type ("Productivity / internal ops tool") and applied its recommendations:

- **Style**: Flat Design + Soft UI Evolution hybrid - clean cards, soft
  layered shadows, 8-12px corner radius, WCAG AA+ contrast targets.
- **Palette**: Teal primary (`#0D9488`) + orange accent (`#EA580C`), the
  skill's curated "Productivity Tool" palette. Dark mode is a proper
  desaturated dark-teal variant (not just inverted colors), with its own
  contrast pass.
- **Typography**: Inter for both headings and body (the skill's "Minimal
  Swiss" pairing, recommended specifically for dashboards/admin panels/
  enterprise apps), with tabular figures on every numeric column so digits
  don't jitter when counts change.
- **Icons**: replaced every emoji (theme toggle, streak flame, trend/fail
  panel headers, stat cards) with a small hand-built inline SVG icon set -
  the skill explicitly flags emoji-as-icons as an anti-pattern.
- **Motion**: 150-300ms micro-interactions on buttons/cards, a staggered
  row entrance on the main table, everything respects
  `prefers-reduced-motion`.
- **Accessibility fixes**: visible focus rings on every interactive element
  (previously missing), aria-labels on the icon-only theme button, and
  larger touch targets on the +/- and fail-selector buttons on touch
  devices (they stay compact on mouse/desktop via a `pointer: fine` media
  query) - the +/- buttons were under the 44px minimum touch target before.
- **Charts**: trend lines differentiate QA members by color, per the
  skill's colorblind-safety guidance for multi-series line charts.

Nothing about logins, roles, admin controls, leave/PTO, assignments, or
history changed - all v700/v800 behavior works exactly the same, just looks
and feels more polished.

Config is already filled in with your Supabase project
(`gvporifcjbenmhuewzqb.supabase.co`) and anon key, so you should not need to
edit `config.js` unless you're pointing this at a different Supabase project.

## How many weeks the analytics look back

Open `app.js` and find this near the top:

```js
const ANALYTICS_WEEKS = 12;
```

Change `12` to whatever lookback you want (e.g. `26` for ~6 months). No SQL
changes needed either way.

## Setup

1. **Supabase SQL**: only needed if this is a brand-new Supabase project, or
   you're not sure the tables already exist. Open your Supabase project ->
   SQL Editor -> paste in `supabase-setup-v700.sql` -> Run. It's written to
   be safe to re-run (every table/insert is guarded with `if not exists` /
   `where not exists`), so running it again on a project that already has
   this schema is harmless and won't duplicate data. If you already ran
   this for v700/v800 on this same project, skip this step entirely.
2. Upload all files (`index.html`, `styles.css`, `app.js`, `config.js`,
   `supabase-setup-v700.sql`) to your GitHub repo, replacing the old ones.
3. Enable GitHub Pages: Settings -> Pages -> Source: Deploy from a branch ->
   Branch: `main` / root.
4. Open: `https://YOUR-GITHUB-USERNAME.github.io/YOUR-REPO-NAME/?v=900`
