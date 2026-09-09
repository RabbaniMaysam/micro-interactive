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

Slider ranges: a price runs from half to twice its default; the figure
height is 420px (the user found 600px too tall).

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
