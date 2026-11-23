# Critical Care Core · Final Review · Jeopardy+

Review game for the CCC final exam (AKAT / BKAT / CCRN-PCCN blueprint). It runs on one projector laptop, and residents play on their phones.
All items are original. The commercial practice exam was used only as a blueprint for coverage and style.

- **Host (projector):** `index.html` → https://scottbrickner.github.io/critical-care-education/final-review/
- **Players (phones):** `play.html` → the QR code on the lobby screen opens it with the room code filled in
- **Backend:** Supabase project *scottbrickner's Project*, tables `ccr_games / ccr_players / ccr_answers`. Anonymous users can only touch them through `ccr_*` RPCs, and only the host key can change game state.

## Run of show: 1300–1430 (90 min)

| Time | What |
|---|---|
| 1300–1308 | Lobby. Residents scan the QR, enter their **first and last name**, and pick **Group A/B/C** (the same groups as this morning's stations). Explain confidence stakes. |
| 1308 | **🎲 Opening toss-up.** One pop-culture question, no points. The group with the highest % correct gets the board, and a tie triggers a spin. |
| 1310–1405 | Board. Roughly 20 of the 24 tiles, about 2.5 min each. Hit **Rotate roles** whenever it says *(due!)*, every 4 tiles. |
| 1405–1412 | ★ Final (500). |
| 1412–1425 | **📊 Calibration report** on the projector: "Does our confidence match our accuracy?", hazardous misconceptions, re-teach list. Faculty re-teach the top 2–3. |
| 1425 | **End game → send results to phones.** Each resident gets a private calibration plus their own "review before the exam" list. |

## Scoring (certainty-based marking)

- Every resident answers and picks a confidence. **Right:** +1× / +2× / +3× the tile value. **Wrong:** 0 / −2× / −6×.
- Team tile score = the **average** of that group's members, so a group of 5 doesn't beat a group of 4 on headcount. Members who don't answer count as 0.
- **⚖ Judgment calls:** best-answer credit (100 / 50 / 25 / 0%), no multiplier, framed as formative. Devil's advocate argues for another answer before you lock.
- **🔧 Hands-on:** everyone answers the calculation on their phone. The group's **Skills lead** also does the live task, and faculty tick the checklist per group for a bonus of up to the tile value.
- **🔗** Bed 4 is an unfolding case: play Cardio 300 before 400.

## Board control

- **First pick:** the opening toss-up (4 pop-culture questions on rotation, 20 sec, no points). Or use *random draw*.
- **After that:** the group with the best score on the last tile picks next. On a tie, the group already holding the board keeps it. If none of the tied groups held the board, a spin decides.
- **Override:** click any group's score card to hand them the board.
- Phones show "Your group has the board!" so the Charge nurse knows to call it.

## Faculty notes

- **Roles** (rotate every 4 tiles): *Charge* answers the debrief prompt for the group. *Skills lead* goes up for 🔧. *Devil's advocate* argues for a different answer on ⚖ tiles.
- Hands-on equipment to stage: **5392 or the pacemaker sim** (Hands-On 400), **vasoactive sim/pump** (Hands-On 100), **transducer/hemo sim** (Hands-On 300). A faculty member plays the neuro-check patient (Hands-On 200).
- **What residents are told:** only group scores show on screen. Faculty can see individual results afterward to plan exam prep, and it's practice, not graded. Individual data never goes on the projector. *Faculty view* (by name) and *Download CSV* are for post-session review.
- **Where results live:** Supabase tables `ccr_players` + `ccr_answers`, keyed by room code. **Write down the room code** and click **Download CSV** before leaving. Claude can pull and score any session by its code.
- **If Wi-Fi dies:** open the *🪧 Paddle / manual scoring* drawer on any tile. Groups hold up a letter card plus a 1/2/3 card, and you tap them in. Manual entries override phone answers for that group. Or start in **Offline: paddle cards only** from Setup.
- Refreshing the host page is safe: the game state is saved in the browser. Phones reconnect on their own.
- Pacing items follow the unit standards: output at 2× the capture threshold, sensitivity at ≤ ½ the sensing threshold, escalate when troubleshooting is exhausted, never unplug the cables to check the underlying rhythm.

## Editing questions

The questions live in `src/bank.js` in the studio working copy. Ask Claude to edit a tile and rebuild. Answer keys are obfuscated in the built page so residents can't read them from the source.
