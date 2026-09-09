# Introductory Microeconomics: Interactive Tools

Source for the class tools site at
**https://rabbanimaysam.github.io/micro-interactive/**

Students pick a chapter, open a tool, and move sliders; the figure redraws
as they move them. Tools are added one at a time as the course proceeds,
so the chapter list is not exhaustive.

## Tools

| Chapter | Anchor | Tool | Inputs (defaults) |
|---|---|---|---|
| 1 | `#budget-line` | Budget line | budget $10 (5 to 15), burger $2 (1 to 4), can of soda $1 (0.5 to 2); axes fixed at 10 burgers by 15 cans |
| 3 | `#demand-experiment` | Demand experiment | five empty rows of price and quantity (0 to 100), typed in class; points plotted and connected in row order |
| 3 | `#demand-move-shift` | Demand: movement along vs. shift | two panels, no card title, each with its own title; the demand line is the segment of P = 105 - Q from Q = 20 to 85, floating inside arrow axes (Plotly's axes hidden, arrows drawn as annotations); left: a vertical price knob (25 to 80) slides a point along the curve and marks P and Q on the axes, no axis titles; right: axes labeled P and Q, a horizontal knob (-25 to 25) draws a blue shifted line beside the black original, an arrow between their midpoints, D1 and D2 at the same height beside the lines' right ends (D2 withheld while the shift is under 7), and "D" with a tight up or down arrow beside the middle of the blue line on the side away from the black one |
| 3 | `#supply-experiment` | Supply experiment | mirror of the demand experiment from ch03 slide 21 (tutoring for 3 hours): Payment and Quantity columns, same code via a config |
| 3 | `#supply-move-shift` | Supply: movement along vs. shift | mirror of the demand tool on the segment of P = Q + 5 from Q = 20 to 85; price knob 30 to 85; labels S, S1, S2, and "S" with an arrow placed below and right of the blue line for a rightward shift |
| 3 | `#equilibrium` | Equilibrium, surplus, and shortage | the two segments above cross at Q = 50, P = 55; a vertical price knob (30 to 80, default 55) marks P on the axis; at 55 one point with Q = 50; away from it two open points on D and S, dotted guides, Qd and Qs on the axis, and, only while the "Show labels" toggle at the top right is on, Qd and Qs names plus a thick dark red segment between the points labeled "Surplus = n" above 55 or "Shortage = n" below; the toggle is off by default and on every reopen (no spoilers), and with it off both quantities read plainly as "Q = n" |
| 3 | `#shift-equilibrium` | Shifts and the new equilibrium | its own frame (Q 0 to 128, P 0 to 124) with e1 at its center (64, 62) and short D and S segments (Q 35 to 93 before a shift); two horizontal knobs (Shift D, Shift S, each -56 to 56, a tick marking the center) draw the shifted curve in blue as D2 or S2, the new crossing e2, P1, P2, Q1, Q2 on the axes with no numbers, and blue arrows hugging each axis from 1 to 2; a shifted curve's segment is centered on e2 (it slides along its own line as it shifts, so the other curve always cuts it at its midpoint), and an original curve's end is extended when e2 would fall within 8 units of it; a "2" label is offset when it would print on the "1" label |

Slider ranges: a price runs from half to twice its default; the figure
height is 420px (the user found 600px too tall). The two-panel tool uses
250px-tall panels with a 0.4em gap; the price label on the left panel is
rotated vertical so the left margin stays at 24px.

Each tool is a page of its own: the sidebar link sets the URL hash, the
router shows that `.tool-page` and hides the others, and calls the tool's
redraw function (Plotly cannot size a figure inside a hidden element).
The first tool is shown when the hash is empty or unknown.

## Architecture

One file, `index.html`: inline CSS, inline JavaScript, Plotly from a public
CDN. No build step. Open `index.html` in a browser to preview.

The look (header, sticky chapter nav, sidebar, white tool cards, slider
rail with a reset button) copies the interactive companion site of the
Amazon paper (`RabbaniMaysam/amazon-interactive`).

Adding a tool: add a `<section class="tool-card" id="...">` under the
chapter's heading with a `controls` div and a `plot` div; declare its
slider specs (`label`, `value`, `min`, `max`, `step`, `fmt`) and a draw
function; register it in the `DOMContentLoaded` handler with
`makeControls`. Add the anchor to the sidebar list under its chapter
(chapters are plain labels, tools are links) and, for a new chapter, a
link in the top nav.

House style (the user's, September 8, 2026): no prose on the page beyond
titles. No introductions, descriptions, equations, readouts, tables, or
legends. A tool is one compact slider row and one large figure; labels
live inside the figure.

## Publishing

GitHub Pages serves the `main` branch root. Push to `main` and the site
rebuilds within a minute or two.
