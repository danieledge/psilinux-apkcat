# psilinux-apkcat

Alpine Linux's package catalogue (v3.24, main and community, armhf) as small
static files, for `apk` on [PsiLinux](https://github.com/danieledge/psilinux)
(Linux on a Psion Series 5mx, which has too little memory to load Alpine's
whole index).

This repository only publishes the catalogue. Every day a GitHub Actions
workflow (`.github/workflows/apkcat.yml`) reads Alpine's index, runs
`tools/apkcat/mkapkcat.py` and, when the index has changed, publishes the
result to this repository's GitHub Pages:

    https://danieledge.github.io/psilinux-apkcat/apk/v3.24/armhf/stats

The packages themselves still come from Alpine's own mirror, and the Psion's
`apk` checks them against Alpine's signing keys.

The generator, its tests and the Psion's `apk` wrapper live in psilinux's
`dev` branch (`tools/apkcat/`, `alpine/overlay/usr/local/sbin/apk`). Change
the generator there, then copy `mkapkcat.py` here. It lives in its own
repository because GitHub runs scheduled workflows only from a default
branch.
