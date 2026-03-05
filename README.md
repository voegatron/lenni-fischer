# Fischer-Abenteuer 🎣
### De Lenni gaht go fische!

Ein Angel-Spiel für Lenni — läuft im Browser, mobilfreundlich, als einzelne Website auf jedem FTP hostbar.

---

## Ordnerstruktur

```
fishing-game/
├── index.html
├── style.css
└── static/
    ├── avatar.png              ← Lennis Profilbild (HUD oben links)
    ├── boat.png                ← Boot-Sprite (ersetzt das gezeichnete Boot komplett)
    └── fish/                   ← Fisch-Bilder (alle optional, Emoji als Fallback)
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
        ├── golden_koi.png
        └── mola_mola.png
```

## Bilder

- **boat.png** — Ersetzt das gesamte Boot + Charakter. Die Angelleine startet
  an der oberen rechten Ecke des Bildes (dort sollte die Rutenspitze sein).
  PNG mit transparentem Hintergrund empfohlen.
- **avatar.png** — Profilbild im HUD oben links neben dem Namen. Optional.
- **Fisch-Bilder** — Jedes einzelne ist optional. Ohne Bild wird das Emoji
  angezeigt. Empfohlene Grösse: 128×128 oder 256×256 PNG, transparenter Hintergrund.

---

## Spielablauf

1. **WERFEN** — Angel auswerfen, Haken sinkt ins Wasser
2. **WARTEN...** — Haken sinkt auf zufällige Tiefe, warten auf einen Biss
3. **BISS!** — Fisch beisst an! Schnell tippen um zu reagieren (3 Sek. Zeit)
4. **EINHOLEN!** — Mehrmals tippen um den Fisch hochzuziehen
5. **Fang!** — Popup zeigt Fisch, Gewicht, Seltenheit und Münzen

Wenn man zu langsam reagiert: *"Der Fisch ist entkommen!"*

---

## Spielstand

- **Auto-Save:** Spielstand wird nach jedem gefangenen Fisch automatisch
  in `localStorage` gespeichert
- **Weiterspielen:** Beim nächsten Besuch erscheint ein grüner
  "Weiterspielen"-Button mit Spielstand-Übersicht
- **Neues Spiel:** Startet frisch — fragt vorher nach, ob der alte
  Spielstand wirklich gelöscht werden soll

Gespeichert werden: Münzen, Level, EP, gefangene Fische, Bestgewichte, max. Tiefe.

---

## Levelsystem

- **EP (Erfahrungspunkte):** Jeder Fisch gibt EP. Seltene Fische geben mehr.
- **EP pro Level:** Startet bei 100, steigt um 30% pro Level
  (`100 × 1.3^(Level-1)`)
- **Max. Tiefe:** Startet bei 30, steigt um +5 pro Level.
  Tiefere Gewässer = seltenere Fische möglich.

### Seltenheits-Boost pro Level

Je höher das Level, desto wahrscheinlicher seltene Fische:

| Seltenheit   | Basis-Gewicht | Boost pro Level      |
|--------------|---------------|----------------------|
| Häufig       | 45            | —                    |
| Ungewöhnlich | 30            | —                    |
| Selten       | 16            | × (1 + Level × 0.05)|
| Episch       | 7             | × rb × 1.2          |
| Legendär     | 2             | × rb × 1.5          |
| Mythisch     | 0.3           | × rb × 2.0          |

*rb = 1 + Level × 0.05*

Beispiel Level 10: rb = 1.5 → Legendäre Fische sind 125% wahrscheinlicher.

---

## Fische (21 Arten)

### Häufig
| Fisch         | Gewicht     | Münzen | Min. Tiefe | EP  |
|---------------|-------------|--------|------------|-----|
| Sonnenfisch   | 0.2–2 kg    | 5      | 0          | 10  |
| Barsch        | 0.3–3 kg    | 8      | 0          | 12  |
| Wels          | 1–8 kg      | 12     | 0          | 15  |
| Schwarzbarsch | 1–10 kg     | 15     | 0          | 18  |

### Ungewöhnlich
| Fisch    | Gewicht   | Münzen | Min. Tiefe | EP  |
|----------|-----------|--------|------------|-----|
| Forelle  | 1–12 kg   | 25     | 10         | 25  |
| Lachs    | 3–15 kg   | 30     | 15         | 30  |
| Hecht    | 2–20 kg   | 35     | 15         | 32  |
| Karpfen  | 2–25 kg   | 28     | 10         | 28  |

### Selten
| Fisch        | Gewicht    | Münzen | Min. Tiefe | EP  |
|--------------|------------|--------|------------|-----|
| Rotbarsch    | 3–20 kg    | 50     | 25         | 45  |
| Thunfisch    | 10–80 kg   | 65     | 30         | 55  |
| Schwertfisch | 15–120 kg  | 80     | 35         | 60  |
| Barrakuda    | 5–40 kg    | 70     | 30         | 50  |
| Goldmakrele  | 5–30 kg    | 60     | 25         | 48  |

### Episch
| Fisch              | Gewicht    | Münzen | Min. Tiefe | EP  |
|--------------------|------------|--------|------------|-----|
| Marlin             | 50–250 kg  | 150    | 45         | 80  |
| Riesenzackenbarsch | 30–180 kg  | 120    | 40         | 75  |
| Muräne             | 5–30 kg    | 100    | 40         | 70  |
| Anglerfisch        | 10–50 kg   | 130    | 50         | 85  |

### Legendär
| Fisch        | Gewicht      | Münzen | Min. Tiefe | EP  |
|--------------|--------------|--------|------------|-----|
| Walhai       | 500–2000 kg  | 500    | 60         | 200 |
| Riesenkalmar | 100–600 kg   | 400    | 65         | 180 |
| Goldener Koi | 2–8 kg       | 1000   | 50         | 250 |

### ✨ Mythisch
| Fisch     | Gewicht      | Münzen | Min. Tiefe | EP  |
|-----------|--------------|--------|------------|-----|
| Mola Mola | 200–2300 kg  | 2500   | 75         | 500 |

*Mola Mola ist erst ab Level 10 möglich (Tiefe 75+ benötigt) und extrem selten!*

---

## Technisches

- Einzelne `index.html` + `style.css` — auf jedem kostenlosen FTP hostbar
- Reine HTML5 Canvas + Vanilla JS, keine Frameworks
- Responsiv: funktioniert auf Handy und Desktop
- Touch-optimiert: kein Doppel-Tap-Zoom
- Bilder sind alle optional (graceful fallback auf Emojis)
- Spielstand via `localStorage` (bleibt im gleichen Browser erhalten)
