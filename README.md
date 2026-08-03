# ListenWell — Releases

Build artifacts for ListenWell: installers for Windows, macOS and Linux, plus the
`latest*.yml` feeds the in-app updater polls.

**There is no source code here.** This repository exists so the update feed can stay
public while the application source is private — a private repository's release
assets are private too, and the updater fetches them anonymously with no token.

Releases are published automatically by the `Desktop release` workflow in the source
repository when a `v*` tag is pushed. Nothing here is meant to be edited by hand.
