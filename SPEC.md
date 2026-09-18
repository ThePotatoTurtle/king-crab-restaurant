# KING CRAB RESTAURANT SIMULATOR — spec

A dumb little browser game. One crab, one supply chain, one obscene payday.

## Constraints
- Single self-contained `index.html`. No build step, no dependencies, no assets.
- All art drawn procedurally on `<canvas>`: thick wobbly black outlines, flat fills,
  colouring offset outside the lines. Lines re-jitter 15x/sec ("boiling" squigglevision).
  Font: Comic Sans MS.
- Controls: mouse move, hold/release left click, drag. `M` mutes. Nothing else.
- ~2 minutes start to finish. No fail state — mistakes cost cash and dignity only.
- Hosted on GitHub Pages.

## The chain (6 scenes)

| # | Scene | Verb | Control | Soft fail |
|---|-------|------|---------|-----------|
| 0 | TITLE | click | click | — |
| 1 | ALASKA | catch the king crab | mouse X steers boat, HOLD to lower the pot | catch a boot / duck / tire / lesser crab: -$, keep fishing |
| 2 | THE HAUL | drive to Vancouver | click to hop potholes & moose | bonk: crab sloshes, FRESHNESS drops |
| 3 | THE TANK | crab into tank | drag | drop it, it scuttles off and insults you |
| 4 | THE KITCHEN | boil it | HOLD to keep the flame on, release in the green | RAW (still waving) / CHARCOAL |
| 5 | SERVICE | serve the plate | drag to the table | smash the plate |
| 6 | PAYDAY | exist | click | — |

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
