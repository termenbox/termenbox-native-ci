# Termenbox native builds

This repo builds and publishes the optional Termenbox apps for Windows, Linux and Android from a named commit of the
(private) product source. The web client at [app.termenbox.dev](https://app.termenbox.dev) is the reference client; the
apps are optional and add nothing the browser cannot do.

## Downloads

See the [Releases](../../releases) of this repo. Each Release names the source commit it was built from and lists the
SHA-256 of every file.

| Platform | File | Signature |
|---|---|---|
| Linux | `.AppImage` | detached GPG signature `.AppImage.asc`, key in `termenbox-native.asc` |
| Android | `.apk` | signed with the Termenbox upload key; verify with `apksigner verify --print-certs` |
| Windows | `.exe` installer | **not yet signed**: Windows shows an "unknown publisher" warning. Check the SHA-256 against the Release text. |

There is no self-updater: download a newer Release to update.

## How a build runs

A person starts the `build` workflow by hand with a source commit. Nothing builds from a pull request or a fork. The
workflow reads the source with a GitHub App limited to reading that one repo, builds on GitHub-hosted runners with no
signing material, and then a final job in the protected `stable` Environment signs and publishes after an owner approves.

## License

See `LICENSE` and the third-party notices shipped inside each app.
