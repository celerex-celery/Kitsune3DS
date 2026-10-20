![Kitsune3DS Emulator](dist/kitsune3ds.svg)

![Current Release](https://img.shields.io/github/v/release/celerex-celery/Kitsune3DS?label=Current%20Release)
![Current Prerelease](https://img.shields.io/github/v/release/celerex-celery/Kitsune3DS?include_prereleases&label=Current%20Prerelease)

![GitHub Downloads](https://img.shields.io/github/downloads/celerex-celery/Kitsune3DS/total?logo=github&label=GitHub%20Downloads)
![Google Play Downloads](https://playbadges.pavi2410.com/badge/downloads?id=io.github.lime3ds.android&pretty&label=Play%20Store%20Downloads)
![Flathub Downloads](https://img.shields.io/flathub/downloads/org.celerex_celery.Kitsune3DS?logo=flathub&label=Flathub%20Downloads)
![CI Build Status](https://github.com/celerex-celery/Kitsune3DS/actions/workflows/build.yml/badge.svg)

**Kitsune3DS** is a free and open-source high level Nintendo 3DS emulator for PC and mobile devices. Our goal is to give 3DS owners a place to enjoy their library of titles with improvements to the original hardware, such as higher resolutions, modern controllers or save states. The emulator also serves as a debugging hub for homebrew developers and as a research and preservation platform for the 3DS ecosystem.

The project continues the legacy of **Citra** and is actively developed by a community of contributors.

*Kitsune3DS is not affiliated with or endorsed by Nintendo.*

# Installation

> [!IMPORTANT]
> **Kitsune3DS is a Windows-only project.** Only 64-bit Windows 10/11 is supported.

### Windows

Kitsune3DS is available as both an installer and a zip archive.

Download the latest release in your preferred format from the [Releases](https://github.com/celerex-celery/Kitsune3DS/releases) page.

If you are unsure of whether you want to use MSVC or MXE, use MXE.

---

# Build instructions

Please refer this repository's [wiki](https://github.com/celerex-celery/Kitsune3DS/wiki/Building-From-Source) for build instructions

# How can I contribute?

### Pull requests

If you want to implement a change and have the technical capability to do so, we would be happy to accept your contributions.

If you are contributing a new feature, it is highly suggested that you first make a Feature Request issue to discuss the addition before writing any code. This is to ensure that your time isn't wasted working on a feature which isn't deemed appropriate for the project.

After creating a pull request, please don't repeatedly merge `master` into your branch. A maintainer will update the branch for you if/ when it is appropriate to do so.

### Language translations

Additionally, we are accepting language translations on [Transifex](https://app.transifex.com/azahar/azahar). If you know a non-english language listed on our Transifex page, please feel free to contribute.

> [!NOTE]
> We are not currently accepting new languages for translation. Please do not request for new languages or language variants to be added.

### Compatibility reports

Even if you don't wish to contribute code or translations, you can help the project by reporting game compatibility data to our compatibility list.

To do so, simply read https://github.com/azahar-emu/compatibility-list/blob/master/CONTRIBUTING.md and follow the instructions.

Contributing compatibility data helps more accurately reflect the current capabilities of the emulator, so it would be highly appreciated if you could go through the reporting process after completing a game.

# Minimum requirements

Below are the minimum requirements to run Kitsune3DS:

### Desktop

```
Operating System: Windows 10/11 (64-bit)
CPU: x86-64 CPU (Windows on ARM not supported).
     Single core performance higher than 1,800 on Passmark.
     SSE4.2 required on x86_64.
GPU: OpenGL 4.3 or Vulkan 1.1 support
Memory: 2GB of RAM. 4GB is recommended
```

# What's next?

We share public roadmaps for upcoming releases in the form of GitHub milestones.

You can find these at https://github.com/celerex-celery/Kitsune3DS/milestones.

# Join the conversation

We have a community Discord server where you can chat about the project, keep up to date with the latest announcements, or coordinate emulator development.

Join at https://discord.gg/4ZjMpAp3M6