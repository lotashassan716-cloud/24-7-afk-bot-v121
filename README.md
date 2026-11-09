# Bot_1 ... Bot_5 - builder bots for the Enderlørd server

5 bots that build fun things and make the server beautiful: houses, a big community hall, parks, gardens, gates,
stone-slab paths, lamps, walls, furnished homes, mazes, parkour courses, stepped pyramids, campfire spots and a giant
ENDERLORD sign wall. Made by Enderlørd - Discord: https://discord.gg/kkfg4MM8

## Run
1. `settings.json` -> `server` (ip / port / version)  [already set to ENDERLORD121.aternos.me:47235]
2. `.env` -> `GEMINI_API_KEY=...` (see `.env.example`)
3. `npm install` then `npm start`  (starts all 5 bots, 25s apart so Aternos does not throttle them)
- Bots and roles live in `bots.json`. Dashboards: Bot_1 = port 5000, Bot_2 = 5001, Bot_3 = 5002, Bot_4 = 5003, Bot_5 = 5004.
- `http://localhost:5000/missions` shows the shared mission board and everything that has been built.
- `npm run start:single` runs just one bot (set `BOT_NAME=Bot_1` and `BOT_ROLE=builder` yourself).

## Roles (`bots.json`)
- Bot_1 builder: houses, community hall, gates, furnishing, parks
- Bot_2 decorator: parks, gardens, slab paths, lamps, campfire spots
- Bot_3 engineer: walls, lamps, furnishing, halls, gates, houses
- Bot_4 and Bot_5 creator: mazes, parkour, pyramids, the giant sign wall, campfires, parks, gardens

## Keeps the server pretty
- Bots never dig or chop inside `player.protectRadius` (default 40) of the village or near any building.
- They only chop real trees (with leaves) and mine natural stone, and replant saplings. Paths are slabs placed on top of
  the grass, nothing is dug up.

## How it works
Each bot first chops wood, crafts tools, builds its own house and mines stone. After that it takes missions from a
shared board (`shared/village.json`), never builds on top of another bot's work, and signs its buildings
("ENDERLØRD ..."). It also fights mobs, eats, sleeps at night and answers chat with Gemini when someone says its name
(e.g. "bot 2 kemon acho?"). Players can say `bot 1 help me`, `bot 2 build`, `bot 3 kath ano`, `bot 1 thamo`, `bot 2 free`.

## Settings you may want to change (`settings.json` -> `player`)
`baseName` (name on signs), `missions.everyMinutes`, `maxHouses`, `trusted` (who can command the bots), `skinCommand`.
Never upload `.env` to GitHub.

## Creative mode (new)
Put the bots in creative (`/gamemode creative Bot_1` ... `Bot_5`). They detect it automatically (`player.creativeMode`: "auto" | true | false).
In creative the bots do NOT chop, mine or craft: they take blocks straight from the creative menu and only build.
Extra creative-only missions: `modernhouse` (glass + concrete, 1-2 floors) and `tower` (3-6 floor glass skyscraper).
Caps are higher in creative so the village grows into a city; raise `player.maxHouses` for an even bigger one.
