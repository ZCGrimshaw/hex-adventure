# Hex Adventure

Single-file game: everything lives in `index.html`. Hosted on GitHub Pages at
https://zcgrimshaw.github.io/hex-adventure/ (zerocrunch.ca/hex-adventure is a redirect page on the main site).
Online Hall of Greats uses the `harvestworks` Supabase project: table `hx_runs`, RPCs `hx_start`, `hx_finish`, `hx_board`.

## Releasing an update
1. Bump `const BUILD = N` in `index.html`.
2. Set `"build": N` in `version.json`, with a one-line player-facing `notes`.
3. Commit and push to `main`. Open games notice within ~2.5 minutes and offer "Save & update".

## Never break saves
Runs autosave to IndexedDB (`hexworld3` / `kv` / `run`) until the 5th skull. Any new field on `P`, `S` or `stats`
must get a default in `migrate()` so older saves keep loading. Do not rename or remove saved fields.
