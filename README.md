# Sablemetrics database

The shared database behind the Sablemetrics apps: Pokémon Champions game data and tournament results, as plain CSV
files (names instead of ids, so they open in any spreadsheet). The apps read it so you don't have to collect it yourself.

Last updated: 2026-11-23

## Using it

Sablemetrics reads this repository on its own: it downloads it the first time it starts, and **Settings › Database ›
Update now** gets the latest after that. Without internet on that computer, download this repository elsewhere
(**Code › Download ZIP**), unzip it, and use **Import a downloaded copy** in the same place. Its tournament data then matches this repository exactly (your own teams, settings and
logs are never touched). The Pokedex app builds and publishes it.

## Files

| File | Rows | What it holds |
| --- | ---: | --- |
| [natures.csv](data/natures.csv) | 25 | Natures and the stats they raise and lower |
| [abilities.csv](data/abilities.csv) | 215 | Abilities and what they do |
| [items.csv](data/items.csv) | 166 | Held items and what they do |
| [moves.csv](data/moves.csv) | 510 | Moves: type, category, power, accuracy, PP, priority, target, effects |
| [pokemon.csv](data/pokemon.csv) | 347 | Pokémon and Megas: types, base stats, Mega stones |
| [pokemon_abilities.csv](data/pokemon_abilities.csv) | 722 | Which abilities each Pokémon can have |
| [learnsets.csv](data/learnsets.csv) | 21,574 | Which moves each Pokémon can learn |
| [formats.csv](data/formats.csv) | 4 | Formats and regulations, with their official dates |
| [format_pokemon.csv](data/format_pokemon.csv) | 939 | The Pokémon legal in each regulation |
| [tournaments.csv](data/tournaments.csv) | 619 | Tournaments: date, region, size, top cut |
| [teams.csv](data/teams.csv) | 28,125 | Each player's result at a tournament: placement, record, opponents' win rates |
| [team_members.csv](data/team_members.csv) | 165,958 | The six Pokémon of each team with item, ability, nature, moves and stat points where known |
| [matches.csv](data/matches.csv) | 59,645 | Round-by-round results: who played whom and who won |
| [mechanics_changes.csv](data/mechanics_changes.csv) | 2 | Balance changes per regulation (a move's accuracy, power or effect chance changing) |
| [legacy_dex.csv](data/legacy_dex.csv) | 1,838 | Pokémon, moves, abilities and items from other games, not available yet (reference only) |
| [legacy_events.csv](data/legacy_events.csv) | 137 | Official events from earlier games (training data for the mechanics models) |
| [legacy_teams/](legacy_teams/) (3 parts) | 59,193 | Team sheets from those events (no player names) |
| [legacy_matches.csv](data/legacy_matches.csv) | 240,109 | Round-by-round results from those events |
| [ranked_snapshots.csv](data/ranked_snapshots.csv) | 4 | In-game ranked ladder snapshots: format, season, date |
| [ranked_pokemon.csv](data/ranked_pokemon.csv) | 1,044 | Each snapshot's Pokémon ranking |
| [ranked_detail.csv](data/ranked_detail.csv) | 42,854 | Each ranked Pokémon's most used moves, items, abilities, natures (with shares) and teammates |
| [ranked_spreads.csv](data/ranked_spreads.csv) | 29,543 | Each ranked Pokémon's most used stat point spreads, with shares |
| [upcoming_events.csv](data/upcoming_events.csv) | 66 | Upcoming official events: name, dates, place |

Every file is UTF-8 CSV with a header row and LF line endings. A large table is split into parts of at most 20 MB
(each with the header row), well under GitHub's limits; `manifest.json` lists every file with its row count, so an app
reads exactly what was published and can tell an incomplete download. Tournaments, teams and events are linked by keys made
from their content (a tournament's format, name and date), so they stay the same from one update to the next.

## Notes

- Tournament results are the players' public results; legacy team sheets carry no player names.
- Images are not included (the apps fetch their own).
- See [THIRD_PARTY_NOTICES.md](data/THIRD_PARTY_NOTICES.md) for the licences of the open-source parts.
