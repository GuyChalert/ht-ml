# ht-ml

Machine-learning engine and models for reading drill-core tray photos in the
HammerTales field app (Android): core outline, breaks, rubble, core loss, scale and
depth marks. The app ships with a model and, on Wi-Fi, checks this repo for a newer one.

**Status: empty. Nothing is built yet.** The plan lives in the app repo
(`FINDINGS.md` §1152, `CORE_PHOTO_PLAN.md` §8).

## Planned layout

| Path | What |
|---|---|
| `engine/` | training code (runs on GitHub Actions) |
| `models/vNNN/` | one trained version: thresholds, classifier weights, `.tflite`, `scores.json` |
| `manifest.json` | the version the app should use, with SHA-256 and a signature |
| `SCOREBOARD.md` | every training run, kept or not, and why |
| `data/` | contributed training rows (cleared data only, see below) |

## Rules

- **Models are signed.** The app refuses any model whose signature or SHA-256 does not
  match. The signing key is never stored in this repo.
- **A new model ships only if it scores better** than the current one on a private test
  set that is never trained on.
- **Contributions come by pull request** and are reviewed before merging. Training reads
  merged data only.
- **Only cleared data.** Send core photos only if the owner of the site or client has
  agreed to their publication. Strip EXIF (GPS, dates) and site names from file names.
- **Contributed data is licensed CC BY 4.0** (https://creativecommons.org/licenses/by/4.0/).
  By opening a pull request with data you agree to that licence.

## Licences

- **Code** (`engine/` and everything that is not data): MIT, see `LICENSE`.
- **Contributed data** (`data/`): CC BY 4.0, see above.
