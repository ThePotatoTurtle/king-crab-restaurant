# 🦀 KING CRAB RESTAURANT SIMULATOR

An extremely serious supply chain experience. Catch a crab in Alaska, truck it to
Vancouver, put it in a tank, boil it, serve it, retire.

**Play it:** https://thepotatoturtle.github.io/king-crab-restaurant/

About two minutes. One crab. No way to lose, only ways to be embarrassed.

## Controls

Mouse and left click. That's the whole game.

| Scene | What to do |
|---|---|
| **Alaska** | Move the mouse to steer the boat. **Hold left click** to lower the pot. Catch the one wearing a crown — everything else costs you money. |
| **The Haul** | **Left click** to hop potholes, moose and geese. Bonking the truck sloshes the crab and drops its freshness. |
| **The Tank** | **Click and drag** the crab into the tank. Drop it and it will scuttle off and say something hurtful. |
| **The Kitchen** | Drag the crab into the pot, then **hold left click** to keep the flame on. Release in the green band. |
| **Service** | Drag the plate to the customer. Don't drop the plate. |
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

## Layout

- `index.html` — the entire game
- `SPEC.md` — the design spec it was built from
- `.claude/launch.json` — local dev server config
