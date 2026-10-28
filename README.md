# Demo mixes

Serve this directory with any static web server. The root `index.html` lists
active MP3s; `archive/index.html` lists archived MP3s. Both pages use the same
native browser audio controls and shared stylesheet, with separate URLs at
`/` and `/archive/` relative to the site's base path. WAV files are not listed.

Audio files use Git LFS. Run `git lfs pull` before serving a checkout, and ensure
your hosting deployment includes the actual audio files rather than LFS pointer
files. A GitHub Pages Actions checkout must enable `lfs: true`.

When adding or moving an MP3, update the corresponding page's track list. Keep
audio sources relative to that page and URL-encode spaces and special characters.
