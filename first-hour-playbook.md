# First Hour Playbook — Zipline FDE Hackathon

**The whole game in one line:** the first hour decides the day. Most candidates
start building in minute 2 and discover in hour 5 they built the wrong thing.
You spend the first hour *scoping*, then build something narrow that can't fail.

Keep a timer visible. Each phase is hard-boxed. When the box ends, move on even
if it's not perfect — a decided-and-moving beats perfect-and-stuck.

---

## Phase 0 — Capture the ask exactly (0–5 min)

Don't open an editor yet. Write these down verbatim:

- [ ] **The literal assignment.** Copy their wording. Don't paraphrase it into
      what you hoped it'd be.
- [ ] **Who's the client?** Name the person/persona in the room you have to
      convince. What's their job? They are 50% of your grade.
- [ ] **What did they give me?** Sample data? A persona? A format? List it.
- [ ] **Deliverable + format + time.** What does "submitted" look like, and how
      long do I actually have?

> If anything is ambiguous, that's not a problem — that's the test. Ambiguity is
> deliberate. Your job is to resolve it with judgment, not to wait for clarity.

---

## Phase 1 — Scope it out loud with Plan mode (5–15 min)

Open Codex, `/plan` (Shift+Tab), and make it interview you. This does double duty:
better spec **and** it visibly demonstrates "operating, not prompting."

Force these four answers before any code (this is Codex's own prompt structure):

- [ ] **Goal** — the outcome, as a result not a method. ("A cited Go/No-Go memo
      an expansion lead brings to deal review.")
- [ ] **The ONE artifact.** Not a platform. One output object. Say it in a
      sentence. If you can't, you haven't scoped it yet.
- [ ] **One user, one Tuesday moment.** Which real person, doing which recurring
      task, is this for? If you can't name the meeting it slots into, narrow more.
- [ ] **Done when** — the verifiable finish line. ("Memo renders for a real site,
      every claim cites a source line or is flagged UNVERIFIED, verifier passes.")

---

## Phase 2 — The cut list (15–25 min)

Decide *now* what you are and aren't building. Write three columns:

- [ ] **Build deep** (1–2 things) — the core artifact + the one feature that
      mind-blows. This is where the verifier/trust loop lives.
- [ ] **Build shallow** — real data, transparent logic, no fake ML. A visible
      weighted score beats a black box.
- [ ] **Gesture at in the pitch only** — adjacent realms you show the
      architecture *could* extend to, but never build. ("These are fields the
      record is built to hold; future agents fill them.")

**Anti-command-center check:** if your plan has more than ~2 panes or needs a
legend to read, you're building for experts. Cut back to the single artifact.
Re-read the rubric line: *"a small tool doing something useful which blows a
client's mind will rank higher than a command center made for experts."*

- [ ] **Pick the ONE demo moment** — the 10 seconds that makes the client gasp.
      Build backwards from that.

---

## Phase 3 — Stand up the operating system (25–40 min)

Drop in the reusable spine. You are not starting from scratch — this is prepped.

- [ ] `AGENTS.md` in place, re-pointed at today's actual ask (repo layout, how to
      run, build/test/lint, the cite-or-flag guardrail, what "done" means).
- [ ] `.codex/config.toml` — model + reasoning defaults, `[agents]` limits.
- [ ] Subagents in `.codex/agents/` — keep only the ones today's ask needs;
      rename/repoint the rest. Verifier stays **read-only**.
- [ ] `docs/code_review.md` wired so `/review` enforces the trust rubric.
- [ ] **Cite-or-flag rule is live:** every factual claim resolves to a source
      line or is labeled UNVERIFIED. This is your differentiator — protect it.
- [ ] **One stage runs end to end** on one real input. Green before you go wide.

> Setup discipline: most "quality" problems are really setup problems — wrong
> working directory, missing write access, wrong model default. Get this clean
> here and the rest of the day is smooth.

---

## Phase 4 — Pre-stage real inputs + the trust surface (40–55 min)

- [ ] **Pre-stage 1–3 real examples** (real city, real address, real PDFs) so the
      live demo never fetches cold and dies on stage. Cache them locally.
- [ ] **Build the trust surface as visible features, not polish:**
      - click a claim → jump to the source line
      - at least one honest **UNVERIFIED** flag on screen (the feature, not the bug)
      - a per-section confidence label
- [ ] Run the full loop on a staged example. Watch the **verifier reject → repair
      → re-verify** cycle actually happen. That live loop is your strongest proof.

---

## Phase 5 — Lock the demo + write the pitch (55–60 min)

- [ ] **Freeze the demo path.** The exact clicks you'll do on stage. Don't
      improvise live; rehearse the staged run once.
- [ ] **Write the 3-beat pitch now**, while you still have time:
      1. **Open in the client's words** — the messy status quo they live in today.
      2. **The wow** — type the input → cited artifact comes out live.
      3. **The trust + change** — click→source, point at UNVERIFIED, then land it
         in Marcus's frame: one analyst's week → minutes; every run makes the next
         one faster.
- [ ] **Tie 2 design choices back to the email out loud** ("you said messy
      inputs and trust, so we built the verifier loop"). Listening to the client
      *is* the FDE job — doing it visibly is rare.

---

## Decision rules for when you're under pressure

- **Assigned a realm you didn't prep?** Don't force your prepped tool onto it.
  Keep the *spine* (dossier object + fetch→extract→analyze→draft→verify + cite-or-flag),
  swap the input agents. The method transfers; the domain is just config.
- **Running out of time?** Cut the wow feature, never the verifier loop. A small
  honest cited tool > a big tool that might be lying.
- **Tempted to add a second screen/feature?** Ask: does it serve the ONE demo
  moment? If not, it goes in the "gesture at" column.
- **Stuck for >10 min on a build problem?** Stub it with real static data and
  move on. The demo doesn't care if the score is computed or pre-baked.
- **Client in the room goes quiet/skeptical?** That's the 50%. Address the doubt
  directly — show them the source line, show them the flag. Don't talk past it.

## Red flags you're off track

- You're 90 min in and haven't produced a single end-to-end output.
- Your demo needs you to explain a UI before they understand it.
- You can't state your tool in one sentence to a non-coder.
- Nothing on screen is ever uncertain — a flawless demo reads as untrustworthy.
- You're polishing CSS before the verifier loop works.

---

**The thing to remember when nerves hit:** they are not grading the cleverest
tool. They are grading whether you can take a messy real problem, carve it to
something useful, make it trustworthy, and convince a non-coder it's real.
You've prepped the system. The first hour is just pointing it at their problem.
