# Weekly QA Counter v700 full restored

This restores the full feature set on top of the stable no-embedded-query app.

Included:
- current week live table
- T2 Privacy / T2 Privacy Pilot
- Priyank/Parth individual views
- Admin all-data view
- Fail buttons 0 / 1 / 2 / 3+
- Total failed count cards
- Previous week summary
- Vacation / PTO / Sick transfer and return restore
- Assignments, agents, weekly settings
- WTD / MTD / YTD counts
- Better updates without showing the loading screen after every click

Setup:
1. Run supabase-setup-v700.sql in Supabase SQL Editor.
2. Upload all files to a clean GitHub repo.
3. Edit config.js and paste your anon public key.
4. Enable GitHub Pages from branch main / root.
5. Open: https://YOUR-GITHUB-USERNAME.github.io/YOUR-REPO-NAME/?v=700
