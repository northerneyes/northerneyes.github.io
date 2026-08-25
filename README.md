# northerneyes.github.io

My portfolio: **https://northerneyes.github.io/**

I'm George Bukhanov, a Lead Software Engineer and Frontend Architect in Espoo, Finland. The site is my introduction: who I am, what I'm strong at, and four case studies from 10+ years of building complex web applications, most recently a geospatial inspection platform (Mapbox GL JS, Potree, OpenSeadragon, ~286,000 lines of TypeScript).

## How it's built

The page is deliberately a single hand-written HTML file with vanilla CSS and JavaScript. No framework, no build step, no runtime dependencies. The only external requests are Google Fonts and the click-to-load embeds.

Some details worth a look in [`index.html`](index.html):

- **Morphing point cloud.** The background visual is ~1,300 particles in a `<canvas>`, generated procedurally (a transmission tower, a globe, a terrain ridge, a network graph, a cube lattice) and interpolated from one shape to the next as you scroll. Plain 2D canvas with a hand-rolled 3D projection, no WebGL library.
- **Slide scrolling with a gentle settle.** Sections behave like slides, but instead of CSS scroll-snap (which grabs mid-scroll) a small script waits until you stop and, only if you are already near a slide edge, glides the rest of the way with eased animation. Any input cancels it instantly.
- **A real map editing demo.** The first case study loads MapLibre GL on click: draw a line between synthetic utility poles, drag any vertex, and watch it snap with a radius that tightens as you zoom in, with a live length readout. These are patterns from my production editor, rebuilt from scratch in ~150 lines. Tiles by OpenFreeMap, no API key.
- **Click-to-load embeds.** The map demo, the Potree point cloud example and the platform video load only on click, so the initial page stays light. When the page runs inside another frame, the same buttons open the content in a new tab instead.
- **Accessibility.** Everything respects `prefers-reduced-motion` (static visuals, no snap, no count-ups), the accordion is keyboard-friendly with `aria-expanded`, and focus states are visible.

## Running locally

It's a static page:

```
python3 -m http.server 8000
# open http://localhost:8000
```

## Credits

- Product screenshots and the platform video are from Sharper Shape's public materials at [sharpershape.com](https://sharpershape.com). The map, point cloud and imagery engines shown there are my work.
- The embedded point cloud example (Eclepens quarry) is from [potree.org](https://potree.org), the open-source renderer I build on professionally.
- Fonts: Bricolage Grotesque and Spline Sans Mono via Google Fonts.

## Contact

gbuhanov@gmail.com · [LinkedIn](https://www.linkedin.com/in/george-bukhanov-93802ba3) · [Medium](https://medium.com/@northerneyes)
