<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="media/kagi-icon-dark.png">
    <img src="media/kagi-icon.png" width="128" height="128" alt="Kagi the corgi, Kagi's app icon">
  </picture>
</p>

<h1 align="center">Kagi</h1>

<p align="center">A fast, lightweight database client for SQL, NoSQL and object storage.</p>

<p align="center">
  <a href="https://github.com/apitamr/kagi-releases/releases/latest"><img src="https://img.shields.io/github/v/release/apitamr/kagi-releases?label=latest&color=e8590c" alt="Latest release"></a>
  <a href="https://github.com/apitamr/kagi-releases/releases"><img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fapitamr%2Fkagi-releases%2Fmain%2Fstats%2Fdownloads.json" alt="Downloads"></a>
  <a href="https://snapcraft.io/kagi"><img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fapitamr%2Fkagi-releases%2Fmain%2Fstats%2Fsnap-installs.json" alt="Snap installs"></a>
  <a href="https://github.com/sponsors/apitamr"><img src="https://img.shields.io/badge/sponsor-%E2%99%A5-e8590c" alt="Sponsor Kagi"></a>
</p>

<p align="center">
  <img src="media/kagi-promo.gif" width="720" alt="Kagi in 26 seconds: the ad as a SQL query, every engine in one app, inline editing, autocomplete, the command palette, the schema diagram and 112 themes">
</p>

PostgreSQL, MySQL and MariaDB, SQLite, DuckDB, SQL Server, ClickHouse, CockroachDB, MongoDB, Redis and S3-compatible storage (Amazon S3, Cloudflare R2, MinIO) in one native app, with SSH tunnels, TLS and your passwords kept in the system's keychain.

## Download

| System | Get it | Updates |
| --- | --- | --- |
| **macOS** (Apple silicon) | [![Download the .dmg](https://img.shields.io/badge/download-.dmg-e8590c)](https://github.com/apitamr/kagi-releases/releases/download/v0.5.7/kagi-0.5.7.dmg) | Download the new one from here |
| **Windows** (x64) | [![Download the .msi](https://img.shields.io/badge/download-.msi-e8590c)](https://github.com/apitamr/kagi-releases/releases/download/v0.5.7/kagi-0.5.7-x64.msi) | Kagi installs them |
| **Ubuntu** | `sudo snap install kagi`, or **App Center** | Automatic |
| **Debian, Ubuntu** (.deb) | [![Download the .deb](https://img.shields.io/badge/download-.deb-e8590c)](https://github.com/apitamr/kagi-releases/releases/download/v0.5.7/kagi_0.5.7_amd64.deb) | Software Updater, or Kagi |
| **Arch, Omarchy** | `curl -fsSL https://apitamr.github.io/kagi-releases/arch/setup.sh \| sh` | `pacman -Syu`, or Kagi |
| **Any Linux** (Flatpak) | `flatpak install --user https://apitamr.github.io/kagi-releases/kagi.flatpakref` | `flatpak update`, or Kagi |
| **Any Linux** (AppImage) | [![Download the AppImage](https://img.shields.io/badge/download-AppImage-e8590c)](https://github.com/apitamr/kagi-releases/releases/download/v0.5.7/kagi-0.5.7-x86_64.AppImage) | Kagi installs them |

The Linux downloads above are for Intel and AMD (x86-64). Every Linux package except the Arch one also comes for 64-bit ARM (`arm64`, `aarch64`) on the [release page](https://github.com/apitamr/kagi-releases/releases/latest); the snap, APT and Flatpak repositories pick the right one themselves.

## Install

<details>
<summary><b>macOS</b>: allow it once, as it isn't signed by Apple yet</summary>

1. Open the `.dmg` and drag **Kagi** into **Applications**.
2. Open Kagi. macOS says it can't verify it: click **Done**, not Move to Trash.
3. In **System Settings › Privacy & Security**, under **Security**, click **Open Anyway** next to the message about Kagi, and confirm.

Or, in Terminal, after step 1: `xattr -dr com.apple.quarantine /Applications/Kagi.app`

After each update you may need to allow it again, and macOS asks once more before Kagi reads your saved passwords: click **Always Allow**. (Right-click › Open no longer works for this on macOS 15 and later.)

</details>

<details>
<summary><b>Windows</b>: past SmartScreen, as it isn't code-signed yet</summary>

Run the `.msi`. If **Windows protected your PC** shows, click **More info**, then **Run anyway**. Kagi is then in the Start menu.

</details>

<details>
<summary><b>Ubuntu</b> (Snap Store)</summary>

```sh
sudo snap install kagi
```

or search for Kagi in the App Center. Until the Snap Store connects them by itself, give it the keyring (to save passwords) and your SSH keys (for tunnels); Kagi shows these commands where it needs them:

```sh
sudo snap connect kagi:password-manager-service
sudo snap connect kagi:ssh-keys
```

</details>

<details>
<summary><b>Debian and Ubuntu</b> (.deb)</summary>

```sh
sudo apt install ./kagi_*_amd64.deb
```

or open it in your software centre. It adds Kagi's APT repository, so Software Updater brings new versions.

</details>

<details>
<summary><b>Arch and Omarchy</b></summary>

```sh
curl -fsSL https://apitamr.github.io/kagi-releases/arch/setup.sh | sh
```

It trusts Kagi's signing key, adds the `[kagi]` repository to `/etc/pacman.conf` and installs `kagi-bin`, so `pacman -Syu` (and Omarchy's Update) keep it current. On Omarchy it follows your theme, light or dark.

Optional: `openssh` for SSH tunnels, `postgresql` or `mariadb-clients` for dumps and restores. To remove it: `sudo pacman -R kagi-bin`. Coming to the AUR as `kagi-bin`.

</details>

<details>
<summary><b>Flatpak</b> (any distribution)</summary>

```sh
flatpak install --user https://apitamr.github.io/kagi-releases/kagi.flatpakref
```

or install the release's `.flatpak` file. It updates from Kagi's repository. In its sandbox:

- SSH tunnels work with your SSH agent's keys or a key file you pick; `~/.ssh` isn't reachable.
- Files open and save through the file picker.
- Dumps and restores don't work (no `pg_dump` or `mysqldump` inside); use another package for those.
- Connect to local servers over `localhost`, not Unix sockets.

</details>

<details>
<summary><b>AppImage</b> (any distribution)</summary>

```sh
chmod +x kagi-*-x86_64.AppImage
./kagi-*-x86_64.AppImage
```

It needs FUSE 2: `sudo apt install libfuse2` (`libfuse2t64` on Ubuntu 24.04 and later) or `sudo pacman -S fuse2`.

</details>

## Screenshots

| Running a query | A schema's diagram | Saved connections |
| --- | --- | --- |
| ![Running a query, in the dark theme](screenshots/query-dark.png) | ![A schema's diagram](screenshots/diagram-dark.png) | ![Saved connections](screenshots/connections-dark.png) |

![Browsing a table](screenshots/table-dark.png)

They show made-up sample data, in the dark theme.

## Privacy

Kagi has no telemetry, analytics, crash reporting, usage tracking, ads or account. It connects only to:

- **What you add:** your databases, servers and storage, and the SSH hosts you tunnel through.
- **GitHub, for updates** (Linux and Windows): to see whether a new version is out and to download it. The request carries nothing about you or your data, only what any web request does: your IP address and a `kagi` user agent. Turn it off in **Settings › Updates**. On macOS Kagi doesn't check at all.

Your connections, queries, history and settings stay on your computer, and passwords stay in your system's keychain or keyring, never in Kagi's files. Stores and package managers (the Snap Store, Flatpak, APT) count installs themselves, as they do for every app.

## Sponsor

Kagi is free, and made by one person. If it saves you time, you can support its work on [GitHub Sponsors](https://github.com/sponsors/apitamr): it pays for the Apple and Windows signing certificates that would end the "allow it once" steps above, and for time on new engines and features.

## License

Kagi is free to download and use, at home and at work. It isn't open source: see [LICENSE.txt](LICENSE.txt) for what you may and may not do with it.

This repository holds the builds only; the source is private. Kagi checks its latest release for updates.
