# Venus Extracurriculars: Mini-games beta

**An unofficial beta by morrowkiln.** This is the [Venus Extracurriculars](https://github.com/venus-extracurriculars/build)
community build with one addition: a mini-games framework and four packs of games, played inside
a scene with the girls who are there. It is not an official Venus Extracurriculars release, and
it is not made or supported by Venus Dev. Please report problems with it here, not to Venus Dev
and not on the Venus Extracurriculars repository.

## What it adds

- **Mini-games**, the framework: offer a game to one girl or several from the seat in the scene,
  or agree to one in the story; girls suggest games themselves where it fits; the result goes
  back into the scene and her memories. Each game has its own page in **Mods**, with its options.
- **[MK] Card Games**: High-Low, Blackjack, Poker, Cat Pairs.
- **[MK] Arcade & Bar Games**: Air Hockey, PARADISO, Pool, Bowling, Skee-Ball, Hoop Shot,
  Whack-a-Bun, Claw Machine.
- **[MK] Party Games**: Beer Pong, Truth or Dare.
- **[MK] Sports**: Foot Race, Swim Race, Rink Race.

The framework is a mod on its own: the packs are separate mods that need it, and anyone can build
a pack. [`docs/mods/mini-games.md`](docs/mods/mini-games.md) explains how.

## Installing

1. You need the official Venus University **0.4.0** for Windows from
   [itch.io](https://venus-dev.itch.io/venus-university). If Venus Extracurriculars or another mod
   is installed on it, uninstall that first.
2. Back up your saves (`data` in the game's folder).
3. Download `Venus-Extracurriculars-0.1.0-minigames-beta.1-no-exe.zip` from
   [Releases](../../releases), unzip it, run `Install.cmd` and pick the game's folder.
4. To go back, run `Uninstall.cmd` from the same zip.

Every mod, the mini-games included, can be switched on or off from **Mods** on the main menu.

## Reporting a problem

Press **Copy bug report** at the game's table, or on the game's page in **Mods**, and paste it into
an [issue](../../issues) with a few words on what happened. It carries the game, its settings and
how it stood; what was riding on the game is left out.

## Source

`main` is the Venus Extracurriculars `main` merged with the mini-games. The code is under
AGPL-3.0-only ([`LICENSE`](LICENSE)); the game's images, music and characters are © Venus Dev and
are not covered by it ([`LICENSE-ASSETS.md`](LICENSE-ASSETS.md)). Each community mod belongs to
its author.

---

*The Venus Extracurriculars README follows.*

# Venus Extracurriculars

An unofficial, fan-made community build of [Venus University](https://venus-dev.itch.io/venus-university),
Venus Dev's single-player AI-driven dating sim. It brings several community mods into one game,
and each one can be switched on or off from **Mods** on the main menu.

This is not Venus Dev's repository, and he is not responsible for anything in it. Please report
problems with this build to us, not to him. The official game is on itch.io:
**https://venus-dev.itch.io/venus-university**

## Playing

The build installs over the official Windows release of the game: download it from itch first,
then run the installer from this build's release. Uninstalling puts the official game back.
Install over the official game only: uninstall any other mod first.

Every mod in the build is listed on the **Mods** screen with its author, and can be turned on or
off there. The mods' own guides are in [`docs/mods/`](docs/mods/).

## Branches

- `core`: the game from Venus Dev's public repository, plus the mod system, with no mods.
- `mod/<name>`: one mod, built on `core`, looked after by its author.
- `integrate/<name>`: a mod merged with `main`, where conflicts with the other mods are settled.
- `main`: what players get, `core` with every mod.

Each mod belongs to its author. Anyone in the organization can merge, as long as someone other
than the author does. [`MODDING.md`](MODDING.md) explains how a mod plugs in, and how to open a
pull request here rather than on Venus Dev's repository.

## Following the game

`core` follows Venus Dev's public repository, and nothing built on a version of the game goes out
before he has released that version himself.

## Running from source

These steps are Venus Dev's, from his repository; they hold here too.

- Some files are not in the repository. The default characters in `assets/characters` are
  zipped, so their NSFW images can't be previewed on GitHub: every zip unpacks to
  `assets/characters/<id>/`, so from `assets/characters`,
  `for z in *.zip; do unzip -q "$z"; done` (or extract each one in place with your archiver).
  The music tracks (`assets/sound/music`, `assets/sound/ambient_music`) are not included either:
  `assets/sound/README.md` says how to get them.
- `npm run dev` then starts with the backgrounds, the sound effects and the pre-generated
  characters. Character generation should work: the pose manifest and openpose skeletons under
  `assets/pose` are included.
- An external API is required to play. API keys are stored in `data/settings.json`, encrypted at
  rest with Windows DPAPI (Electron's `safeStorage`); where DPAPI is unavailable it falls back to
  storing the key as plain text in the same file.

Requires Node 22.

```
npm ci
npm run typecheck
npm test
npm run build
npm run dev
```

## Licence

- Code is licensed under AGPL-3.0-only, as Venus Dev's is: see `LICENSE`.
- Image, audio and video files are all rights reserved: see `LICENSE-ASSETS.md`.
- If you spot a security issue, please read `SECURITY.md` before reporting it.

## Thanks

To Venus Dev, for the game and for publishing its source.
