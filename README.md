# DeAstroStacker-ci

Build runner for DeAstroStacker. No application source lives here.

GitHub bills Actions minutes to the repository a workflow runs in, and standard
runners are free on a public repository. This one checks the application out of
its own private repository with a read-only token, builds it, and leaves the
result as a workflow artifact.

Two legs: Linux x86_64 (`.tar.gz`) and macOS Apple Silicon (`.dmg`).

Manual trigger only, from the Actions tab or:

    gh workflow run build.yml -R MichaelLevAstro/DeAstroStacker-ci -f ref=main

Artifacts are kept for fourteen days.

## Setup

One secret, `SOURCE_TOKEN`: a fine-grained personal access token limited to the
DeAstroStacker repository with `Contents: Read` and nothing else. Fine-grained
tokens expire, and an expired one shows up as a checkout failure rather than
anything more helpful.
