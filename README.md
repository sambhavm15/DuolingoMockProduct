# Ask Oscar — Duolingo Chess mockup

Interactive, single-file mockup (`index.html`) of an **"Ask Oscar"** AI coach inside Duolingo Chess's *Review your game* screen.

## What it does
The page is a real, playable game of chess against a built-in engine, wrapped in Duolingo's "Review your game" screen. Oscar answers questions using live analysis of the actual position, not canned text.

**Opening screen (the slide demo).** It loads on the move-14 review: you played `Ne5`, and Oscar notes that "There was a chance to capture here."
- **FIX MOVE** rewinds the board. **HINT** draws the best move (`Bxd5`) as an arrow. Play it to get **Best move!**, then tap **PLAY ON** to keep playing from there.
- The redo arrow (→) instead continues the game as originally played.

**Playing.** Tap a piece and then a square; legal moves show as dots. You're White and the engine replies as Black. After each of your moves, Oscar grades it:
- **Best move! / Good move** (green)
- **Better move available** (orange)
- **Big mistake** (red)

The tag at the top (WAY AHEAD … WAY BEHIND) tracks the evaluation.
- If your move had a better alternative, the button becomes **FIX MOVE**. Otherwise it's a grey **HINT**.
- The ← and → arrows take moves back and replay them.
- **X** starts a new game from the opening position, and so does `?new=1`.
- When the game ends (checkmate, stalemate or any draw), the button becomes **NEW GAME**.

**Ask Oscar.** The chat follows the game and suggests questions that fit the moment. You can also type questions in plain English:
- *Was that a good move? / Why was this weak?* Grades your last move, names the reply that punishes it, and says what you missed (a capture, mate or castling).
- *What was the best move?* Gives the engine's top move, with an arrow and an evaluation bar.
- *Show me the line.* Plays the best continuation on the board.
- *What should I do now?* Gives a hint for the current position; tap where the arrow points to play it.
- *What's Black threatening? / Am I in check?*
- *Who's winning?* Gives the evaluation plus a material count.
- *Are any of my pieces hanging?*
- Rules: how each piece moves, castling (including whether you can castle right now), en passant, promotion, check and checkmate, stalemate, draws, piece values, opening tips.
- *New game*, *take back*

Tap any move tag in a bubble to see it on the board. Tap the board to return to the live game.

## Limitations
- **You always play White.** The engine always plays Black, and the board isn't flipped.
- **Pawns always promote to a queen** (no piece picker). The engine can underpromote.
- **The engine is simple:** a 4-ply alpha-beta search with captures-only extension, roughly club-beginner strength. It's deterministic, so the same moves get the same replies. It can miss deep tactics, and its move grades are judgments from a shallow search, not a strong engine like Stockfish. The opponent and the coach use the same engine.
- **Oscar isn't a language model.** Typed questions are matched by keyword to the question types above. Anything else gets a polite "try asking me about…". The explanations come from templates filled with the engine's analysis (captures, hanging pieces, mates, castling), so they're accurate but not deeply strategic.
- **No clocks, resign/draw offers, saved games, PGN export or opening names.**
- **Each move freezes the screen for up to about 2 seconds** while the engine analyses and replies (it runs on the main thread).
- **The move-14 demo uses hand-written answers** for the three suggested questions, so the slide screenshots stay polished. Everything after that is generated.
- Typing `?chat=1` in the URL opens Oscar right away.

## Run locally
Open `index.html` in a browser. On desktop it's drawn inside an iPhone frame (390×844). On a phone it fills the screen.

## Deploy (shareable link)
- **Vercel:** go to vercel.com/new, import this GitHub repo, set Framework Preset to "Other", leave the build command empty, and deploy. Or from the CLI: `npx vercel --prod` in this folder.
- **Netlify:** drag the folder onto app.netlify.com/drop.
- **GitHub Pages:** go to Settings, then Pages, choose Deploy from branch, and pick your branch with `/ (root)`.
