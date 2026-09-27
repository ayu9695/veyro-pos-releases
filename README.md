# Veyro POS releases

The update feed for the Veyro POS desktop till. It holds installers and
nothing else: no source, no configuration, no credentials.

Each release carries three files, and a till needs all three:

| file | what it is for |
| --- | --- |
| `Veyro-POS-Setup-<version>.exe` | the installer |
| `latest.yml` | what a till reads to discover that a new version exists |
| `Veyro-POS-Setup-<version>.exe.blockmap` | lets a till download only the parts that changed |

**This repository is public on purpose.** A till downloads its updates
anonymously, so pointing electron-updater at a private repository would mean
baking a credential into every installer that ships. The product source lives
in a private repository; only the built installer belongs here, and an
installer contains no secrets — the one value baked into it is the production
server URL, which is public by definition.

Releases are normally published by `publish-desktop.yml` in the source
repository, which waits until production is actually serving the commit the
installer was built from before it hands anything to the fleet.
