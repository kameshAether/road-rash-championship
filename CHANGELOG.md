# Changelog

All notable changes to Road Rash.

## [Unreleased] — 2026-09-26

### Fixed
- Player attacks actually land: cooldowns were initialised as `punchCooldown` /
  `kickCooldown` / `weaponCooldown` but read as `punchCd` / `kickCd` /
  `weaponCd`, so Space/K/W never triggered an attack
- Punch and kick use a real reach window (lateral 55/65px) instead of ~0.8px
- Race distance converts km/h to m/s, so Coastal Highway takes ~25s instead of ~9s
- Rivals are clamped to the road instead of drifting off-screen forever, and the
  150-point overtake bonus is paid once per rival per race instead of every frame
- Payouts are whole dollars (no more `$3172.6000000000004`)
- The top HUD row (wallet, position, hazard, damage bars) is visible again, and
  the HUD is hidden behind the results screen
- Garage "Repair Bike" clears the damage actually carried into the next race
  (it previously healed a value the next race ignored)
- Score resets at the start of each race instead of accumulating forever
- Simulation is frame-rate independent (fixed 60Hz steps) with a guard against
  two concurrent render loops after a fast pause/resume
- Obstacle removal no longer skips entries (reverse iteration)
- rgba particles no longer inherit a stale canvas fill style

### Added
- `localStorage` save/load: wallet, purchases, unlocks, upgrades and carried
  damage survive a page reload
- Hazard meter readout in the HUD (the hazard value was computed but never shown)
- Multi-hit weapons bank a quick follow-up swing; weapon `stun` extends the
  opponent's knockdown instead of being unused
- Meta description and theme-color for browser chrome
- Accessibility-friendly meta tags

### Changed
- Next track unlocks on a top-half finish; Mountain Pass is no longer unlocked
  from the start
- Volume slider scales a single master gain (levels were previously applied twice)
- Volume control moved to the bottom-right so it no longer overlaps the HUD

### Removed
- Unimplemented "B — Brake+Weapon" control from the help screen
- Dead code: `spawnBlood`, `boost`, the duplicate HUD updater, `weaponStunLeft`

## [1.0.0] — Initial Release

- Motorcycle combat racing browser game
- Orbitron-themed UI with neon red palette
- Keyboard controls: arrow keys to accelerate/brake/steer, Space to punch,
  K to kick, W to use the equipped weapon, P to pause
