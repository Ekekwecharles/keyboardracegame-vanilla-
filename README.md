# REDLINE // Type Racer

A browser-based typing speed racing game where your WPM and accuracy control how fast your car moves down the track. Race against bots, level up, unlock cars, and challenge friends in real-time multiplayer, all in a single HTML file with a neon "asphalt" racing aesthetic.

This repo contains two versions of the game:

| File              | Description                                                                                                                                                                                                                             |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `index.html`      | The original, lightweight version. Single race screen, one difficulty selector, two bots, live WPM/accuracy/combo gauges.                                                                                                               |
| `secondgame.html` | The expanded version. Adds a tabbed interface (Race, Garage, Multiplayer, Profile), player levels and XP, unlockable cars, achievements/badges, race history, custom difficulty settings, and local multiplayer via `BroadcastChannel`. |

Both are fully self-contained, there is no build step, no server, and no dependencies beyond Google Fonts (Orbitron and JetBrains Mono) loaded over CDN.

## How to run

Just open either file directly in a browser.

```bash
# clone the repo
git clone <your-repo-url>
cd <repo-folder>

# open in your default browser
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

You can also serve them with any static file server, or double-click the file in your file explorer.

## How to play

1. Click anywhere on the page to focus the typing field.
2. Start typing the highlighted text. Correct characters turn cyan and push your car forward; mistakes turn red and reset your combo.
3. Use backspace to fix mistakes, you can't cross the finish line with uncorrected errors still typed.
4. Beat the bots to the finish line to win the race.

### `index.html`

- Choose a difficulty (Easy / Mid / Hard) to change text length.
- Race against two fixed-pace bots.
- Live gauges show WPM, accuracy, and combo.
- Speeds above 55 WPM trigger a visual "boost" effect.

### `secondgame.html`

- **Race tab**: same core racing loop, plus a mistake penalty (characters typed count against your progress).
- **Garage tab**: unlock and select different vehicles (bike, hatchback, muscle car, supercar, hypercar) as you level up.
- **Multiplayer tab**: create or join a room by code (or shared link) and race friends in real time using `BroadcastChannel` (same-browser/tab based, no backend required).
- **Profile tab**: tracks level, XP, races played/won, best WPM, average accuracy, race history, and earned achievements (First Race, First Win, 60+ WPM, 90+ WPM, Perfect run, Combo streaks, 10 Races, Level 5, etc.).
- Adjustable difficulty presets (Rookie / Pro / Legend) or a fully custom bot speed and mistake-penalty setup.

## Tech

- Plain HTML, CSS, and vanilla JavaScript, no frameworks or build tools.
- `localStorage` for persisting profile, XP, unlocks, and race history in `secondgame.html`.
- `BroadcastChannel` API for peer-to-peer style multiplayer within the same browser.
- CSS custom properties for the neon color theme (violet, cyan, pink, amber).

## Project structure

```
.
├── index.html        # original single-race version
├── secondgame.html    # full-featured version with garage, multiplayer, and profile
└── README.md
```

## Notes

- Multiplayer in `secondgame.html` relies on `BroadcastChannel`, which only synchronizes across tabs/windows in the same browser profile. For true cross-device multiplayer you'd need to swap this out for a real-time backend (e.g. WebSockets or a service like Pusher).
- No external JS libraries are used, everything (word generation, WPM/accuracy calculation, race animation) is hand-rolled.

## License

Add your preferred license here (MIT, for example) if you plan to make this public.
