# Pluto Plus SD boot with PetaLinux

Learning project: reproduce the Pluto Plus firmware using PetaLinux, then make
and understand incremental changes.

## Clean baseline

- `docker/`: Ubuntu 18.04 dependency image and Compose configuration.
- `installers/`: local PetaLinux 2019.1 installer, ignored by Git.
- `tools/`: local installed PetaLinux 2019.1 tools, ignored by Git.
- `work/upstream/plutoplus/`: unmodified upstream source, pinned as a Git submodule.

Old projects, exported hardware, generated output, logs, and SD backups were
removed. No upstream patches have been applied and no new build has been run.

## Fetch source on another checkout

```bash
git submodule update --init --recursive
```

The upstream repository wraps ADI firmware, with nested repositories for HDL,
Linux, U-Boot, and Buildroot. Its patches adapt these components to Pluto Plus.
The stock firmware uses Buildroot; our PetaLinux project has not been created.
We will first inspect those patches, then build a PetaLinux configuration from
the board requirements. Keep the upstream checkout unmodified as a reference.

See `docker/README.md` to enter the build environment.
