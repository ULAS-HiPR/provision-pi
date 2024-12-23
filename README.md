# provision 🥧

[![CI](https://github.com/ULAS-HiPR/provision-pi/actions/workflows/build.yml/badge.svg)](https://github.com/ULAS-HiPR/provision-pi/actions/workflows/build.yml)

This is a forked flake for provisioning CanSats with Raspberry Pi boards.
It provides a minimal NixOS setup that boots headlessly with SSH and Wi-Fi.

For usage, build the sd-image:

```shell
nix build '.#nixosConfigurations.mach25.config.system.build.sdImage' --extra-experimental-features "nix-command flakes"
```

> Note: You might see warnings about `system.stateVersion` and `services.openssh.permitRootLogin`. These can be safely ignored.

Then write the image to an SD card:

```shell
dd if=result/sd-image/nixos-sd-image-21.11pre-git-aarch64-linux.img of=/dev/sdX bs=4M status=progress
```

Replace `/dev/sdX` with the correct device path.

