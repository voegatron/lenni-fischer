# Reel Adventure - File Structure

Upload this entire folder to your FTP host.

```
fishing-game/
├── index.html
└── static/
    ├── avatar.png              ← Player photo (shown in HUD, optional)
    ├── boat.png                ← Boat + character sprite (replaces drawn boat!)
    └── fish/                   ← Custom fish images (all optional)
        ├── sunfish.png
        ├── perch.png
        ├── catfish.png
        ├── bass.png
        ├── trout.png
        ├── salmon.png
        ├── pike.png
        ├── carp.png
        ├── red_snapper.png
        ├── tuna.png
        ├── swordfish.png
        ├── barracuda.png
        ├── mahi_mahi.png
        ├── marlin.png
        ├── giant_grouper.png
        ├── moray_eel.png
        ├── anglerfish.png
        ├── whale_shark.png
        ├── giant_squid.png
        └── golden_koi.png
```

## How It Works

- **boat.png** — This replaces the ENTIRE drawn boat and character in the game.
  Use an image that includes both the character and the boat (like a cartoon
  of your godchild sitting in a boat). It floats on the waves and the fishing
  line extends from the right side. PNG with transparent background recommended.
  If no boat.png is found, the game draws a default pixel boat.

- **avatar.png** — Shown in the top-left HUD corner next to the player name.
  Good for a headshot/profile pic. Optional.

- **fish images** — Each one is optional. If missing, the emoji fallback is used.
  Recommended: 128x128 or 256x256 PNG with transparent background.

## Fish by Rarity

| Rarity    | Fish                                                |
|-----------|-----------------------------------------------------|
| Common    | Sunfish, Perch, Catfish, Bass                       |
| Uncommon  | Trout, Salmon, Pike, Carp                           |
| Rare      | Red Snapper, Tuna, Swordfish, Barracuda, Mahi Mahi  |
| Epic      | Marlin, Giant Grouper, Moray Eel, Anglerfish        |
| Legendary | Whale Shark, Giant Squid, Golden Koi                |
