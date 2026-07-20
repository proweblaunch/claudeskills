# ZODIZE — Cinematic Digital Environment
### Experience Storyboard & Creative Direction
Prepared as a coordinated pass: Creative Direction → Brand Narrative → Cinematic Direction → Motion Choreography → 3D Spatial Design → Enterprise SaaS Clarity → Typography/Systems → Frontend Feasibility → Accessibility → Award-Level Critique.

---

## 0. THE CENTRAL IDEA

Stop calling it a website. Call it **THE CORE** — a single continuous environment the visitor pilots through, not scrolls past.

**The governing metaphor:** the visitor is descending into the operating layer of a living enterprise system — a physical manifestation of architecture, ledgers, and infrastructure rendered as a dark, precision-machined, bioluminescent world. One object survives the entire journey and evolves with the story: **the Core**, a faceted crystalline intelligence-form that is dormant at the top of the page and fully assembled/activated by the CTA. Every scene is a chamber the visitor's camera travels *through* on the way to the Core's activation. This gives you the single non-negotiable rule of the whole build:

> **Nothing fades in. Things are arrived at.** The camera moves; the world reveals itself because you got closer to it, not because a CSS opacity value changed.

This is what separates a "scroll site with 3D decoration" from a cinematic environment — and it's the standard every scene below is held to.

**Rejected direction (name it so no one drifts back to it):** section cards stacked vertically with a 3D hero at the top and static content below. That is the default this brief explicitly asked to avoid.

---

## 1. BRAND NARRATIVE ARC (the story the camera tells)

A premium enterprise brand reveal has to earn trust, not just spectacle. The seven scenes below map directly to a classic B2B trust arc — **Awaken → Prove capability → Prove precision → Prove philosophy → Prove humanity → Prove scale → Prove results → Invite** — but every beat is staged as physical travel through the Core's world rather than a slide.

| Beat | Emotional job | Scene |
|---|---|---|
| Awaken | Command attention, establish world | 01 Emergence |
| Orient | "here's what this place does" | 02 Capability Corridor |
| Prove | Numbers as physical evidence | 03 Proof Field |
| Explain | Philosophy, not features | 04 Architecture Chamber |
| Humanize | This is built by people, not a template | 05 The Foundry |
| Expand | Show the product universe | 06 Product Constellation |
| Assemble | Payoff — the Core completes | 07 The Assembly |
| Validate | Third-party proof | 08 Proof Vault |
| Resonate | Voices in the space | 09 The Signal Room |
| Convert | Clear, confident exit | 10 The Threshold |

---

## 2. WORLD BUILD & SPATIAL LOGIC

- **One scene graph, one camera.** All "sections" are waypoints on a single dolly path through one Three.js scene — not 10 separate canvases. This is the difference between "3D decoration on a normal page" and an actual environment.
- **Depth budget:** every scene keeps a 3-plane system — **foreground** (interactive/readable UI, sharpest focus), **midground** (the Core + hero geometry, the story), **background** (fog, particulate, distant architecture, softest focus, slowest parallax). This is what sells depth of field without literally ray-tracing DOF.
- **Persistent horizon line + fog gradient** across all scenes so the world never resets — this is the single cheapest trick that makes 10 scenes feel like one place instead of 10 canvases stitched together.
- **Recurring cast:** the Core (protagonist object), data-motes (ambient population — small glowing particles that behave like a school of fish, reused everywhere), and holographic UI shards (the "premium enterprise" texture — thin glass panels with instrument-panel typography, always slightly out of focus unless directly addressed).

---

## 3. SCENE-BY-SCENE STORYBOARD

### SCENE 00 — Ignition (Loader)
- **Purpose:** Replace the preloader with the first frame of the film, not a progress bar bolted to the front door.
- **Feeling:** Anticipation. Something is powering on.
- **First noticed:** A single point of light in total darkness, breathing.
- **Camera:** Static, extreme close, slow push-in of 4–6%.
- **Choreography:** The point of light pulses in time with a low counting rhythm; on completion it doesn't fade the loader out — it **explodes outward into the Scene 01 environment**, and that explosion *is* the transition (camera is inside the blast).
- **3D objects:** One point light + a thin particle shell that will become the Core.
- **Fore/mid/back:** N/A — single subject, full black.
- **Lighting:** One key light only, cold blue-white, no fill (drama through absence).
- **Material:** Emissive point, no surface yet — the Core hasn't been "manufactured" yet.
- **Scroll behavior:** None — this is time-based, not scroll-based (respect the user's patience; 1.6s max, skippable on click/tap).
- **Transition out:** Match-cut: the point of light *is* the same light source that becomes the Core's inner glow in Scene 01.
- **VFX:** Bloom on the point only. No lens flare filigree — restraint here buys credibility for the bigger moments later.
- **Brand message:** Precision before spectacle.
- **Interaction:** Click/tap/keypress skips instantly (accessibility + power users).
- **Perf note:** This scene has zero geometry cost — it's free, so it's the right place to hide asset preloading behind.

---

### SCENE 01 — Emergence (Hero)
- **Purpose:** Establish the world and the thesis line. This is the whole brand in 8 seconds.
- **Feeling:** Awe, restrained power. "This company builds serious things."
- **First noticed:** The Core — a faceted, half-formed crystalline structure hanging in volumetric fog, slowly rotating, incomplete (visibly missing panels — foreshadows Scene 07's assembly payoff).
- **Camera:** Starts inside the fog close to the Core, slow **dolly-out and slight orbit** (not a static hero shot) as the headline materializes — camera movement is doing narrative work, not decoration.
- **Choreography:** Headline doesn't fade in — individual words **condense out of the data-motes** near the Core, as if the system is compiling the sentence in real time. Subtext and CTAs arrive on a half-beat delay, riding the same dolly.
- **3D objects:** The Core (hero protagonist), sparse orbiting data-motes, distant unfinished architecture silhouettes in the deep background (previews of later scenes — plant the flag early).
- **Fore/mid/back:** FG — headline + CTA glass panel, always in crisp focus, camera-locked (billboarded) so it never blurs even as the camera moves. MID — the Core. BG — soft fog + far silhouettes, heavy DOF blur.
- **Lighting:** Single cold key from upper-left (this becomes the film's constant key direction — keep it consistent for the entire journey), teal rim light off the Core's facets, near-total darkness elsewhere.
- **Material:** Core = brushed gunmetal chassis with glowing seams (not glassy/toylike — think satellite hardware, not a video-game gem).
- **Scroll behavior:** First scroll tick triggers the dolly-out; scroll velocity subtly affects orbit speed (skilled scrollers feel the machine respond to them).
- **Transition to next:** Camera continues its dolly past/through the Core's outer shell — we fly *through* a gap in its unfinished panels into Scene 02, like entering a corridor inside the machine.
- **VFX:** Volumetric fog with god-rays off the key light, restrained bloom on emissive seams only, chromatic aberration at 2% max (cinematic lens feel, not a glitch effect).
- **Brand message:** "Built for Scale. Designed for Impact" — spoken by the object, not just the type.
- **Interaction:** Cursor/gyroscope adds ±3° camera parallax (desktop mouse, mobile device-tilt) — subtle, never nauseating.
- **Perf note:** Highest-fidelity scene on desktop; on mobile the orbit is replaced by a locked camera with only the compile-in text animation (see §8 Device Tiering).

---

### SCENE 02 — Capability Corridor (Services)
- **Purpose:** "Here is what this place actually does" — orient the visitor inside the machine.
- **Feeling:** Competence. Systems humming, everything purposeful.
- **First noticed:** Four illuminated instrument bays lining the corridor the camera is now traveling down, each holding a distinct geometric "capability object" (a floating circuit-lattice cube for Custom Software, a ledger-stack for Fintech, a modular grid for Enterprise, a branching tree for SaaS).
- **Camera:** Continuous forward dolly (the "walk down the corridor") — each bay is reached, not scrolled to.
- **Choreography:** As the camera arrives at each bay, that bay's object **assembles from its constituent fragments** (small pieces fly in from the corridor walls and lock together) while its glass label-panel racks into place beside it. Previous bays stay lit and visible in the rear-view, reinforcing "one continuous space."
- **3D objects:** Four capability totems (bespoke low-poly forms, distinct silhouettes so they read even out of focus), corridor wall geometry with subtle circuit-trace emissive lines.
- **Fore/mid/back:** FG — glass label panel with heading + one-line copy, camera-locked. MID — the capability totem, in hero focus as the camera reaches it, softening as camera passes. BG — the corridor continuing into darkness, previous/next bays glimpsed.
- **Lighting:** Same key direction as Scene 01, but each bay adds a colored accent light (blue/green alternating) to create rhythm down the corridor — this is how you avoid "everything looks the same" over ten scenes.
- **Material:** Totems in brushed metal + emissive glass, label panels in frosted holographic glass with mono-spaced instrument type.
- **Scroll behavior:** Scroll = forward camera travel (scrubbed 1:1, not time-based) — this is the section that must feel most "piloted."
- **Transition to next:** Corridor opens into a wide chamber; the four totems' emissive lines all sweep forward and converge into a single point ahead — that convergence point becomes the data-crystallization effect that opens Scene 03.
- **VFX:** Light-trail particles along corridor walls suggesting data flow, assembly-snap micro-flash (very brief, physically motivated, not glittery).
- **Brand message:** Four disciplines, one engineering standard.
- **Interaction:** Hovering/tapping a bay pauses forward travel and gently orbits that totem, surfacing "Learn more" — camera resumes on scroll continuation (this is your affordance for people who want to linger, without breaking the piloted feel for people who don't).
- **Perf note:** Four totems is the ceiling for hero-quality simultaneous geometry; anything beyond it gets impostor/billboard treatment.

---

### SCENE 03 — Proof Field (Stats)
- **Purpose:** Numbers as physical, verifiable evidence, not a stat-counter widget.
- **Feeling:** Weight, credibility, "this isn't a startup pitch deck."
- **First noticed:** The convergence point from Scene 02 detonates into a field of data-motes that **crystallize mid-air into four giant numerals** — the numbers are built from thousands of the same particles seeded throughout the whole experience (visual continuity payoff).
- **Camera:** Brief held wide shot (the one static beat in the whole film) so the numbers can be read without competing with camera motion — earn the pause here, spend it deliberately.
- **Choreography:** Numerals count up as they crystallize (the counting *is* the assembly, not a bolted-on separate animation), each locks into a floating glass plinth labeled in mono type.
- **3D objects:** Four numeral particle-sculptures on plinths, ambient mote field.
- **Fore/mid/back:** FG — none (numbers ARE the subject, full attention). MID — the four numeral sculptures in a shallow arc facing camera. BG — the corridor's residual glow fading into open dark space, signaling scale.
- **Lighting:** Even, slightly brighter than surrounding scenes — this is the "proof" beat, it should feel illuminated/verifiable rather than moody.
- **Material:** Particle/point-cloud numerals (translucent, faceted points) rather than solid extruded text — keeps it feeling like data made visible, not a graphic.
- **Scroll behavior:** Scrub-locked count-up tied precisely to scroll position through this scene, then releases into forward travel again.
- **Transition to next:** Camera resumes dolly, flying *between* the numeral sculptures (through the gap in the arc) into a tighter, more intimate space — the pacing contraction (wide → narrow) signals "we're going deeper into philosophy now."
- **VFX:** Particle crystallization (motes rush from the field edges to form each numeral), no bloom overload — let the held shot breathe.
- **Brand message:** 80+ delivered, 50+ trusted us, 5+ years, 12+ countries — proof, stated once, cleanly.
- **Interaction:** None required — this scene's job is clarity, not play.
- **Perf note:** Particle numerals via GPU instancing only; never individual mesh-per-particle.

---

### SCENE 04 — Architecture Chamber (Philosophy / "const zodize = {...}")
- **Purpose:** This is where "engineering philosophy" gets staged as an actual place — the ship's engine room.
- **Feeling:** Focus, intelligence, quiet confidence.
- **First noticed:** The camera has arrived directly beside the Core again (we've circled back to the protagonist, now more complete than Scene 01 — visible progress) with a holographic terminal panel hovering beside it, live-compiling code.
- **Camera:** Slow **orbit around the Core**, first genuinely "circling the protagonist" beat in the film.
- **Choreography:** Code types itself onto the holopanel in sync with orbit position; each completed line sends a small pulse of light into the Core, and one more of the Core's missing panels **snaps into place** — this scene is a chapter in the Core's assembly, not a standalone terminal graphic.
- **3D objects:** The Core (now ~50% assembled), one holographic terminal panel, thin light-conduits linking panel to Core.
- **Fore/mid/back:** FG — terminal panel, crisp. MID — the Core mid-orbit. BG — the architecture-chamber's structural ribs, dim, industrial.
- **Lighting:** Cooler and more concentrated than surrounding scenes — a single spotlight cone on the Core, everything else near-black (this is the "focus" beat, light design should say so).
- **Material:** Terminal glass = thin holographic pane with soft chromatic edge; Core panels = matte ceramic-metal, only the *new* panel added this scene gets a fresh emissive edge (visually marks progress).
- **Scroll behavior:** Orbit angle scrubbed to scroll; code-typing is time-based within that scrub window so it never outruns the reader.
- **Transition to next:** Orbit completes 180°, revealing an opening in the chamber wall behind the Core that wasn't visible from the front — camera peels off through it into Scene 05.
- **VFX:** Light-conduit pulses, panel-snap flash, subtle depth-of-field pull toward the Core when orbit is near-complete (rack focus).
- **Brand message:** "We design the system before we write the first line."
- **Interaction:** None — protect the one purely contemplative beat in the piece.
- **Perf note:** Typewriter code text is DOM/CSS over a WebGL layer, not 3D text geometry — keeps this scene cheap despite feeling rich.

---

### SCENE 05 — The Foundry (About / Team)
- **Purpose:** Prove this is built by people with judgment, not a faceless system — the humanity beat.
- **Feeling:** Warmth without softness — still precision-engineered, just with a pulse.
- **First noticed:** A workbench-like holographic array where abstract "figures" — stylized human silhouettes rendered as light-rigged low-poly forms (not literal photoreal people, keeps it premium/abstract rather than stock-photo) — are shown mid-collaboration with floating schematic fragments.
- **Camera:** Lateral dolly (side-scrolling past a workshop, like passing windows on a train) rather than push-in — this is a "look sideways into the world" beat, a deliberate camera-language break so it doesn't blur into every other forward-travel scene.
- **Choreography:** Each of the three "expertise pillars" (Fintech Expertise, Enterprise Scale, No Hype Just Code) is a workbench the camera passes; a silhouette figure gestures and a relevant schematic fragment (a wallet icon, a scale/growth glyph, a clean code-block) assembles above their hands as camera arrives.
- **3D objects:** 2–3 abstract light-rig figures, three workbench schematic props, ambient floating tools/fragments.
- **Fore/mid/back:** FG — pillar heading + one-line copy, camera-locked. MID — figure + workbench. BG — foundry structure, warm ember-colored practical lights breaking the cold palette (deliberate — humanity gets the one warm beat in an otherwise cool film).
- **Lighting:** Introduce warm amber practicals (2900K) against the film's cold key — the palette shift is the emotional signal, don't undercut it by keeping everything blue.
- **Material:** Figures = faceted light-mesh (translucent, rigged from light not skin — stays abstract/premium, avoids uncanny-valley photoreal humans).
- **Scroll behavior:** Lateral scrub, same 1:1 feel as Scene 02 corridor but sideways — visitor should physically sense the camera-language shift.
- **Transition to next:** Camera pulls back and up and away from the foundry floor, rising to reveal it sits inside a much larger structure — the reveal-of-scale move that opens Scene 06.
- **VFX:** Warm particulate dust motes in the light shafts, schematic-fragment assembly snaps (same family as Scene 02, for continuity).
- **Brand message:** Deep domain expertise, delivered without noise.
- **Interaction:** None major — maybe a soft parallax tilt on the schematic fragments toward cursor, kept minimal to protect the human warmth of the beat.
- **Perf note:** Figures are the most geometry-expensive asset in the piece — budget 2–3 max, reuse rig across all three pillars with different held props.

---

### SCENE 06 — Product Constellation (Products)
- **Purpose:** Show the breadth of the product universe without it feeling like a grid dump.
- **Feeling:** Scale, ambition, "this is a platform company, not a shop."
- **First noticed:** The pulled-back reveal from Scene 05 resolves into open space containing six satellite modules orbiting a shared gravitational point — each satellite a distinct crystalline product-icon (ERP, FinCore, LendX, WalletOS, PayFlow, StaffHub).
- **Camera:** Slow orbit around the whole constellation, camera itself becoming a seventh satellite — reinforces "you are inside the system."
- **Choreography:** As the camera's orbit angle passes each satellite, that satellite brightens, tilts toward camera, and its glass label deploys; category filter pills (ERP/Fintech/Infrastructure) exist as a foreground HUD that, when tapped, dims non-matching satellites and tightens the orbit radius around the surviving set — filtering as physical narrowing of the world, not a CSS display:none swap.
- **3D objects:** Six satellite product-forms, one dim central gravity-point (implies "the Zodize platform" without literalizing it).
- **Fore/mid/back:** FG — category filter HUD, camera-locked. MID — the constellation. BG — starfield-density data-motes suggesting infinite depth.
- **Lighting:** Cooler, more evenly lit than Scenes 04–05 — signals "systems view," pulling back out of the intimate/warm register.
- **Material:** Each satellite gets a distinct but harmonized facet-color (2 accent hues alternating per category, consistent with Scene 02's rhythm device) — "Coming Soon" status shown as a satellite still partially wireframe/unlit, elegant way to communicate roadmap state spatially.
- **Scroll behavior:** Orbit angle scrubbed to scroll; filter interaction is click-driven and takes over camera orbit target smoothly (no scroll-jack fighting).
- **Transition to next:** Orbit continues past the constellation until it's fully behind camera — ahead, the six satellites' light trails all bend and stream toward one point in the distance: the Core, waiting, still unfinished. This is the setup shot for the film's climax.
- **VFX:** Light-trail bending toward vanishing point, satellite brighten/tilt-on-approach.
- **Brand message:** One engineering standard, six products, all built the same way.
- **Interaction:** Filter pills (functional), satellite hover = slight forward nudge + label.
- **Perf note:** Six satellites is comfortably within budget if each reuses 1–2 base geometries with material/scale variation rather than six bespoke meshes.

---

### SCENE 07 — The Assembly (Why Zodize / Systems Built to Last)
- **Purpose:** The narrative and visual climax — the Core completes. Everything the film has been building toward pays off here.
- **Feeling:** Payoff, inevitability, "of course it comes together like this."
- **First noticed:** The Core, now returned to full frame, still visibly missing its final six panels — one per remaining principle (Architecture First, Security by Default, Scale Without Rebuild, Fintech Precision, Clear Communication, Long-Term Partnership).
- **Camera:** Locked wide **pin** (the film's second and final static beat, deliberately mirroring Scene 03's stillness to bookend the "serious proof" beats) with a slow, almost imperceptible push-in across the whole scrub range — stillness with tension, not a frozen shot.
- **Choreography:** This is your existing pinned-scrub concept, elevated: scroll drives a scrubbed timeline where each of the six panels — currently scattered at the edges of frame, tumbling slowly — accelerates inward, decelerates into place with a hard snap and a shockwave-ring flash, and locks. The corresponding principle's text materializes on a glass plinth beside the Core exactly on the snap frame (motion and copy landing on the same beat is what makes it feel inevitable rather than coincidental). On the sixth snap, the whole Core flares white for one frame and settles into its final, fully-lit state — this is the loudest single VFX moment in the entire experience, and it should be the *only* moment that goes that loud, so it lands.
- **3D objects:** The Core (final assembly), six panel fragments, six glass principle-plinths.
- **Fore/mid/back:** FG — active principle's plinth text, crisp, others dimmed in periphery. MID — the Core, permanently in hero focus this scene. BG — the accumulated environments of every previous scene, faintly visible in the deep distance (the corridor, the foundry, the constellation) — the visitor can see the whole journey behind the Core, cementing "one continuous world."
- **Lighting:** Builds progressively brighter with each panel snap — lighting-as-narrative-device, culminating in the full-flare completion.
- **Material:** Panels transition from dull unlit ceramic (scattered state) to the Core's signature brushed-metal-with-glowing-seam finish only on snap — the material change itself communicates "activation."
- **Scroll behavior:** Pinned scrub, generous scroll distance (this is the emotional peak, give it room — don't rush the one scene the whole film has been pointing at).
- **Transition to next:** Once fully assembled, the Core begins a slow, majestic rotation in place and the camera unpins, gently pulling back and down — descending "below" the Core toward a reflective floor plane that will host the proof/testimonial scenes, like leaving the engine room for the gallery level of the same building.
- **VFX:** This is the one scene that earns heavier bloom, a genuine (brief) shockwave ring per snap, and a real lighting escalation — every restraint decision earlier in the film is what makes this one land.
- **Brand message:** "We don't just write code. We architect systems." — proven, not just stated.
- **Interaction:** None during the pin — protect the payoff from being interrupted by hover states.
- **Perf note:** This is the single scene worth spending the most frame-budget on; everywhere else in the film should be built cheaper specifically to afford this moment. Six discrete assets with baked snap animations, not per-frame physics simulation — keeps it deterministic and light.

---

### SCENE 08 — Proof Vault (Work / Case Studies)
- **Purpose:** Third-party validation, presented as physical evidence you can walk past.
- **Feeling:** Institutional trust, "real companies, real results."
- **First noticed:** Three illuminated vitrines (display cases) set into a reflective gallery floor, each containing a floating abstract UI-fragment sculpture representing a case study (JaguarMarkets, QFS Fountains, the Zodize platform itself).
- **Camera:** Continued descend-and-forward dolly from Scene 07's exit, now horizontal, gallery-walk pacing — deliberately calmer after the Assembly's intensity (pacing contraction after climax = essential, don't sprint straight into more spectacle).
- **Choreography:** Each vitrine's UI-fragment sculpture subtly rotates as approached; a thin data-readout (client, sector, year) racks in beside it. Floor reflections of the Core (visible in the far background) ripple faintly, tying this gallery spatially back to the engine room above.
- **3D objects:** Three vitrine sculptures, reflective floor plane, distant Core visible above/behind through a glass ceiling seam.
- **Fore/mid/back:** FG — case metadata panel. MID — vitrine sculpture. BG — reflective floor + distant glass ceiling revealing the Core above, real spatial continuity payoff.
- **Lighting:** Gallery-spot per vitrine, cooler ambient fill (museum lighting logic).
- **Material:** Vitrine glass = real-time reflective/refractive shader (this is the one scene worth spending a genuine screen-space reflection budget on, since the floor-reflection is doing the "one continuous world" storytelling work).
- **Scroll behavior:** Forward scrub dolly, standard pacing.
- **Transition to next:** Camera rises slightly and turns toward a wall of suspended glass panes ahead, catching fragments of voices/light — leads into Scene 09.
- **VFX:** Floor reflections, vitrine glass refraction, minimal else — let the reflections carry the "premium" read.
- **Brand message:** Delivered, proven, trusted.
- **Interaction:** Click a vitrine to open the case study (standard UI overlay, camera holds position rather than cutting away — never break world continuity for a content view).
- **Perf note:** Real-time reflections are the priciest single effect here — fall back to a pre-baked cubemap reflection on mobile/low-tier rather than cutting the vitrines' emotional job entirely.

---

### SCENE 09 — The Signal Room (Testimonials)
- **Purpose:** Human voices, literally given a place in the world.
- **Feeling:** Trust made personal.
- **First noticed:** Suspended glass panes (echoing the terminal panel language from Scene 04, for system-wide visual grammar) each carrying a quote, softly backlit, gently rotating like chimes in still air.
- **Camera:** Slow lateral drift through the panes (walking through a room of hanging glass), gentle randomized bob suggesting the panes are actually suspended, not just UI cards with a 3D skin.
- **Choreography:** Panes nearest the camera path sharpen and their quote reads clearly; panes further off-axis stay soft and blurred, doing double duty as atmosphere and as a natural "next" affordance (you can see the next quote waiting, softly, before you reach it).
- **3D objects:** Three (or more, in a slow rotating set) glass quote-panes, star-rating rendered as small emissive glyphs, faint avatar-glyphs (abstract initials-in-circle, not literal photos, to preserve the abstracted-premium register established with the Scene 05 figures).
- **Fore/mid/back:** FG — active pane, sharp. MID — adjacent panes, softening. BG — the gallery's reflective floor continuing below, distant Core glow above.
- **Lighting:** Soft, even, warm-leaning (echoing Scene 05's humanity register one more time before the film closes).
- **Material:** Thin holographic glass, consistent with Scene 04's terminal — visual rhyme, not a new material language introduced this late.
- **Scroll behavior:** Lateral scrub, gentle.
- **Transition to next:** Panes part like curtains as camera passes through the last one, revealing bright open space ahead — the film's final chamber.
- **VFX:** Minimal — soft backlight bloom on panes only.
- **Brand message:** Real clients, real outcomes, real trust.
- **Interaction:** None required; optional click-to-expand for full quote.
- **Perf note:** Cheapest content scene in the film — good place to recover frame budget before the finale.

---

### SCENE 10 — The Threshold (CTA + Footer as one continuous close)
- **Purpose:** Convert, with the same confidence as the rest of the film — not a bolted-on contact form at the bottom of a page.
- **Feeling:** Invitation. The film has earned the ask.
- **First noticed:** The camera has arrived in a vast open chamber; the Core (fully assembled, majestically rotating, as left in Scene 07) is now visible in full, distant but dominant, at the far end — and directly ahead is a **portal/gate structure**, glowing, clearly the way through.
- **Camera:** Final push-in, slow and deliberate, straight down the center line toward the portal — the most "cinematic trailer ending" shot in the piece, earned because it's the only time we push straight at something rather than orbiting or traveling past it.
- **Choreography:** Headline ("Ready to build something scalable?") materializes across the portal's aperture using the same data-mote-condensation language from Scene 01 (bookend the film's opening device — full-circle craft). Primary CTA sits as a glowing keystone at the portal's center; secondary CTA as a smaller side-glyph. Footer content (services/products/company links, newsletter) is staged as inscriptions on the portal's inner ring — legible, standard, accessible UI, just wrapped in the world's material language rather than reverting to a flat white footer.
- **3D objects:** The portal structure, the distant completed Core, light-mote stream flowing from Core toward portal (visually: "everything you just saw feeds into this door").
- **Fore/mid/back:** FG — CTA + footer inscriptions, fully standard/accessible DOM content layered over the WebGL, camera-locked and always crisp (this is the one place clarity fully overrides cinema — see §6). MID — the portal. BG — the Core, soft-focus, glowing, final look back at the protagonist.
- **Lighting:** Brightest scene in the film — the door is lit like an exit sign, deliberately, warm-white rather than cold-blue (signals "safe, human, time to act" after a mostly cold/technical palette).
- **Material:** Portal = same brushed-metal-with-glowing-seam family as the Core (they're clearly of the same world), footer inscriptions in the mono instrument type used throughout.
- **Scroll behavior:** This is the natural end of the scrub-driven camera path; once here, page behaves like a normal scrollable footer (standard DOM scroll takes over) — don't force cinematic scroll-jacking onto content whose entire job is fast, boring, reliable usability (email capture, legal links).
- **Transition to next:** None — end of experience. Optional: a subtle "return to top" affordance that replays a fast (2s) version of the opening dolly in reverse, for visitors who want to re-enter rather than reload.
- **VFX:** Portal glow, final data-mote convergence, restrained — this scene sells itself on composition and lighting, not more particles.
- **Brand message:** The invitation, delivered with the same confidence as everything before it.
- **Interaction:** Standard, fully accessible form/link interactions — no novelty here, this is where conversion has to work perfectly on every device and browser.
- **Perf note:** Cheapest possible WebGL load for this scene (it's mostly DOM/CSS over a simple portal mesh + particle stream) — the budget should be nearly exhausted by now, and that's fine, because this scene needs the least of it.

---

## 4. GLOBAL MOTION SYSTEM (the choreography rules that make it feel like one film)

- **Camera grammar, not random motion.** Every scene uses one of exactly four camera moves, reused deliberately: **push-in** (attention/climax — Scenes 00, 04-approach, 10), **forward dolly** (travel/narrative progress — Scenes 02, 06, 08), **lateral dolly** (a look sideways, a change of register — Scenes 05, 09), **orbit** (contemplation, "circling the subject" — Scenes 01, 04, 06). Reusing this small vocabulary across ten scenes is what reads as directed rather than generated.
- **Two static beats only** (Scene 03 and Scene 07) — stillness is a resource, not a default; spend it exactly twice so each spend means something.
- **Reveals are always spatial, never opacity.** Ban list for this build: `opacity: 0 → 1` fades, `translateY` slide-ins, generic `scale(0.9) → scale(1)` pop-ins. Replacement grammar: condensation-from-particles (headlines), assembly-from-fragments (objects), approach-and-brighten (as camera nears a subject), snap-and-flash (the Assembly scene's signature beat, used nowhere else so it stays special).
- **Easing:** cinematic ease curves throughout — heavy `power4`/`expo` eases on camera moves (weight, not bounce), no elastic/back easing anywhere in the piece (that register reads as playful/consumer-app, wrong for this brand).
- **Scroll-to-time mapping:** every scene declares itself either **scrubbed** (camera position is a direct function of scroll position — Scenes 01, 02, 03, 04, 05, 06, 07, 08, 09) or **timed** (an animation plays out on its own clock once triggered — Scene 00 only, briefly). Never mix the two within a single scene; that inconsistency is what makes scroll-3D sites feel broken rather than piloted.
- **Continuity devices (use relentlessly):** recurring data-mote population, one consistent key-light direction, a persistent horizon/fog gradient, and object hand-offs at every scene transition (the thing you're looking at when a scene ends is structurally connected to the thing you see first in the next scene — a gap flown through, a convergence point, a reveal-through-glass). If two adjacent scenes don't share a physical hand-off, that transition needs a redesign.

---

## 5. MATERIAL & LIGHTING BIBLE

- **Palette:** near-black void (`#06070a`) as constant backdrop; **cold key** — electric blue (`#5b7fff`) as the dominant light/material accent throughout; **signal green** (`#12e6a3`) as the secondary accent reserved for "activation/proof" moments (numerals, snaps, CTAs); **one warm exception** — amber (`~2900K`) reserved exclusively for Scenes 05 and 09 (humanity beats) and the Scene 10 portal (invitation beat) — warmth is rationed, which is what makes it mean something when it appears.
- **Recurring materials:** (1) *Chassis metal* — brushed gunmetal with glowing seam lines, used for the Core and the Scene 10 portal (same family = same object-world). (2) *Instrument glass* — thin, frosted, holographic, chromatic-edged, used for every UI panel/label/terminal/quote-pane. (3) *Data-mote* — small emissive translucent points, the connective tissue of the entire piece, present in every single scene at some density.
- **Lighting discipline:** one consistent key-light direction (upper-left, cold) for the entire film — every scene's fill/accent lights can change, but the key never moves. This single rule is what makes 10 wildly different scenes read as one coherent physical space.
- **VFX budget discipline:** bloom is used everywhere but at three intensity tiers (ambient/low, accent/medium, Scene 07 completion/high) — never used at max intensity more than once, or it stops meaning anything. Chromatic aberration and film grain, if used, stay under 2–3% at all times (cinematic lens characteristic, not a glitch-art effect — this brand is precision, not chaos).

---

## 6. ENTERPRISE SAAS CLARITY LAYER (the part that keeps this convertible, not just cool)

A cinematic environment that loses the plot on usability isn't premium, it's a portfolio piece. Non-negotiables layered on top of everything above:

- **Persistent wayfinding HUD:** a slim, always-visible progress rail (10 tick-marks, current scene lit) doubling as a scene-jump menu — click any tick to smooth-travel directly there. This is the single most important usability addition: it turns "a scroll experience you're trapped in" into "a world you can navigate."
- **Skip/escape hatch:** a persistent, unobtrusive "Skip to content" / standard nav bar toggle that switches to an instant, ordinary anchor-linked scroll mode — for return visitors, screen-reader users, and anyone on a deadline. The cinematic mode is the front door, not the only door.
- **CTAs are never inside the cinema's uncertainty.** Every scene's primary action (Learn more, Start a Project, filter, case study link) is rendered as camera-locked foreground UI — sharp, legible, standard hit-target size (44×44px min), never subject to motion blur, DOF softening, or the camera's orbit. Cinema in the background, software-grade usability in the foreground, always.
- **Loading is honest.** Scene 00's ignition sequence doubles as real asset preloading — if heavier scenes (07, 08) aren't ready when their turn comes, they get a graceful lower-fidelity placeholder rather than a stall; the film never blocks on a spinner mid-journey.
- **Legibility over atmosphere, always, without exception, for body copy and forms.** Fog/bloom/DOF are tuned per-scene specifically so the FG text plane never drops below 4.5:1 contrast — verified per scene, not assumed.

---

## 7. TYPOGRAPHY & DESIGN SYSTEM

- **Display:** a geometric/technical sans with distinct character (in the spirit of Space Grotesk or a comparable technical display face) — used sparingly, large, for the handful of headline moments that "materialize" in-world.
- **Body/UI:** a highly legible humanist sans (Inter-class) for all glass-panel copy, footer, forms — this is the typeface that has to work at small sizes over a moving background, so legibility wins over character here.
- **Instrument/mono:** a monospace face (JetBrains Mono-class) for every eyebrow label, data readout, terminal content, and HUD element — this is what sells "systems/engineering" at a typographic level and ties every scene's UI language together.
- **Kinetic type rule:** headline type is treated as a 3D-adjacent object (condenses from particles, sits on a camera-locked plane, catches the scene's key light on its edge) rather than a flat HTML string with a fade transition — type is a citizen of the world, not an overlay on top of it.
- **Scale discipline:** one modular type scale used everywhere (no one-off font sizes per scene) — display headlines clamp between roughly 32–88px across breakpoints, body settles at 16–18px, mono labels at 11–13px with wide letter-spacing for that "instrument panel" read.

---

## 8. FRONTEND FEASIBILITY & DEVICE TIERING (implementation-aware, direction-first)

**Recommended stack:** Three.js as the single persistent WebGL scene (not React Three Fiber per-section remounts — this experience is fundamentally one scene graph, which favors an imperative Three.js core with a thin state layer) + GSAP ScrollTrigger driving the scrub-timeline camera rig, with all HUD/CTA/footer content as real DOM layered on top (per the clarity-layer rule above). This matches the "Pattern 1: Layered Separation" approach — Three.js scene, GSAP timeline layer, DOM UI layer — which is exactly what a scroll-driven cinematic marketing experience calls for.

**Three explicit device tiers**, because true continuous-camera 3D travel is not something every device should attempt:

1. **Desktop / high-tier (full film).** Everything above, full fidelity, full camera choreography.
2. **Tablet / mid-tier.** Same scene structure and camera path, reduced particle counts, simplified reflections (baked cubemap instead of real-time in Scene 08), DOF approximated with CSS blur layers instead of a real post-process pass.
3. **Mobile / touch (the "highlight reel" mode — this is the important call).** Continuous free-camera travel on a 6-inch touchscreen tends to read as disorienting or motion-sickness-inducing rather than cinematic. Recommendation: **keep every scene, keep the object language and the material bible, but replace continuous scrub-camera travel between scenes with discrete locked "postcard" shots per scene** (camera holds one strong composition per scene, subtle ambient motion only, hard-cut or quick cross-fade — not scroll-scrubbed dolly — between scenes). Visitors still get the world, the Core, the Assembly payoff, and the material/lighting language; they don't get seasick doing it with a thumb.

**Performance guardrails (apply throughout):** GPU-instanced particles only, capped device pixel ratio (≤2), pause/unmount off-screen scene renderers via IntersectionObserver, LOD swaps on the Core geometry itself (full facet detail only within Scenes 01/04/07, simplified proxy elsewhere), and a hard total-scene-weight budget so Scene 07's completion moment can afford to be the most expensive frame in the film without the rest of the page suffering for it.

---

## 9. ACCESSIBILITY & USABILITY PASS

- **`prefers-reduced-motion` isn't a toggle you bolt on last — it's a second, fully-designed edit of this same film**, not a broken version of it: same ten scenes, same copy, same brand narrative, delivered as static/gently-animated compositions with instant scroll-linked reveals in place of camera travel. Nobody using this mode should feel like they got the "lite" version — they should feel like they got a calm, confident version.
- **Keyboard + screen reader:** the wayfinding rail (§6) is a real, tab-accessible nav list under the hood; every scene's DOM content (headline, body, CTA, form) exists in a sensible reading order regardless of its visual/camera position, so a screen-reader pass reads as a normal, well-structured page.
- **Motion-sickness mitigation:** no continuous roll/tilt beyond the ±3° cursor-parallax ceiling stated in Scene 01; orbit speeds capped; no scenes with simultaneous fast camera rotation + fast particle motion (pick one per beat).
- **Contrast & focus:** every foreground text plane independently contrast-checked against its worst-case background frame (not just its average frame); visible focus rings on all interactive elements even against a dark, glowing backdrop (a light outer-glow focus ring rather than a default blue browser outline, so it survives the palette without disappearing).
- **No flashing hazard:** Scene 07's completion flare is a single soft frame, not a strobe — verified against seizure-safety flash-rate guidance regardless.

---

## 10. AWARD-LEVEL CRITIQUE & REFINEMENT (the cuts that protect the vision)

Being honest about where this concept could fail, and what to cut before it does:

- **Risk: "everything is a spectacle" fatigue.** Ten scenes of equal intensity would numb the visitor by Scene 05. **Mitigation already built in above** — the two static beats, the rationed warm palette, the single loudest-VFX-moment rule, and the tiered bloom intensities all exist specifically to protect Scene 07's payoff. If anything in the build starts creeping toward "let's add a bit more glow here too," that's the instinct to override.
- **Risk: cinematic ambition eating usability.** Mitigated structurally by §6 (camera-locked foreground UI, always-on wayfinding rail, skip mode) — but worth stating as a build principle: **any time a motion decision and a usability decision conflict, usability wins**, full stop, no exceptions, including in Scene 07.
- **Risk: mobile becomes an afterthought port instead of a designed experience.** Mitigated by treating mobile as Tier 3 with its own designed camera language (§8) rather than "the same thing, but slower." Build and review the mobile tier as its own storyboard pass before shipping, not as a QA fix afterward.
- **Risk: this reads as generic "Awwwards template" 3D (floating glass panels + particles + bloom) rather than distinctively Zodize.** What earns distinctiveness here, specifically: the Core as a singular, evolving, story-carrying protagonist object (most sites this genre never commit to one recurring hero object across every scene); the six-panel Assembly sequence tied directly to the brand's own six stated principles (not a generic reveal — it's the actual "why us" content, staged); and the rationed, disciplined use of the warm palette exception, which most sites in this genre never bother with (they just glow blue everywhere). Protect these three specifically — they're what separates this from a stock "3D hero + particles" template.
- **Recommendation before full build:** prototype the highest-risk, highest-payoff sequence first — **Scene 01 → Scene 02 transition** (establishes the camera grammar, the fly-through hand-off device, and whether the piloted-scrub feel actually works on real hardware) plus **Scene 07 in isolation** (the single most complex choreography and the moment the whole brand case rests on). If those two hold up on mid-tier hardware, the rest of the film is lower-risk execution of the same established language.

---

## NEXT STEP

This document is the direction — not yet the build. Given the scope (a genuinely bespoke, single continuous 3D scene graph across ten narrative beats with three device tiers), I'd suggest one of two paths from here:

1. **Prototype first** — I build Scenes 01–02 plus the Scene 07 Assembly sequence as a working proof-of-concept, so the camera grammar and the payoff moment can be judged on real hardware before committing to the full ten-scene build.
2. **Full build, phased** — I build the whole experience in the sequence above, shipping scene-by-scene so you can review and redirect early rather than at the end.

Either way, happy to start whenever you're ready — just say which.
