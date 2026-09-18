# 🦀 KING CRAB RESTAURANT SIMULATOR

An extremely serious supply chain experience. Catch a crab in Alaska, truck it to
Richmond, put it in a tank, boil it, serve it, retire.

**Play it:** https://thepotatoturtle.github.io/king-crab-restaurant/

About two minutes. One crab. Plenty of ways to lose it.

Any failure sends you back to the boat in Alaska and restarts the whole chain --
there is no scene-by-scene retry.

## Controls

Mouse and left click. That's the whole game.

| Scene | What to do |
|---|---|
| **Alaska** | Steer the boat with the mouse, **hold left click** to lower the pot. Catch the one wearing a crown — everything else costs you $300 and precious time. **15 seconds of daylight**; the sky darkens as it runs out and nightfall ends the run. |
| **The Haul** | **Left click** to hop potholes, moose and geese. Each bonk costs **20% freshness** — five crashes and the crab is a smoothie. |
| **The Tank** | **Click and drag** the crab out of the bucket and into the tank. Freshness drains fast — a full bar gives you **10 seconds**. Drop the crab and it scuttles off, costing cash and seconds you don't have. |
| **The Kitchen** | Drag the crab into the pot, then **hold left click** to keep the flame on. Release in the green band — **raw or burnt ends the run**. |
| **Service** | Drag the plate to the customer. **Dropping it ends the run.** |
| **Payday** | Sit back. |

`M` mutes the sound. Career earnings are saved in your browser.

## Running it locally

It's one self-contained `index.html` with no dependencies or build step — open the
file in a browser and it works. To serve it properly:

```bash
python -m http.server 8765
```

## How the art works

Every graphic is drawn procedurally on a `<canvas>` — there are no image assets.
Shapes are traced as polylines, subdivided, and offset by a noise function that
reseeds 15 times a second, which gives the lines their constant boil. Fills are
deliberately drawn a few pixels off from their outlines so everything looks like it
was coloured in by someone in a hurry.

The wobble is scale-aware (`WSC`), so a crab drawn at 3x doesn't get 3x the wobble.
It is also keyed to each point's offset from its own shape's origin rather than to
world position, so a shape that moves across the screen keeps its wobble instead of
re-rolling it every frame. Fill offsets use a separate static noise function
(`nzf`) so the colour sits still while only the outline boils.

### Dialling the wobble

Three numbers near the top of the script:

| | what it does | calmer | wilder |
|---|---|---|---|
| `WOBRATE` | seconds between reseeds of the line boil | `0.3` | `0.1` |
| `WOB` | line wobble amplitude in px | `1.0` | `2.5` |
| `cap` in `shape()` | how far fills sit off their outlines | `2.0` | `5.0` |

`WOBRATE` is in seconds, not frames, so the boil looks identical at 60Hz and 240Hz.

## Layout

- `index.html` — the entire game
- `SPEC.md` — the design spec it was built from
- `.claude/launch.json` — local dev server config
