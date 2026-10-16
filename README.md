# Ask Oscar — Duolingo Chess mockup

Interactive, single-file mockup (`index.html`) of an **"Ask Oscar"** AI coach inside Duolingo Chess's *Review your game* screen.

## Demo flow
1. Review screen shows move 14 (`Ne5`), with **Better move available**. Only one action button shows at a time:
   - **FIX MOVE** (yellow) rewinds to before move 14 and gives you the move.
   - **HINT** (light grey) replaces it while you're fixing and draws the best move as an arrow. Tap the bishop and then d5 (or just d5 once the hint is showing) to play it.
   - **NEXT HIGHLIGHT** (green) appears once you find the best move.
2. Tap **ASK OSCAR**. A chat sheet slides up, the board shrinks so it stays visible, and Oscar opens with *"Reviewing move 14 — your knight on e5"*.
3. Tap a chip (or type something):
   - **Why was this weak?** shows red arrows for `…Nf4` hitting your queen
   - **What was the best move?** shows `Bxd5!` with a yellow arrow and an eval bar
   - **Show me the line.** plays `14. Bxd5 c6 15. Bb3` on the board
4. **Let me try it!** closes the sheet and hands the position back to the player.

Typed questions get matched by keyword to the scripted answers, so it runs without a backend. Tap a move tag in a bubble (for example `Bxd5`) to redraw it on the board. Use `index.html?chat=1` to open with the chat already showing (handy for screenshots).

## Run locally
Open `index.html` in a browser. On desktop it's drawn inside an iPhone frame (390×844). On a phone it fills the screen.

## Deploy (shareable link)
- **Vercel:** go to vercel.com/new, import this GitHub repo, set Framework Preset to "Other", leave the build command empty, and deploy. Or from the CLI: `npx vercel --prod` in this folder.
- **Netlify:** drag the folder onto app.netlify.com/drop.
- **GitHub Pages:** go to Settings, then Pages, choose Deploy from branch, and pick your branch with `/ (root)`.
