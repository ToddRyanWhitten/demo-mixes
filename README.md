# Demo mixes

## GitHub Pages

Once Pages is enabled and the deployment succeeds, listen at:

- Active tracks: https://ToddRyanWhitten.github.io/demo-mixes/
- Archive tracks: https://ToddRyanWhitten.github.io/demo-mixes/archive/

To enable public hosting:

1. In [Settings > General](https://github.com/ToddRyanWhitten/demo-mixes/settings),
   use **Danger Zone > Change repository visibility** to make the repository public.
   This exposes the repository's files and history, not just the published site.
2. In [Settings > Pages](https://github.com/ToddRyanWhitten/demo-mixes/settings/pages),
   select **GitHub Actions** as the build and deployment source.
3. Merge the deployment workflow into `main`, or run **Deploy GitHub Pages**
   manually if it is already merged.

The published site is public; do not deploy tracks that should remain private.

The **Deploy GitHub Pages** workflow deploys on pushes to `main` and can also be run
manually from the **Actions** tab after Pages is enabled. It downloads Git LFS
content and publishes only the HTML pages, stylesheet, and MP3 files; WAV files
and repository tooling are excluded.

Keep **Deploy GitHub Pages** as the only Pages deployment workflow. A separate
Jekyll deployment without Git LFS checkout can overwrite the working site with
pointer files: the controls appear, but the audio will not play. The workflow
checks for these pointers and stops rather than publishing broken audio.

## Local playback and track updates

Serve this directory with any static web server. The root `index.html` lists
active MP3s; `archive/index.html` lists archived MP3s. Both pages use the same
native browser audio controls and shared stylesheet, with separate URLs at
`/` and `/archive/` relative to the site's base path. WAV files are not listed.

Audio files use Git LFS. Run `git lfs pull` before serving a checkout, and ensure
your hosting deployment includes the actual audio files rather than LFS pointer
files. The Pages workflow already enables `lfs: true` during checkout.

When adding or moving an MP3, update the corresponding page's track list. Keep
audio sources relative to that page and URL-encode spaces and special characters.
