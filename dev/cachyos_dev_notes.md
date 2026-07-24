# CachyOS Developer & Gaming Notes

Practical considerations for running CachyOS as a dev/gaming machine.

---

## Rolling Release Mindset

- Fedora is stable/predictable; CachyOS updates constantly. Test before committing to major changes.
- Keep a working snapshot/backup—rollbacks are possible but tedious.
- `sudo pacman -Syu` regularly; long gaps between updates can break things.

---

## Multilib (32-bit Support)

- Ensure `[multilib]` is enabled in `/etc/pacman.conf`—essential for Wine/gaming.
- Check: `sudo pacman -S lib32-glibc` should work without errors.

---

## AUR & yay

- AUR packages auto-build; some are stale or unmaintained. Check last update date before installing.
- Security: review PKGBUILDs before running `yay -S` on sensitive stuff.
- Consider binaries for heavy builds (e.g., `aseprite`, `unity-hub`) to save compile time.

---

## Kernel Tuning

- CachyOS ships with optimized kernels (CachyOS, Bore, RT variants).
- Default is fine for gaming/dev; only switch if you have specific needs.
- Check current: `uname -r`

---

## GPU (AMD 6600)

- Mesa is included; AMDVLK optional but usually unnecessary.
- ROCm (compute) is separate from graphics drivers—install only if needed for compute.
- Test Vulkan: `vulkaninfo | head -20` should work out of box.

---

## Package Conflicts

- Arch is stricter about deps than Fedora. If pacman warns about conflicts, don't force (`--force`); find the actual issue.
- Use `pacman -S package1 package2` together if interdependent.

---

## Orphaned Packages

- Clean periodically: `sudo pacman -Rns $(pacman -Qtdq)` (removes orphaned deps).
- Keeps system lean.

---

## KDE Plasma Config

- Settings sync better on Arch/KDE combo than Fedora.
- Config path: `~/.config/kde*`
- No major gotchas; Plasma 6.x is stable.

---

## Lazarus/Free Pascal

- Available via pacman: `sudo pacman -S lazarus fpc`
- AUR has newer snapshots if needed.
- Should compile & debug fine; no Wine layer needed.

---

## Wine for NWN:EE

- Arch wine is bleeding-edge; occasionally breaks older games.
- Keep `~/.wine_nwnee` backup; can rollback wine if needed: `sudo pacman -U /var/cache/pacman/pkg/wine-*.pkg.tar.zst`
- Lutris handles prefixes cleanly anyway.

---

## Community

- Arch/CachyOS community is smaller/terse than Fedora's—wiki is your lifeline.
- Arch wiki >> most distro docs; bookmark it.

---

## Dual Boot Gotcha

- If also booting Windows: CachyOS/GRUB plays nicely with it, but verify boot order in BIOS after install.
- EFI vars occasionally reset; not a blocker, just aware.

---

## Summary

CachyOS is snappier & more cutting-edge than Fedora, but less forgiving. Keep backups, check AUR before installing, enable multilib, monitor `pacman -Syu` output. For your use case (NWN, Lazarus, gaming), it's solid. The only real risk is a borked update mid-workflow—mitigate with snapshots.

---

## Quick Reference

```bash
# Update everything
sudo pacman -Syu

# Check multilib support
sudo pacman -S lib32-glibc

# Clean orphaned packages
sudo pacman -Rns $(pacman -Qtdq)

# Install Lazarus + FPC
sudo pacman -S lazarus fpc

# Rollback wine if needed
sudo pacman -U /var/cache/pacman/pkg/wine-*.pkg.tar.zst

# Check kernel
uname -r

# Test Vulkan
vulkaninfo | head -20
```
