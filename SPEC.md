# KING CRAB RESTAURANT SIMULATOR — spec

A dumb little browser game. One crab, one supply chain, one obscene payday.

## Constraints
- Single self-contained `index.html`. No build step, no dependencies, no assets.
- All art drawn procedurally on `<canvas>`: thick wobbly black outlines, flat fills,
  colouring offset outside the lines. Lines re-jitter 5x/sec ("boiling" squigglevision),
  on a time-based clock so the boil looks the same at any refresh rate.
  Font: Comic Sans MS.
- Controls: mouse move, hold/release left click, drag. `M` mutes (sfx + music). Nothing else.
- Soundtrack: two loops synthesised from note data, one picked at random per load.
  No audio files anywhere in the project.
- ~2 minutes start to finish. Real fail states: any failure restarts the entire
  chain from the boat in Alaska, never from the scene that was failed.
- Hosted on GitHub Pages.

## The chain (6 scenes)

| # | Scene | Verb | Control | Cost of failure |
|---|-------|------|---------|-----------------|
| 0 | TITLE | click | click | — |
| 1 | ALASKA | catch the king crab | mouse X steers boat, HOLD to lower the pot | junk: −$300 and lost seconds. **15s daylight clock → RESTART** |
| 2 | THE HAUL | drive to Richmond (19.2s) | click to hop potholes & moose | bonk: **−20% freshness**. **0% → RESTART** |
| 3 | THE TANK | bucket into tank | drag | drop it: −$200 and lost seconds. **15s freshness clock → RESTART** |
| 4 | THE KITCHEN | boil it | HOLD to keep the flame on, release in the green | **RAW or CHARCOAL → RESTART** |
| 5 | SERVICE | serve the plate | drag to the table | **smash the plate → RESTART** |
| 6 | PAYDAY | exist | click | — |

Every RESTART returns to scene 1. The ALASKA clock doubles as a day/night cycle:
the sky ramps morning → sunset → night across its 15 seconds.

## Money
```
gross = 47,000 (one (1) crab, market price)
      x freshness multiplier (0.6 -> 1.0)
      x doneness multiplier (burnt .45 / raw .62 / perfect 1.0)
      - penalties ($300-ish each)
```
Payout is an itemised receipt with fake line items. Career total persists in
localStorage so friends can compare.

## Feel
Cash explosion, rotating gold rays, raining dollar bills, a counter that spins up
with a rising arpeggio. The crab wears a crown the entire time, including in the pot.
