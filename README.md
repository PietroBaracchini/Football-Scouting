# Football scouting database

A scouting system built from scratch: a structured player database, a hybrid rating
model that keeps data and judgement separate, and a board to read the results.

**→ [Open the board](https://pietrobaracchini.github.io/Football-Scouting/)**

---

## What you are looking at

The board shows a working shortlist. For each player it carries two scores that are
deliberately kept apart:

- **Data** — season totals taken from FotMob, converted to per-90, and scored 0–100
  against positional benchmarks. Each position is judged on the 7–12 metrics that
  matter for that position, with its own weights.
- **Scout Eye** — a grid of positional competencies scored 1–10 from watching the player.

The final rating combines them, currently 45% data and 55% scout eye. Both halves
re-normalise over whatever was actually filled in, and both report how much that was,
so a score built on four metrics is never mistaken for one built on twelve.

The point of the split is the gap between the two. Where numbers and eye disagree is
where the interesting scouting question is.

## Method notes

**Positional, not general.** There is no single metric set for "a footballer". Six
position groups each have their own sheet, their own metrics and their own weights.
Within the midfield sheet, a player filed as a defensive midfielder and one filed as a
central midfielder are judged on different competency grids.

**Missing data is visible, not hidden.** FotMob does not report every metric for every
season. A missing metric is excluded and the remaining weights rescale, rather than
being silently counted as zero — a real zero and an absent value are not the same
thing. The board shows which metrics are missing and what share of the weights the
score actually rests on.

**Benchmarks are explicit.** Every metric has a stated min and max defining the 0 and
100 points, per position, in one editable table. The model can be re-tuned without
touching code.

**Context is recorded.** Each player's team is classified by game model — direct or
patient in possession, shielding or recovering out of it — so that a midfielder's low
progression numbers can be read against how his team plays.

## Status

Early. Five players, fully scored, used to validate the model end to end. The
immediate work is volume: clustering and peer-relative benchmarking need a real
sample per position before they say anything, and the scoring scale on the eye side
needs calibrating as more players go in.

## Coming here

- The generator scripts: the database reader, the player-sheet builder, the board builder
- The rating model documentation
- Clustering by playing style, once the sample supports it

---

Pietro Baracchini 
