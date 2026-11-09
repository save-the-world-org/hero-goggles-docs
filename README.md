# hero-goggles-docs

The docs for [Hero Goggles](https://hero-goggles.darkshift.cloud), by Darkshift: find an influencer at KubeCon by their
UWB beacon, on an iPhone and in Meta Ray-Ban Display glasses. Live at https://hero-goggles-docs.darkshift.cloud.

A static site: plain HTML pages and one stylesheet, no build step and no dependencies.

| File | Page |
|---|---|
| `index.html` | Overview, with the commercial |
| `quick-start.html` | The glasses, the iPhone, the live map and MCP |
| `architecture.html` | How the parts connect |
| `radar.html`, `dash0.html`, `elasticsearch.html`, `gitar.html` | One page per sponsor integration |
| `infrared.html` | How Infrared by Darkshift builds and hosts it |
| `thanks.html` | The hackathon, its sponsors and partners |
| `assets/site.css` | The styles: Darkshift's palette, Syncopate headlines, Google Sans Flex text |
| `assets/logos/` | Sponsor and Darkshift logos, copied from their own files, never redrawn |
| `media/` | The commercial: `hero-goggles-commercial.mp4`, `.webm` and the poster `.webp` |

## Run it locally

    python3 -m http.server 8000     # or: npx serve .
    open http://localhost:8000

## Change it

Edit the HTML directly; every page carries the same header, side navigation and footer, so a new page copies one of
them and adds itself to every page's `<nav class="side">`. Every claim about the code links to the file in
[save-the-world-org](https://github.com/save-the-world-org) that backs it; anything not live says so.

## Deploy

The repo is the Product `hero-goggles-docs` in the org save-the-world-org on Infrared's hosted plane. Infrared builds it
with Paketo buildpacks as a static site and serves it from the zone `hero-goggles-docs-production`, public. A merge
does not deploy by itself:

    ir --org save-the-world-org deployment new --product hero-goggles-docs
    ir --org save-the-world-org deployment wait --product hero-goggles-docs --for released

The repo is also in Infrared's code index (domain `save-the-world`).
