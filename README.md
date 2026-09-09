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
| 3 | `#demand-move-shift` | Movement along vs. shift | two panels on the line P = 100 - Q with unnumbered axes; left: a vertical price knob (10 to 90) slides a point along the curve and marks P and Q on the axes; right: a horizontal knob (-30 to 30) draws a blue shifted line beside the black original, an arrow between them, and a "D" with an up or down arrow |

Slider ranges: a price runs from half to twice its default; the figure
height is 420px (the user found 600px too tall).

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
