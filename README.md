# PelaSync — Logo in Motion

A small motion study for the PelaSync mark. The static logo is a clay dot inside two
sage rings; this page brings the rings to life three different ways and lets you compare
them side by side, set the tempo, and copy the drop-in code.

**Live page:** _(enable GitHub Pages — see below — then paste the URL here)_

## The three motions

| Motion | Feel | What it does |
| --- | --- | --- |
| **Sonar** | Crisp, alert | Thin rings are born at the core and ripple outward, fading as they travel. |
| **Breathe** | Calm, soft | The whole mark gently expands and settles in place, rings trailing the dot. |
| **Swell** | Alive, legible | The two rings hold their home positions while a matching pair sheds outward and dissolves — always readable, always moving. |

Every color is pulled straight from the icon (sage `#5F9D87`, clay `#C68360`), it's pure
SVG + CSS with no dependencies, and it honors `prefers-reduced-motion` — anyone with that
setting sees the clean static mark, no animation.

## View it locally

It's a single self-contained file. Just open `index.html` in a browser, or serve the
folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Publish it on GitHub Pages

1. Create a new repo on GitHub (e.g. `pelasync-logo-motion`) and push this folder to it.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**, pick the
   `main` branch and the `/ (root)` folder, then **Save**.
4. Wait a minute; your page goes live at
   `https://<your-username>.github.io/pelasync-logo-motion/`.

The `.nojekyll` file in this folder tells GitHub to serve the HTML as-is (no Jekyll
processing).
