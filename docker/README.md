# PetaLinux Docker environment

Run from this directory:

```bash
sudo docker compose run --rm petalinux
```

Inside the container:

```bash
source /tools/petalinux-2019.1/settings.sh
cd /work/upstream/plutoplus
```

Compose mounts repository-local `installers/`, `tools/`, and `work/` at
`/installers`, `/tools`, and `/work`. Installer binaries and installed tools are
ignored by Git. The Docker image provides host dependencies, not PetaLinux.
On a fresh machine, supply the installer separately and install PetaLinux into
`/tools/petalinux-2019.1` inside the container.

Build the dependency image with `sudo docker compose build` if needed. Optional
`.env` builder IDs are documented in `.env.example`.

The old manually started container has obsolete saved host mount paths. Use
Compose for new containers. Docker access currently requires sudo on this host.
