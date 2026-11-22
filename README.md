# Flight Path Collector

A community addon for [Polestar](https://polestar.guide), the guide addon for
World of Warcraft: Forever. It walks you to every flight path you are still
missing, on both continents, for the Horde and for the Alliance. It is a
separate addon by creazy231; it is not made or supported by Polestar.

## What it does

- **Only the ones you miss.** Polestar knows which flight paths your
  character has, so every flight path you already know is passed over and
  the guide starts at the first one missing. Stop whenever you like: next
  time it picks up where you are.
- **Every flight path of your faction**: 34 for the Horde, 35 for the
  Alliance, the neutral ones (Ratchet, Marshal's Refuge) included, and WoW
  Forever's new ones in Mount Hyjal and the Riverglades.
- **Low levels first.** Each continent goes from the cities and starting
  zones out to the level 60 zones, and every step says the zone's levels.
  When the zones get too dangerous for your character, stop and come back
  with a few more levels.
- **Polestar plans the trip.** The arrow uses the flights you already know,
  the boats, the zeppelins and the Deeprun Tram to get you to the next one.

## The guides

In Polestar's guide menu (`/polestar guides`), under **Community guides** >
**Flight Path Collector**, folder **Flight paths**:

| Guide | Flight paths |
|---|---|
| Flight Paths: Kalimdor (Horde) | 21, Orgrimmar to Mount Hyjal |
| Flight Paths: Eastern Kingdoms (Horde) | 13, Undercity to Light's Hope Chapel |
| Flight Paths: Eastern Kingdoms (Alliance) | 17, Stormwind to Light's Hope Chapel |
| Flight Paths: Kalimdor (Alliance) | 18, Rut'theran Village to Mount Hyjal |

Each guide covers one continent and stands on its own, so start with either:
an Undead character, for example, can begin with the Eastern Kingdoms guide.
The last step of each points to the other continent's guide.

**Import strings:** the addon's page on polestar.guide also offers each guide
as an import string for Polestar's Import page (`/polestar import`), and
every one imports on its own. With the addon installed you don't need them:
Polestar refuses a string for a guide the addon already has.

## WoW Forever's new flight paths

Mount Hyjal (Tainted Foothills and Summit of Eternity, both factions) and the
Riverglades (Rog'mar for the Horde, Farholde Keep for the Alliance) are WoW
Forever's own. Polestar knows them since version 0.4.0: those steps tick
themselves when the flight master's map opens, like every other one. With an
older Polestar, **tick those steps off yourself** once you have the flight
path.

Not in the guides: the druid-only flights in Moonglade, which are no flight
paths you learn, and Powderfuse Port and Tidegear Coast, which the game's
files list but which have no flight master in the world yet.

## Getting there safely

- Every step names its zone's levels. Feralas, Azshara, Felwood, Un'Goro,
  Silithus, Winterspring, Mount Hyjal, the Burning Steppes and the
  Plaguelands are level 45 to 60 zones.
- Moonglade, Everlook and Mount Hyjal are reached through the furbolg
  tunnels of Timbermaw Hold, whose furbolgs attack until your standing with
  Timbermaw Hold reaches Unfriendly. At level 60 you can run straight through.
- Horde and Alliance towns sit side by side in several zones: give the other
  faction's guards a wide berth.

## Install

- **Polestar Client:** open **Community**, find **Flight Path Collector** and
  press **Install**.
- **By hand:** unzip the release into the game's `Interface/AddOns/` folder,
  next to the `Polestar` folders, so that
  `Interface/AddOns/PolestarPack_flight-path-collector` exists.

Restart the game the first time (a `/reload` does not load a new addon).
**Options > Community guides** (`/polestar packs`) turns the addon on or off.

## Problems and ideas

Report a wrong or missing flight path to creazy231 on the addon's page on
polestar.guide, not to Polestar. When Forever opens a new flight path, it
goes into the next version.

Credits: creazy231. Licence: CC-BY-4.0 (see `LICENSE`).

## For authors

The addon is built from this folder: `pack.json` and the four `.guide` files
in `guides/`, in Polestar's guide format. With a Polestar clone (Node 24+,
LuaJIT, its `forge` built and its reference data built), from this folder:

- `forge guide lint`: checks the guides against the game's data.
- `polestar playtest`: plays every guide to the end.
- `polestar install --pack . --dest <AddOns folder>`: copies it into the game.
- `forge release pack`: writes the release zip to `dist/`.

With Polestar 0.4.0's reference data, `forge guide lint` gives no errors and
no warnings (older data lacks WoW Forever's four flight points and warns once
for each of the six steps that use them). The guides have no `next` line on
purpose: an import string may only lead on to a guide the player has already
imported, so a `next` between these guides would make the first one's string
fail on its own. Raise `version` in `pack.json` for every release, and a
guide's `version` when its steps or texts change, so that players who
imported its string get Update.
