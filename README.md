# Introductory Microeconomics: Interactive Tools

Source for the class tools site at
**https://rabbanimaysam.github.io/micro-interactive/**

Students pick a chapter, open a tool, and move sliders; the figure redraws
as they move them. Tools are added one at a time as the course proceeds,
so the chapter list is not exhaustive.

## Tools

| Chapter | Anchor | Tool | Inputs (defaults) |
|---|---|---|---|
| 1 | `#budget-line` | Budget line | budget $10, burger $2, can of soda $1 |

## Architecture

One file, `index.html`: inline CSS, inline JavaScript, Plotly from a public
CDN. No build step. Open `index.html` in a browser to preview.

The look (header, sticky chapter nav, sidebar, white tool cards, slider
rail with a reset button) copies the interactive companion site of the
Amazon paper (`RabbaniMaysam/amazon-interactive`).

Adding a tool: add a `<section class="tool-card" id="...">` under the
chapter's heading with a `controls` div, a `plot` div, and any readouts;
declare its slider specs (`label`, `value`, `min`, `max`, `step`, `fmt`)
and a draw function; register it in the `DOMContentLoaded` handler with
`makeControls`. Add the anchor to the sidebar list and, for a new chapter,
a link in the top nav.

## Publishing

GitHub Pages serves the `main` branch root. Push to `main` and the site
rebuilds within a minute or two.
