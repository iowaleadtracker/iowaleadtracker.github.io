# iowaleadtracker.github.io

A mirror of **[iowaleadtracker.com](https://iowaleadtracker.com/)**, the canonical site,
at **https://iowaleadtracker.github.io/**.

It exists for readers who can't reach iowaleadtracker.com, for example on networks that
block Cloudflare. If the main site loads for you, use it.

This repository holds only the build workflow. The model, the saved weather forecasts,
every assumption and the site build are in
[iowaleadtracker/iowaleadtracker](https://github.com/iowaleadtracker/iowaleadtracker); open
issues and corrections there.

## How it's built

[`.github/workflows/mirror.yml`](.github/workflows/mirror.yml) checks out the source
repository's `main`, runs `make_map_picker.py --build --mirror`, and publishes the result
with GitHub Pages:

- when started by hand or by the maintainer's deploy (`make_map_picker.py --deploy`),
- and hourly, but only when `main` has a new commit (`build.txt` on the mirror records the
  commit it was built from).

Both sites are built from the same commit and the same saved forecasts, replayed as of
when they were pulled, so they show the same maps. A build that would need to download
weather fails instead of publishing a different map.

The mirror adds a notice naming the main site, keeps `rel=canonical` pointing at
iowaleadtracker.com, and carries the site's security policy in a `<meta>` tag because
GitHub Pages can't send custom headers. GitHub Pages sees visitors' IP addresses; the
mirror doesn't count visits.

This is an unofficial estimate, not from the Army or any government agency. Don't use it
to decide if you're safe.
