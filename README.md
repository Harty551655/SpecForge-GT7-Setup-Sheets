SpecForge GT7

A free, single-page tool that generates a starting tuning sheet for any car in Gran Turismo 7. Pick your car, tell it which parts you have installed, choose a track and layout, add a PP limit if the race has one, describe any problems you have driving it, and get a printable setup sheet.

Unofficial fan project. Not affiliated with, endorsed by, or sponsored by Polyphony Digital or Sony Interactive Entertainment. Gran Turismo and related names and marks belong to their respective owners.

Live app: [Open SpecForge GT7](https://harty551655.github.io/SpecForge-GT7-Setup-Sheets/)

---

## What it does

- **Car picker:** choose by manufacturer or by category (Gr.1, 2, 3, 4, B, N, X). Drivetrain, power, weight and base PP fill in automatically.
- **Parts list:** tick what you have installed (suspension, LSD, transmission, ECU, adjustable downforce, brake balance controller, ballast, power restrictor, tyres, plus engine and drivetrain upgrades). Settings your car cannot adjust show as locked, with the part you would need.
- **Track and layout:** pick the track, then the layout. Each layout is tagged fast, mixed or technical, which drives the downforce, gearing, ride height and toe values.
- **PP limit:** enter a max PP and the sheet shows how much PP the car has left to spend, or how far over the limit it already is, with ways to get under it.
- **Problem notes:** type things like "understeers in slow corners", "rear locks under braking" or "bouncy over kerbs" and the settings adjust to suit. The sheet lists what it changed and why.
- **Setup sheet:** suspension, aerodynamics, differential, transmission, brakes, ballast and power. Copy it as text or print it or save it as a PDF.
- **Aero scale:** downforce is shown from -50% (slider minimum) to +50% (slider maximum), with 0% in the middle. A built-in calculator turns those percentages into the actual numbers once you enter each slider's MIN and MAX.
- **Differentials:** choose whether your customizable LSD is on the front, the rear, or both. The sheet shows separate front and rear settings when needed.

> The numbers are **starting points** based on general tuning rules of thumb, not an official GT7 formula and not tested lap times. Drive a few laps and change one thing at a time.

---

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app: page, styles, car list, tuning logic and your logo, all in one file |
| `README.md` | This file |
| `SpecForge-Car-Entry.xlsx` | Optional spreadsheet that builds car lines for you (see below) |

There is nothing to install and no build step. Open `index.html` in a browser to run it.

---

## Customising the app (colours, fonts, title, logo)

Everything you may want to change lives near the top of the `<script>` section in `index.html`, so you never have to touch the tuning logic.

1. **Search for `SECTION 1: COLOURS`.** There are two palettes, `light` and `dark`. Change the hex codes and save. Each colour is labelled:

   | Key | Used for |
   |---|---|
   | `ac` | Main accent: buttons, highlights |
   | `ac2` | Secondary accent: sheet section headings |
   | `bg` | Page background |
   | `card` | Panels and cards |
   | `tx` | Main text |
   | `mu` | Muted grey text |
   | `bd` | Borders and lines |
   | `in` | Dropdown and input backgrounds |
   | `ok` | Success or good notices |
   | `wn` | Warning or attention notices |
   | `on` | Text on top of accent-coloured buttons |

2. **Search for `SECTION 2: OTHER SETTINGS`.** The `DEFAULT_THEME` block controls:

   | Setting | What it does |
   |---|---|
   | `mode` | `auto` (follows the visitor's device), `light` or `dark` |
   | `title1`, `title2` | The heading. The second part uses the accent colour |
   | `tagline` | The line under the heading |
   | `hf`, `bf` | Heading and body fonts (the list is in the comment above the block) |
   | `fs`, `r`, `mw` | Text size, corner roundness and page width in pixels |
   | `logo`, `sheetLogo` | Header logo and sheet logo. Use `'logo.png'` for a file next to `index.html`, or a `data:image/...` string |
   | `watermark`, `wmOpacity` | Faint logo behind the app and the sheet (`true`/`false`, opacity 0.02 to 0.15) |
   | `team`, `note` | A name and a footer note printed on every sheet |
   | `wu`, `su` | Weight unit (`kg` or `lb`) and speed unit (`km/h` or `mph`) |
   | `hints` | Show or hide the grey hints column on the sheet |

Visitors cannot change any of these. Only someone who can edit the file can.

---

## Adding cars

The car list is the block that starts with `const RAW=` in `index.html`. One car per line:

```
Name|Category|Drive|Power|Weight|PP|Manufacturer
```

Example:

```
Corvette C7 ZR1 '19|N|FR|754|1615|634|Chevrolet
```

- **Category:** just the code without "Gr.": `N`, `4`, `3`, `2`, `1`, `B` or `X`.
- **Drive:** `FR`, `MR`, `RR`, `FF` or `4WD` (anything else is treated as 4WD).
- **Power and weight:** numbers only (BHP and kg). Use `0` if the game shows "-". The app then uses a default weight and shows "?" for power.
- **PP:** the car's base PP as a whole number.
- **Manufacturer:** spell it the same every time (for example always `Alfa Romeo`), because it builds the manufacturer dropdown.
- Blank lines are ignored. Older lines that sit under a `#Manufacturer` header with no manufacturer on the end also still work.

### Using the spreadsheet

`SpecForge-Car-Entry.xlsx` builds the lines for you:

- **Add Cars:** type one car per row using the dropdowns.
- **Paste Game List:** paste your whole game table (Model, Manufacturer, Category, PP, Drive, Power, Weight) in that column order. It converts text like "133 BHP / 5,500 rpm" and "1,035 kg" into plain numbers.

Copy the grey **Code line** column, paste it into the `RAW` block, save, and upload the file again. The **Check** column flags anything missing or wrong.

---

### Updating later

Upload a new `index.html` with the same name (**Add file**, then **Upload files**) and commit. The live site updates in a minute or two. If you do not see the change, do a hard refresh in your browser.

---

## Good to know

- **Works anywhere:** it runs entirely in the browser, with no server and no account.
- **Fonts:** most heading and body fonts load from Google Fonts, so they need an internet connection. The app falls back to your system font otherwise.
- **Claude-only extras:** if the app is opened on its original claude.ai link, editors see an "Admin: add cars for everyone" box that shares cars with all viewers live. That box does not appear on GitHub Pages. On GitHub Pages, cars are added by editing the `RAW` block and uploading the file again.
- **Printing:** use **Print / Save PDF** on the generated sheet. The page, buttons and footer are hidden when printing, and the logo watermark prints faintly behind the sheet.
- **Accuracy:** car stats come from the game's published figures at the time of entry and may change with game updates. Always check the values in the tuning menu in game.

---

## Credits

Built for the Gran Turismo 7 community.

Logo and branding: SpecForge.
