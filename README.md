# STRANDED — AI-Powered Space Survival

This is **STRANDED v2 — Animation & Graphics Upgrade**, a playable development build, not the completed game described in the supplied master specification. Open `STRANDED.html` via GitHub Pages (recommended). Three.js is loaded from cdnjs; the first load requires Internet access. World progress uses browser IndexedDB, tied to the origin serving the game. Export a JSON save to back up progress.

## How to play

1. Start a new expedition; move with **WASD**, hold **Left or Right Shift** to **sprint**, and press **Space** to jump. Sprint consumes stamina and cannot resume until stamina recovers to 30 after exhaustion. Press **V** to switch camera views.
2. Approach minerals and press **F** to mine them. Minerals have finite, persistent quantities.
3. Press **I** to inspect your inventory and **C** to refine alloys and craft one repair kit.
4. Return to your ship, press **E**, and restore your engines.
5. Launch. Use **WASD** for thrust in orbital space, **R** / **Q** for vertical thrust and mouse to steer; approach an orbital planet until the landing prompt appears, then **E** to land.
6. Craft habitats, construct structures, and test save/reload with **Settings → Save now / Export save**.
7. Optional: enter a DeepSeek API key in Settings, then use **Navigation → Ask DeepSeek** to generate a creative planet profile. The local engine remains authoritative.

The current prototype uses compact playable terrain zones, an articulated procedural astronaut with walk/run/jump/landing animations, richer biome scenes, and simple orbital representations. Flight and landing are simulated in a **scaled local space scene**, not seamless full-scale planet transitions. Features shown in the implementation but not tested manually on a Chromebook are *not* marked approved.

## v2 movement and visual upgrade (2026-11-11)

- Articulated astronaut with moving shoulders, arms, hips, shins and feet; detailed helmet, reflective visor, backpack and suit.
- Blended walking, running, sprinting, jumping, landing and mining animations.
- Smooth acceleration/deceleration, stamina-limited sprinting with both Shift keys, exhaustion recovery and a motion readout.
- Camera smoothing, subtle running bob and wider field of view at sprint speed.
- Biome-specific sky and sun glow, fog and lighting, instanced scenic plants/rocks/crystals, ship details and drone rotor animation.
- Procedural footsteps, running dust, landing effects and ship thruster glow.
- Low, Balanced and High graphics presets under Settings; Balanced is recommended for an 8 GB Chromebook.
- Save schema remains v1 and prior inventory, mining depletion, construction, repairs and world seeds are retained. Export a backup when moving from file:// to GitHub Pages.
- **Validation:** JavaScript syntax and release packaging checked; actual gameplay on Chromebook remains **unverified**. All user approvals stay unchecked.

## Master requirement tracking policy

Each item retains a stable ID and has a development status, dependencies, acceptance test, known limitations, and explicit user-approval field. All approval boxes stay **unchecked** unless the user approves the feature. Do not interpret implementation as approval. When an issue is reported, change status to **Broken / Needs Repair**, record the regression, and leave approval unchecked. New features are added here rather than replacing existing requirements.

Statuses: `Planned`, `In Development`, `Implemented — Awaiting Test`, `Tested — Awaiting User Approval`, `Approved`, `Broken / Needs Repair`.

| ID | Feature | Status | Dependencies | Acceptance test / known limitations | User approved |
|---|---|---|---|---|---|
| STR-001 | 3D rendering and scene lifecycle | Implemented — Awaiting Test | Three.js CDN | Render on 8GB Chromebook; context loss recovery pending | [ ] |
| STR-002 | Astronaut movement and gravity | Implemented — Awaiting Test | STR-001 | WASD, smooth acceleration, Shift sprint, fatigue recovery, jump/land; advanced collisions pending | [ ] |
| STR-003 | First-/third-person camera | Implemented — Awaiting Test | STR-002 | Toggle V; smoothed camera and terrain-height floor; object occlusion pending | [ ] |
| STR-004 | Procedural terrain and planet biomes | In Development | STR-001 | Four seed-stable zones with instanced scenery, biome sky and fog; streaming/LOD pending | [ ] |
| STR-005 | Finite resource collection | Implemented — Awaiting Test | STR-004 | Mine 3 times, reload, deposit stays depleted | [ ] |
| STR-006 | Local inventory and item transactions | Implemented — Awaiting Test | STR-005 | Mining and crafting adjust counts; capacity/drag-drop pending | [ ] |
| STR-007 | Recipe validation and crafting | Implemented — Awaiting Test | STR-006 | No free outputs with insufficient inputs | [ ] |
| STR-008 | Health, oxygen, stamina, energy | In Development | STR-002 | Environmental oxygen drain and drone damage; food/water/radiation pending | [ ] |
| STR-009 | Ship damage and repair | Implemented — Awaiting Test | STR-007 | Repair kit required, consumes one kit | [ ] |
| STR-010 | Interactive ship flight | In Development | STR-009 | Scaled orbit with thrust and fuel, no atmospheric flight | [ ] |
| STR-011 | Planet selection and landing | In Development | STR-010 | Fly within 25 units, land with fuel cost, 4 destinations | [ ] |
| STR-012 | Seed-consistent surface return | Implemented — Awaiting Test | STR-004 | Terrain and depletion persist by seed | [ ] |
| STR-013 | IndexedDB game save/load | Implemented — Awaiting Test | STR-006 | Save, refresh, continue; transaction completion handled | [ ] |
| STR-014 | JSON save import/export | Implemented — Awaiting Test | STR-013 | Export, import and restart; schema v1 only | [ ] |
| STR-015 | Hostile drones and PvE combat | In Development | STR-002 | Drone pursuit, hits and drops; combat depth pending | [ ] |
| STR-016 | Planetary habitat building | In Development | STR-007 | Module resource cost and persisted placement; real editor pending | [ ] |
| STR-017 | Optional DeepSeek JSON creative world profile | Implemented — Awaiting Test | API key | Validated name/lore only; current model availability and CORS unverified | [ ] |
| STR-018 | AI persistent missions and world director | Planned | STR-017, STR-023 | Validate and persist generated objective definitions | [ ] |
| STR-019 | Orbital stations and walkable interiors | Planned | STR-010 | Repair, dock and build attachable station modules | [ ] |
| STR-020 | NPC identities, trading and factions | Planned | STR-018 | Stable NPC identity; inventory-authoritative trade | [ ] |
| STR-021 | Research and upgrade tech tree | Planned | STR-007 | Unlock actual systems, not just prose | [ ] |
| STR-022 | Resource refinement and automation | Planned | STR-016 | Power-constrained production and bounded catch-up | [ ] |
| STR-023 | Persistent mission state and validation | Planned | STR-013 | Real triggers validate and reward once | [ ] |
| STR-024 | 3D galaxy and system mapping | Planned | STR-010 | Navigable multi-scale galaxy map | [ ] |
| STR-025 | Procedural wildlife and ecosystems | Planned | STR-004 | Discover, scan and interact with seeded lifeforms | [ ] |
| STR-026 | Space combat and pirates | Planned | STR-010, STR-015 | Shields, enemy ships, damage and salvage | [ ] |
| STR-027 | Procedural interiors, wrecks, ruins | Planned | STR-004 | Navigable rooms, persistent door and loot state | [ ] |
| STR-028 | Multi-ship ownership and station docking | Planned | STR-019 | Persistent fleet and valid docking | [ ] |
| STR-029 | Background planet generation and worker queue | Planned | STR-004 | FPS remains responsive under generation | [ ] |
| STR-030 | Terrain LOD/chunk streaming | Planned | STR-004 | Long-distance traversal without memory growth | [ ] |
| STR-031 | Full environmental survival model | Planned | STR-008 | Food, water, thermal, radiation and shelter effects | [ ] |
| STR-032 | Mining tools, scanner and discovery journal | Planned | STR-005 | Multiple equipment types with meaningful progression | [ ] |
| STR-033 | Ship interior and component panels | Planned | STR-009 | Walk to consoles and repair individual systems | [ ] |
| STR-034 | Structural modular construction editor | Planned | STR-016 | Snap previews, collisions, modules and networks | [ ] |
| STR-035 | Galaxy-scale seeded generation | Planned | STR-024 | Same universe across reloads and destinations | [ ] |
| STR-036 | Procedural weather and world events | Planned | STR-018 | Simulated effects using bounded mechanics | [ ] |
| STR-037 | AI cost budget and usage reporting | Planned | STR-017 | Session/day token limits and display | [ ] |
| STR-038 | Asset cache and robust offline recovery | Planned | STR-001 | Cached game playable after network loss | [ ] |
| STR-039 | Accessibility and remappable controls | Planned | STR-002 | Full keyboard, alternate input, contrast options | [ ] |
| STR-040 | Graphics/diagnostics and performance QA | In Development | STR-001 | FPS and Low/Balanced/High graphics presets; Chromebook benchmarks pending | [ ] |
| STR-041 | Soundscape, mixing, effects | In Development | STR-001 | Procedural footsteps and interaction beeps; ambient audio/mixing pending | [ ] |
| STR-042 | Multi-slot saves, migrations and corruption protection | Planned | STR-013 | Slot-level durability, backup validation and migrations | [ ] |
| STR-043 | Emergency recovery and no-softlock balancing | In Development | STR-008 | Health auto-recovery; survival resources/fuel softlock still possible | [ ] |
| STR-044 | Rebindable interface and responsive touch controls | Planned | STR-039 | Mobile/touch and accessible bindings | [ ] |
| STR-045 | Full tutorial inside damaged ship | Planned | STR-033 | Start inside actual walkable wreck, not on surface | [ ] |
| STR-046 | Unit tests and browser interaction tests | Planned | STR-001–045 | Execute verified gameplay and persistence tests | [ ] |

| STR-047 | Articulated astronaut animation rig | Implemented — Awaiting Test | STR-002 | Verify idle, walk, sprint, jump, land and mining poses in third person | [ ] |
| STR-048 | Smooth acceleration and stamina-limited sprint | Implemented — Awaiting Test | STR-002, STR-008 | Verify both Shift keys, exhaustion, recovery, momentum and status | [ ] |
| STR-049 | Distinct planetary atmospheres and instanced scenery | Implemented — Awaiting Test | STR-004 | Visit four planets; check performance, collisions and persistent resource IDs | [ ] |
| STR-050 | Graphics performance presets | Implemented — Awaiting Test | STR-001, STR-040 | Validate Low/Balanced/High and framerate | [ ] |
| STR-051 | Motion VFX, drone rotors and ship thrusters | Implemented — Awaiting Test | STR-010, STR-015 | Sprint dust, footsteps, rotors and thruster flame | [ ] |

## Implementation notes / limitations

- **Unverified:** No interactive browser/Chromebook gameplay tests have been executed for this build. Don't mark features approved until the user tests and explicitly approves.
- **Critical gap:** This prototype begins on the surface beside the ship. The requested interior opening is planned as STR-045.
- Planet destinations are four curated procedural seeds, not a complete expanding galaxy.
- Ground collision uses terrain height only. Static mesh collision and full camera occlusion avoidance are not yet implemented.
- Flight uses thrust in a compressed scene; there is not yet continuous atmospheric transition.
- One save slot and schema v1 only. Autosave every 15 simulation seconds; export is recommended.
- AI key stays in memory unless the user checks **Save key locally**. If saved, the key is stored in browser IndexedDB; this is not secret storage. No backend proxy is used.
- DeepSeek errors do not interrupt offline gameplay but uncached Three.js is an external dependency.
- For production, split the single file into tested modules and use a pinned dependency mirror/service worker if offline reliability is required; preserve a single-file release build.

## Next priorities

1. Test animated walk/run/jump/sprint, graphics quality and FPS, then validate movement → mine → craft → repair → fly → land → save on the target Chromebook.
2. Expand ship and interiors, introduce actual docking and more controlled ship travel.
3. Add streamed terrain chunks, collision, scanner, survival recovery resources, and a reliable planet generator.
4. Implement structured AI missions with schema validation, budget control and persistent quest history.
5. Add automated gameplay/regression tests and multi-slot atomic saving before large-scale content growth.