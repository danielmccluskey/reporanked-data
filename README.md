# reporanked-data
Data Combinations for RepoRanked to allow others to contribute things such as enemy combinations for different ELO brackets.

## Enemy Combinations Data

This file contains the predefined enemy combinations used in **REPORanked** to ensure fairness and reduce RNG variance during gameplay.

### Format
***as of writing this, only difficulty 1 is used at the moment***

The data is structured as a JSON object in the following format:
```json
{
  "1": [
    {
      "Enemy - Gnome Director": 1,
      "Enemy - Gnome": 15
    },
    {
      "Enemy - Ceiling Eye": 10
    }
  ],
  "2": [
    {
      "Enemy - Gnome Director": 2,
      "Enemy - Gnome": 10
    }
  ],
  "3": [],
  "4": []
}
```
- **Top-level keys (`"1"`, `"2"`, etc.)** represent difficulty levels, the server chooses these based on ELO of both players.
- Each value is a **list of possible enemy combinations** for that difficulty.
- Each combination is a dictionary of **enemy names and their counts**.

### Purpose

This system is used to:

- Maintain **competitive integrity** in REPORanked matches.
- Avoid extreme RNG scenarios (e.g., spawning 6 Headmen on difficulty 2).
- Ensure all players face **the same challenges** when seeded into the same match.

### Notes

- This file is intended to be read by the game logic to spawn enemies deterministically based on difficulty and seed.
- Avoid manual edits unless you know what you're doing, invalid entries may break enemy generation.


## Map Pool Data

This file defines the list of available maps used in **REPORanked**. One of these maps is selected at random for each match, independent of difficulty level.

### Format

The data is a simple JSON array of strings, e.g.:
```json
[
  "Manor",
  "Arctic",
  "Wizard"
]
```
### Purpose

Hosting this list here allows me to easily add/remove maps from rotation without having to maintain a database table.

### Notes

- The selection is **random**, but drawn from this list only.
- This file should be maintained alongside other static game data files.
- Avoid using maps not included in the base game (Don't use museum map on the beta test).
