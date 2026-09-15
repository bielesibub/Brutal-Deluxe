# Speedball II: Brutal Deluxe — browser adaptation

Open **[▶ Play](https://html-preview.github.io/?url=https://github.com/bielesibub/brutal-deluxe/main/index.html)** to play. It is a single self-contained HTML file: no installation, server, CDN, downloads or external media requests are needed.

On load or refresh, the original Image Works / Bitmap Brothers opening credits appear before the title. Press **Start Game** (or Enter/Fire) to restart the introduction with browser audio unlocked. Fire skips to game selection. Choose **1 PLAYER GAME** for the original **SELECT MATCH** menu, then **LEAGUE** or **PRACTICE**. Practice enters the arena directly. **2 PLAYER GAME** opens local Exhibition setup. The separate **EXHIBITION** button starts the browser adaptation’s standalone solo match.

- Arrow keys / WASD: move the blue player.
- Space: tackle without the ball; tap to throw, hold and release for a high throw.
- X: pass. Tab: switch player. P / Escape: pause. M: sound.
- Touch controls and standard gamepad D-pad / stick, A (fire), B (pass), Start (pause) are supported.

Knockout, Cup, Demo Game and Replay Goals appear in their original menu positions but are dimmed and marked **NOT YET AVAILABLE**. Selecting them leaves progress unchanged. Up/down wraps through the menu; **BACK**, Escape or gamepad B returns from Select Match to Select Game. This restores the hierarchy, not the still-missing modes, pre-match management or two-player series rules.

## Local two-player Exhibition

Choose **2 PLAYER GAME**, then choose shared keyboard, Blue keyboard + Red controller, or two controllers. With two controllers, the first browser controller slot is Blue and the second is Red; these assignments remain fixed through half-time. Press a controller button before starting so the browser can detect it.

- **Blue keyboard:** WASD to move, Space to fire/tackle, X to pass, Tab to switch.
- **Red keyboard:** arrows to move, Enter to fire/tackle, / to pass, . to switch.
- **Controllers:** stick/D-pad to move, A to fire/tackle, B to pass, X to switch, Start to pause.
- **P / Escape:** pause. A disconnected controller pauses play; reconnect it in its assigned slot, release its controls, then resume. To change assignments, return to Game Menu.

Local Exhibition uses fresh team stats, keeps teammates and goalkeepers under AI control, and shares the ball-following camera. Results return to Game Menu and do not change solo cash, upgrades or league saves. Touch buttons control Blue when Blue uses the keyboard assignment. Two physical controllers and simultaneous human play still need testing; some keyboards limit simultaneous key presses.

## Included

Original Amiga title art, nine story pages, eight credit pages, typewriter cursor, corrected 16-pixel font and palette, arena tiles, team colour swap, player animation frames, ball, coins, launcher and monitor artwork. Exhibition has two 90-second halves, changing ends, AI teams and goalkeepers, possession, passing, throws, tackles, injuries, goals, celebrations, replay, half-time and final-score screens. Practice has no time limit. The original sampled title music and game effects play through a browser port of the 50 Hz sound driver.

This is a playable **adaptation**, not CPU emulation or a complete instruction-for-instruction port. AI, physics and arena hardware behaviour are approximated. Two eight-team divisions and a basic gym are implemented; cup campaigns, promotion playoffs and transfers remain open. All eleven single-player pickup types are implemented with the source selection rules. Freeze remains excluded while its source behaviour is being resolved; local two-player Exhibition is available as a first playable implementation; physical-controller acceptance testing remains open. Only cut-scene assets present in the supplied memory data are used; no replacement victory/defeat artwork is invented.

## Kickoff and movement corrections

The launcher now decodes all five bitplanes (13 original frames), with its exact frame table and the small/large ball launch sequences. Initial formations and player ball offsets come from the original sprite tables. Normal ball frames indicate height, not rotation; their built-in shadows are preserved without drawing a duplicate ball.

AI decisions update every 10 simulation ticks with a stable designated pursuer. Arrival thresholds prevent repeated direction changes, support targets track the carrier's body rather than hand animation, goalkeepers keep facing the court and automatically clear possession, and stationary or blocked players stop their run animation. These are fixes to the browser adaptation, not a claim that the complete original AI has been ported. Regression tests cover launch milestones, overshoot, target jitter, pursuer switching, goalkeeper clearance and settled support players. The corrected launch and formation have also been checked in the local browser.

## Arena scoring corrections

Multiplier ramps use all four original 49-position paths and ball frame data, with a multiplier change at step 22. Opponents first reduce your multiplier before gaining their own. Enter a ramp along its vertical channel with a low ball; ordinary wall hits no longer award a multiplier.

Each team has its own star bank. Hitting your bank lights a star for multiplied points; hitting a lit opponent star extinguishes it and subtracts two points. Five lit stars yield the original ten-point base bonus on the next one-second check. Banks clear and swap at half time. Lit stars use original pitch tiles, and replay snapshots preserve their historical scoring state.

Regression tests cover both directions through both ramps, multiplier contention, bank boundaries, duplicate hits, extinguishing, five-star bonuses, half-time bank changes and replay state isolation. General AI/physics and the ramp housing collision integration remain approximations; remaining fidelity work and exact collision timing are tracked in NEXT_STEPS.md.

Zappers now activate for low loose balls, flash both original wall sprites, play the original effect and rebound the electrified ball. Opponent contacts consume charges and cause knockdowns; teammates can catch safely. The multiplier sets one to three charges per throw. Automated checks cover contact, rebound, catch and replay behaviour. Damage and throw slowdown use source formulas; collision and knockdown motion remain adapted.

## Medibots

Serious injuries now trigger a treatment stoppage with two original medibot sprites, lifting/carrying animation and the original injury/pickup sounds. The patient returns at the sideline after evacuation. Clock and powerups pause during treatment; multiple injuries are handled sequentially. Paths and injury staging remain adapted. Browser inspection and regression checks cover the sequence and safe match transitions.

## Match cash

Coins award 100 cash to the collecting team, using the original default value and collection sound. Pickup notices show the running total; half-time and full-time screens show both totals. Cash carries across goals and half-time, then resets for a new match. Coins no longer heal players. Four coin slots use original quadrant positions and respawn delays. New coins stop spawning at 10,000 blue cash in Practice or 1,100 in Exhibition (borrowing the original Knockout limit); coins already visible remain collectible. Spend banked earnings on upgrades in the gym.

## Armour

Original armour icons now appear on the pitch. Collection boosts one player attribute to 250; a damaging hit drops the piece and restores that attribute. Each piece allows two collections before replacement. An overhead icon identifies the wearer. Armour works with temporary stat effects and is recorded in replays.

## Provenance

All shipped graphics, story/credit text, samples and music sequences come from [Simon Frankau's speedball2-re-amiga](https://github.com/simon-frankau/speedball2-re-amiga). No outside screenshots, recordings, fonts, generated images or third-party media are used in the game.

Original game © 1990 The Bitmap Brothers / ImageWorks. Design: Eric Matthews. Code: Rob Trevellyan. Art: Dan Malone. Music: Nation 12. Music code and FX: Richard Joseph. Reverse engineering: Simon Frankau.