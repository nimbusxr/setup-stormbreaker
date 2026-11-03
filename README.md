# setup-stormbreaker

Installs [stormbreaker](https://github.com/nimbusxr/stormbreaker), operational acceptance testing
in shared environments, in GitHub Actions on Linux, macOS and Windows, and adds it to `PATH`.

```yaml
- uses: nimbusxr/setup-stormbreaker@v0
  with:
    version: latest   # or a version such as 0.1.0, or nightly
- run: stormbreaker streams lint parcel-lifecycle --root data
```

A suite itself runs on [axx](https://github.com/nimbusxr/axx), which
[setup-axx](https://github.com/nimbusxr/setup-axx) installs. axx builds stormbreaker's packs from
the suite's `axx-packs.yaml`, so a job that only runs a suite doesn't need this action.

| Input | Default | |
| --- | --- | --- |
| `version` | `latest` | A version such as `0.1.0`, `latest` (the newest release, pre-releases included) or `nightly`. |
| `token` | `${{ github.token }}` | The token used to list releases, which avoids API rate limits. |

The installed version is the `version` output. `v0` follows the action's `0.x` releases while
stormbreaker is in beta.

The action downloads the release archive for the runner's OS and architecture from GitHub and
checks it against the release's `checksums.txt`. Every `0.x` release of stormbreaker is a GitHub
pre-release, so `latest` is resolved from the list of releases rather than GitHub's "latest release".

`install.sh` and `install.ps1` are copies of stormbreaker's
[install scripts](https://github.com/nimbusxr/stormbreaker/tree/main/scripts).

## License

Apache-2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
