# HORUS Releases

This repository is the public, binary-only update channel for the HORUS macOS
application. It contains signed update metadata and generic application builds.

It does **not** contain studio images, captions, search indexes, project folders,
team tokens, contributor information, server configuration, or private source
material. Team archive data remains on the separately authenticated HORUS server.

HORUS uses [Sparkle](https://sparkle-project.org/) to verify and install releases
from `appcast.xml`. The application archive is signed with Sparkle's EdDSA key;
the corresponding private key is not stored in this repository.

Production releases are created by the manually dispatched **Release Pool
macOS** workflow. It reads Pool source through a short-lived, read-only GitHub
App token, builds on an ephemeral Apple Silicon runner, runs the test suite,
signs and notarizes the application, and updates this repository only after the
production environment is approved. Signing credentials are protected GitHub
environment secrets and are never available to the Pool source repository or
included in an artifact.


The workflow defaults to `validate`: it builds and checks Developer ID signing,
Apple notarization, and the Sparkle signature without publishing an update.
Choose `publish` only for an intentional public release. Source must be a
commit on Pool main, and the workflow itself must run from this repository’s
main branch. Published binaries are never overwritten; interrupted feed updates
can be retried only with the original identical ZIP and checksum.

The protected environment is `pool-production`. Its one-time credential and
reviewer setup is documented in the private Pool repository at
`desktop/RELEASE_HANDOFF.md`. The private source repository’s independent
**Check Mac release** workflow tests unsigned packaging without signing secrets.
