# HORUS Releases

This repository is the public, binary-only update channel for the HORUS macOS
application. It contains signed update metadata and generic application builds.

It does **not** contain studio images, captions, search indexes, project folders,
team tokens, contributor information, server configuration, or private source
material. Team archive data remains on the separately authenticated HORUS server.

HORUS uses [Sparkle](https://sparkle-project.org/) to verify and install releases
from `appcast.xml`. The application archive is signed with Sparkle's EdDSA key;
the corresponding private key is not stored in this repository.

