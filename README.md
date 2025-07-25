# BlueBuild Template &nbsp; [![bluebuild build badge](https://github.com/joshmock/blue-build-hyprland/actions/workflows/build.yml/badge.svg)](https://github.com/joshmock/blue-build-hyprland/actions/workflows/build.yml)

A [BlueBuild](https://blue-build.org/) image based on [wayblue](https://github.com/wayblueorg/wayblue)'s Hyprland images, and customized based on how I set up my development laptop.
See the [BlueBuild docs](https://blue-build.org/how-to/generate-iso/) to generate an ISO from this image.

## Missing bits so far

Most of these will be installed in [Distrobox](https://distrobox.it/) containers, unless they need access to the host kernel to do their job.

- interception-caps2esc
- mopidy+gstreamer
- noti
- mimeo
- xdg-utils-mimeo
- jless
- lazygit
- traceroute
- calc
- difftastic
- git-extras
- gh
- glances
- yq
- htop
- jq
- strace
- tree-sitter
- vault
- wget
- whois
- zeal-git
- neovim-remote
- git-annex
- rclone
- autorestic
- restic
- yt-dlp
- aerc
- gmailctl
- lynx
- msmtp
- mutt-wizard
- neomutt
- notmuch
- task
- taskopen
- timew
- bugwarrior
- nnn
- pass

## Installation

> [!WARNING]
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:

  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/joshmock/joshmock-hyprland:latest
  ```

- Reboot to complete the rebase:

  ```
  systemctl reboot
  ```

- Then rebase to the signed image, like so:

  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/joshmock/joshmock-hyprland:latest
  ```

- Reboot again to complete the installation

  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If built on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/joshmock/joshmock-hyprland:latest
```
