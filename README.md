# Uptime Save Editor

A single-file, fully client-side save editor for the game **[Uptime](https://store.steampowered.com/) (data center management sim)**.
Open `uptime_save_editor.html` in any modern browser, drop in a `.save` file, edit it, and download the patched save — no install, no server, no upload of your save file anywhere.

## Features

- **Devices** — bulk-rename hosts, switches, gateways, EDDs, appliances, racks, AZs and regions (apply/strip a name prefix across a selection).
- **Rack View** — visual per-rack elevation of installed devices.
- **Network** — live overview, sparklines, per-device load, top ports by traffic, top ports by errors/link flaps, VRFs & subnets.
- **Customers** — bulk actions: set health to 1.0, clear probation, zero out SLA credits, set `price_multiplier` for a selection.
- **Player** — edit finances & stats.
- **Repair** — one-click fixes: clear active incidents, release maintenance hosts, reset over-temperature, clear SIEM storage, clear churn history & reputation loss, upgrade all host NICs to 25G SFP28.
- **Tuning** — search/filter and edit raw `config.tuning` / `base_config.tuning` values.
- **Statistics** — view lifetime totals (cosmetic, in $).
- Bilingual UI (English/German), light/dark theme.
- Reads and writes the save name shown on the in-game load screen via the matching `meta.json`.

## How it works

Uptime's `.save` files are [MessagePack](https://msgpack.org/)-encoded, prefixed with a `CSIM` magic header. This tool includes its own small MessagePack decoder/encoder written in plain JavaScript, so it can parse the save into an editable in-memory structure and re-serialize it back to bytes on download — all in the browser, nothing is sent over the network.

## Usage

1. Open `uptime_save_editor.html` in Chrome, Edge, or Firefox.
2. Drag your `.save` file onto the drop zone (usually found under your Uptime save folder), or click to browse for it.
3. If prompted, also load the matching `meta.json` so the save name shown in-game stays correct.
4. Make your edits across the tabs.
5. Click **Download patched .save** and replace the original save file with the downloaded one.

**Back up your save before editing it.** This tool writes a modified save file; a malformed edit could make the save fail to load.

## Requirements

None beyond a modern browser — the file is fully self-contained (HTML, CSS and JS in one file, no external dependencies, no build step).
