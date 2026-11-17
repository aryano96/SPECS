# Learn AR with SPECS — Winning Playbook

> Private working notes. **Delete this file (or move it out) before you make the submission repo public.**
> Researched 2026-11-17. Items marked ⚠️ could not be read directly from the Devpost page and should be confirmed there.

---

## 1. What this hackathon actually is

| | |
|---|---|
| **Name** | Learn AR with SPECS (Devpost *Learn* / learning hackathon, Round 2) |
| **Tagline** | "Learn to design for glasses. Your coding agent builds the Lens, no SPECS required." |
| **Platform** | Snap **SPECS** AR glasses, built in **Lens Studio**, demoed in Lens Studio's **preview** on a laptop. No glasses needed. |
| **Prizes** | 1st **$1,250** · 2nd $750 · 3rd $500 (one winner each, $2,500 total) |
| **Deadline** | **Dec 7, 2026, 5:00 pm EST** ⚠️ confirm on the page |
| **Live project review** | **Thu Dec 3, 12:00 pm ET**. Attend it, show your work-in-progress, get feedback from the judges. |
| **Judges** | Darlyze Calixte (Developer Marketing Manager, Devpost) and Joe Holmes (AI Learning Hackathon Architect, Devpost). These are the people who designed the learning process, so following it faithfully counts. |
| **Mode** | Online, solo allowed. Tracks: AR/VR, Design, ML/AI. |
| ⚠️ URL note | One listing says Round 2 lives at `learn-specs-10-26.devpost.com`. Make sure you're **registered on the round whose deadline is Dec 7**. |

### Judging criteria (4)
1. **Design**: Is it a *complete, coherent product experience*, not just a technical proof of concept?
2. **Technical Implementation**: How well is it built, and how well did it use **CLAD, Lens Studio, and the Lens Studio MCP**?
3. **Innovation/Idea**: How creative and novel is it, and does it differ from existing concepts?
4. **Presentation**: Does the video show it working **end to end**? Does the pitch say **what problem, who it's for, why it matters**? Is it easy to follow?

**Judges will not run your project.** The video *is* your project as far as they're concerned.

### What to submit
- **Video under 3 minutes**, **public on YouTube**, recorded from Lens Studio's preview.
- **Public GitHub repo** containing the **Lens Studio project folder with the `devpost/` folder inside it** (`devpost/design-brief.md` etc.).
- Devpost write-up (standard sections). ⚠️ Check the "What to Submit" section on the page for any extra fields.

---

## 2. The toolchain (what each piece is)

- **Lens Studio** (Snap's desktop editor, Mac/Windows). Use the latest version (Devpost tested on **5.24**; LEAF needs ≥ 5.22).
- **Lens Studio MCP**: the server inside Lens Studio that lets Claude Code drive the editor. Start it via *AI Assistant → AI Model Context Protocol (MCP) → Configure Server → Start Server*. In Claude Code, `/mcp` should show `lens-studio` connected.
- **CLAD** (Closed Loop Agentic Development): Snap's Claude Code plugin (`ls-clad`) with agents/skills like `specs-experience-builder`, `verify-preview`, `specs-leaf-*`. It builds the Lens.
- **LEAF** (Lens Evaluation & Automation Framework): automated tests that simulate pinch/grab/press in the preview. Commands: `/specs-leaf-install-packages`, `/specs-leaf-write-scenarios`, `/specs-leaf-run-in-preview`.
- **SIK / UI Kit**: Spectacles Interaction Kit + UI Kit. Use them for *all* interactions so the mouse can drive them and LEAF can test them.
- **Skill pack** `challengepost/learn-specs`: one skill, `plan-lens`, which interviews you and writes `devpost/design-brief.md`.

### Setup, in this exact order (on YOUR computer, not a cloud session)
1. Lens Studio → **SPECS** → **Base Template** → **File > Save As** (creates the project folder).
2. Open a terminal **in that folder** (the one with `.esproj` and `.mcp.json`), Lens Studio still open, and start `claude`. Approve the `lens-studio` MCP server.
3. Install CLAD: https://developers.specs.com/docs/clad/setup/setup-ai/claude-code-setup
4. `npx skills add challengepost/learn-specs --all -y`
5. Say `plan-lens` (20–30 min interview → `devpost/design-brief.md`).
6. `/clear`, then paste:
   > Read devpost/design-brief.md and build it for SPECS. Follow the brief closely. Get the basic flow working first, then add detail. Write and run LEAF tests for each done criterion, and tell me which pass.
7. `git init` in the project folder **right away** and commit after every working step. A visible commit history is evidence of real process.

Troubleshooting: MCP https://developers.specs.com/docs/clad/troubleshooting/troubleshoot-lens-studio-mcp · Plugin https://developers.specs.com/docs/clad/troubleshooting/troubleshoot-lens-studio-plugin

---

## 3. How to win each criterion

### Design: "a complete, coherent product"
Most entries will be a demo of one effect. Yours should feel like an **app**:
- **A start state** (short intro or "Start" pinch), **a core loop**, and **an end state** (done, summary, score, "nice work"). The judge should see the whole journey.
- **One spatial moment, done extremely well.** Don't add features; polish the one moment.
- Follow the **four habits** the judges teach (they will look for these):
  1. Info sits **on the thing it's about**, not a floating website.
  2. **Shows when needed, then gets out of the way.**
  3. **A few big targets. Pinch is the new tap.**
  4. **Keep it where they're already looking**; a sound or small arrow for anything out of view.
- Comfort numbers: content **0.6–1.6 m away, slightly below eye level**; view is narrow (~37°×32°); arms low; **no black or dark UI** (additive display = black is invisible); light, readable text.
- Feedback on every action: highlight on hover, a sound on pinch, a small animation on success.

### Technical Implementation: "how well did you use CLAD, Lens Studio, MCP"
Make the use of the toolchain **visible and provable**:
- Build through **CLAD + MCP**, not by hand. Keep the brief → build → design-notes loop.
- **LEAF tests for every done criterion, all passing.** Save the pass/fail report into `devpost/` (e.g. `devpost/leaf-results.md`) and **show it in the video for 5 seconds**.
- Keep a **`devpost/iteration-log.md`**: each round of design notes you gave CLAD and what changed (e.g. "Moved step card 15 cm lower next to the pan; made Next 2× bigger; re-ran tests: 5/5 pass").
- Fill in the brief's **After the build** section honestly, with "logic proven" / "feel unproven" labels. The judges wrote that rubric; doing it shows you learned what they're teaching.
- Clean README in the repo root: what it is, the video link, how it was built (CLAD/MCP/LEAF/SIK), done criteria with test status.

### Innovation: "different from existing concepts"
- **Avoid the examples the course itself uses.** Many of the ~250 participants will copy them: cooking timers and risotto, translating a sign, pool-table aiming, a basketball defender, recipe following, generic workout counters, plant care.
- Strong ideas come from **your own life**: a niche hobby, job, skill you're practicing, a moment when your hands are busy or your eyes need to stay up.
- **Combine two or three strengths of glasses** (shares your view + draws in the world + leaves your body free). The course says "Good AR uses one. Great AR combines them."
- Pass the "phone test": state in one sentence why it's *worse* on a phone.

### Presentation: the video decides everything
Under 3:00, public YouTube, voiceover plus captions. Suggested structure:

| Time | Content |
|---|---|
| 0:00–0:15 | **Hook**: the real problem in one sentence, and who has it. |
| 0:15–0:30 | **Why glasses**: which strengths it uses; why a phone fails here. |
| 0:30–2:00 | **End-to-end demo in Interactive Preview**: start → core loop → finish, uninterrupted. Narrate *design choices* ("the card only appears when you need it", "one big pinch target because your hands are messy"). |
| 2:00–2:35 | **How it was built**: brief → CLAD via Lens Studio MCP → **LEAF results on screen (N/N passing)** → one iteration example (before/after). |
| 2:35–2:55 | **What's proven vs. unproven on real glasses**, what's next, and close. |

Tips: record at 1080p+, hide your desktop clutter, move the preview camera slowly, rehearse the clicks, cut dead time. Rewatch it once as a stranger: is the problem clear in the first 15 seconds?

---

## 4. Stay inside the preview (the #1 way to lose)

Everything in your **done criteria and video must work in Lens Studio's preview** with keyboard and mouse.

- ✅ **Works:** walking around (WASD, Q/E, right-drag look), real-scale objects, buttons/sliders/panels, pinch/grab/drag/throw via mouse, spatial sound, simple physics, animation, 3D models, text.
- 🔁 **Needs a stand-in:** recognizing real objects (use a "Found it" button or a hard-coded result), real surfaces (virtual table/wall), real routes (virtual markers + "Next" button), AI answers (hard-coded fallback), voice (always pair with a button), live data (sample data).
- ❌ **Can't show:** two-hand or custom gestures, hand speed or poses, live camera vision/SnapML, memory across sessions, persistent anchors, multiplayer/Connected Lenses.
- 🚫 **Out of scope:** recording, identifying, or following people without consent; face recognition.

---

## 5. Timeline (today = Nov 17 → deadline Dec 7)

| Dates | Goal |
|---|---|
| **Nov 17–19** | Register (correct round). Install Lens Studio, create project, MCP, CLAD, skill pack. `git init`. Pick your idea. |
| **Nov 20–23** | Run `plan-lens`, approve the brief. First CLAD build. Basic flow working, LEAF installed. |
| **Nov 24–30** | Iterate with design notes (log each round). Make all LEAF tests pass. Add start/end states, sound, feedback, polish. |
| **Dec 1–3** | Rough video cut. **Attend the live review Dec 3, 12 pm ET** and apply the feedback. |
| **Dec 4–5** | Final video, README, Devpost write-up, make repo public. |
| **Dec 6** | **Submit**, a full day early. Verify the video is public and the repo link works in a private/incognito window. |

---

## 6. Devpost write-up template

- **Inspiration**: the personal moment that sparked it.
- **What it does**: the one spatial moment, in plain words.
- **Why glasses**: which of the three strengths; why it's worse on a phone.
- **How I built it**: plan-lens interview → design brief → CLAD in Claude Code via Lens Studio MCP → SIK/UI Kit → LEAF tests (N/N pass) → design-note iterations.
- **Challenges**: e.g. faking recognition within preview limits; placement and comfort tuning.
- **Accomplishments**: complete flow, all tests passing, design habits applied.
- **What I learned**: designing for glasses vs. screens (the four habits), directing an agent with design notes.
- **What's next**: what real SPECS hardware would unlock (real recognition, real hand feel). Be honest about "feel unproven".
- **Built with**: Lens Studio, SPECS, CLAD, Lens Studio MCP, LEAF, Spectacles Interaction Kit, UI Kit, Claude Code, TypeScript.

---

## 7. Final pre-submit checklist

- [ ] Registered on the correct round; submitted before Dec 7 5 pm EST
- [ ] Video < 3:00, **public** on YouTube, shows full flow end to end, states problem / audience / why it matters
- [ ] Repo **public**; contains the Lens Studio project + `devpost/` (brief with `status: approved`, After-the-build notes filled, LEAF results, iteration log)
- [ ] README with video link, description, toolchain, test status
- [ ] Every done criterion demonstrable in preview; LEAF passing
- [ ] No dark/black UI; text readable; content in view, 0.6–1.6 m, below eye level
- [ ] No recording/identifying of people
- [ ] This playbook file removed from the public repo

## Sources
- Devpost page: https://learn-specs.devpost.com/ (resources: https://learn-specs.devpost.com/resources)
- Skill pack: https://github.com/challengepost/learn-specs
- CLAD docs: https://developers.specs.com/docs/clad · LEAF: https://developers.specs.com/docs/clad/tools/test-your-lens-with-leaf
