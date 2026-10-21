# Kagi releases

Builds of Kagi, a compact database client for PostgreSQL, MySQL/MariaDB, SQLite, DuckDB, SQL Server, ClickHouse, MongoDB and Redis.

Download the file for your system from the [latest release](https://github.com/apitamr/kagi-releases/releases/latest), then follow its section below.

| System | File | Updates |
| --- | --- | --- |
| macOS (Apple Silicon) | `kagi-<version>.dmg` | Download the new version when Kagi says there is one |
| Windows (x64) | `kagi-<version>-x64.msi` | Installs them itself |
| Linux, any distribution | `kagi-<version>-x86_64.AppImage` | Installs them itself |
| Linux, any distribution (Flatpak) | `kagi-<version>-x86_64.flatpak` | Download the new version when Kagi says there is one |
| Debian, Ubuntu | `kagi_<version>_amd64.deb` | Download the new version when Kagi says there is one |
| Arch, Omarchy | `kagi-<version>-x86_64.tar.gz` and `PKGBUILD` | Download the new version when Kagi says there is one |

## macOS

Kagi isn't signed with an Apple Developer ID yet, so macOS can't check it and blocks it the first time. You allow it once:

1. Open the `.dmg` and drag **Kagi** into **Applications**.
2. Open Kagi. macOS says it can't verify it: click **Done**, not Move to Trash.
3. Open **System Settings › Privacy & Security**, scroll to **Security**, and click **Open Anyway** next to the message about Kagi. Confirm with your password or Touch ID.
4. Kagi opens, and from now on it opens like any other app.

Or, in Terminal, after step 1:

```sh
xattr -dr com.apple.quarantine /Applications/Kagi.app
```

**After each update**, macOS treats the new copy as a different app until Kagi is signed:

- You may need to allow it again as above.
- macOS asks once more before Kagi can read each saved password from your keychain. Click **Always Allow**.

Right-clicking the app and choosing Open no longer gets past this on macOS 15 and later; use Privacy & Security.

## Windows

The installer isn't code-signed yet, so Windows SmartScreen may stop it.

1. Run the `.msi`. If **Windows protected your PC** shows, click **More info**, then **Run anyway**.
2. Follow the installer. Kagi is in the Start menu.

Kagi checks for updates and installs them itself.

## Linux

### AppImage (any distribution)

```sh
chmod +x kagi-*-x86_64.AppImage
./kagi-*-x86_64.AppImage
```

AppImages need FUSE 2. If it doesn't start, install it: `sudo pacman -S fuse2` on Arch, `sudo apt install libfuse2` on Debian and Ubuntu (`libfuse2t64` on Ubuntu 24.04 and later).

Kagi checks for updates and installs them itself.

### Flatpak (any distribution)

```sh
flatpak install --user kagi-*-x86_64.flatpak
flatpak run io.github.apitamr.kagi_releases.Kagi
```

It fetches the runtime from Flathub if you don't have it. Inside Flatpak's sandbox:

- SSH tunnels work, as `ssh` comes with it, signing with your SSH agent's keys or a key file you pick; `~/.ssh` (its config and known hosts) is out of its reach.
- It opens and saves files (SQLite and DuckDB databases, `.sql` files, exports) through the file picker; a path typed by hand isn't reachable.
- Dumping and restoring don't, as `pg_dump`, `mysqldump` and the others aren't in the sandbox. Use another package for those.
- Connect to local servers over TCP (`localhost`), not their Unix sockets.
- Its saved connections are kept apart from another install's, in `~/.var/app/io.github.apitamr.kagi_releases.Kagi`.

### Debian and Ubuntu

```sh
sudo apt install ./kagi_*_amd64.deb
```

### Arch and Omarchy

Download the release's tarball and `PKGBUILD` into one folder, then in that folder:

```sh
makepkg -si
```

For SSH tunnels Kagi uses `ssh` (`openssh`); for dumps and restores, `pg_dump` and `psql` (`postgresql`) or `mysqldump` and `mysql` (`mariadb-clients`).

Kagi then shows in your app launcher. On Omarchy it follows your theme, light or dark, unless you turn that off in its Settings.

It is coming to the AUR as `kagi-bin`, for `yay -S kagi-bin` and Omarchy's **Install › AUR**.

To remove it: `sudo pacman -R kagi-bin`.

## About this repository

It holds the builds only; the source is private. Kagi checks this repository's latest release for updates.
