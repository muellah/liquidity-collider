# Liquidity Collider

The live Coinbase BTC-USD order book drawn as two fluids pressing against each other.
Buy orders flow in from the left, sell orders from the right; the gap between them is the spread,
trades carve cavities into the side they consume, and sweeps above $100,000 send out a shockwave.

Live: https://muellah.github.io/liquidity-collider/

- One file (`index.html`), no build step, no dependencies.
- A Web Worker keeps the full level-2 book from the public Coinbase Exchange WebSocket and groups it
  into 64 one-basis-point tiers per side.
- A GPU Navier–Stokes solver (WebGL2) turns those tiers into fluid density and inflow.
- If the feed cannot be reached, a seeded synthetic order book runs instead.

Press `?` in the app for an explanation of everything on screen.
`P` switches colour palette, `F` switches material, `H` hides the text, `M` toggles live / synthetic data.

## Materials

The data mapping is the same for every material; a material changes how the fluid moves and how it is drawn.

| Material | Motion | Look |
|---|---|---|
| Water | medium | glassy, refracting surface |
| Smoke | thin, fast, released in puffs | soft and translucent, no surface |
| Ink | thin strands that fade slowly | dark ink on light paper |
| Oil | thicker than water, slow large swirls | dark glossy layer with a faint rainbow at thin edges |
| Honey | thickest, creeps in broad bands | dull translucent gel |
| Mercury | medium | sharp-edged mirror metal; the amount shows as coverage |

`?mat=<name>` and `?pal=<0-4>` in the URL select a material and palette directly.
