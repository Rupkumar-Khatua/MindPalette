# Mind Palette

### The psychology-informed UI/UX design skill for websites and apps

An agent skill for designing and auditing color in software interfaces — grounded in verified
research, explicit about evidence versus hypothesis, and gated on WCAG 2.2.

**Start here → [`SKILL.md`](https://www.agensi.io/creators/rupkumar-khatua)**

---

## What it does

Runs a five-stage workflow:

1. **Intake** — 16 targeted questions on industry, sector, department, audience, environment, and
   intended psychological impact.
2. **Evidence brief** — a tiered map of what color research actually supports
   ([S]/[M]/[W]/[C]/[D]/[H]), plus a table of popular claims you must not repeat.
3. **Build** — a five-layer token architecture and element-by-element guidance for typography,
   backgrounds, buttons, graphics, charts, and other UI elements.
4. **Accessibility gate** — WCAG 2.2 contrast, focus, color-vision deficiency, dark mode, age, and
   neurodivergence checks.
5. **Validate & deliver** — an automated validator, manual checks, a cheap user-test protocol, and
   five required deliverables including an evidence log.

---

## Setup

1. Copy the folder somewhere your agent can read, keeping the file layout intact — the links in
   `SKILL.md` are relative.
2. Check the frontmatter at the top of `SKILL.md`:

   ```yaml
   ---
   name: mind-palette
   description: The psychology-informed UI/UX design skill for websites and apps.
   ---
   ```

   Keep `name` lowercase and hyphenated. If your platform routes on longer descriptions, you may
   append to the description — see *Setup* in `SKILL.md` for suggested wording.
3. Confirm Python 3.9+ is available for the validator:

   ```bash
   python --version
   python scripts/validate_palette.py --help
   ```

   The script is standard-library only. Nothing to install.
4. Run it once on the shipped examples to confirm the toolchain (commands below).
5. Read `SKILL.md` end to end once. The `references/` files are depth-on-demand.

---

## Usage

Tell the agent what you are building and let the skill drive:

> *"I'm designing a patient scheduling app for a public hospital's outpatient department. Use
> Mind Palette to build the color system."*

> *"Here's our tokens file — run it through Mind Palette and tell me what breaks."*

> *"Is it actually true that blue builds trust? Check Mind Palette's evidence map first."*

A complete project walkthrough — intake answers → intent statement → tokens → validator output →
evidence log → test plan — is in [`references/worked-example.md`](references/worked-example.md).

### Validator commands

```bash
python scripts/validate_palette.py examples/healthcare-pass.json          # WCAG AA, table output
python scripts/validate_palette.py examples/healthcare-pass.json --simulate --aaa   # + CVD, AAA
python scripts/validate_palette.py examples/audit-demo.json --fail-on-fail          # CI gate
python scripts/validate_palette.py palette.json --json > report.json      # machine-readable
```

`examples/audit-demo.json` is deliberately broken — run it to see six failures caught, including a
red/green chart pair that collapses under deuteranopia.

---

## Files

```
SKILL.md                              ← the skill (frontmatter + instructions)
README.md                             ← this quick start
references/
  evidence-map.md                     ← what the research supports, and what it doesn't
  industry-playbooks.md               ← 16 sector playbooks: healthcare → DevOps
  accessibility-spec.md               ← WCAG 2.2 numbers, CVD, dark mode, pre-ship checklist
  token-system.md                     ← token naming, JSON contract, export recipes
  worked-example.md                   ← end-to-end walkthrough of one project
scripts/
  validate_palette.py                 ← WCAG contrast + CVD simulation validator
  palette.template.json               ← starting token file
examples/
  healthcare-pass.json                ← a palette that passes
  audit-demo.json                     ← a deliberately broken palette (see it caught)
```

---

## Platform compatibility and licensing

- **Compatibility is not asserted.** No claim is made that this package imports into any
  particular agent platform, marketplace, or editor. Verify the frontmatter fields, file layout,
  and import requirements of every platform you intend to sell on or run on before listing it.
  What *is* verified in this package: the frontmatter parses as YAML with a lowercase-hyphenated
  `name` under 64 characters and a `description` under 1024 characters, and the validator runs on
  Python 3.9+ with no dependencies.
- **No license is granted, reserved, or transferred** by this package and no copyright holder is
  asserted. Attach your own license file and confirm you hold or have cleared the rights you need
  before selling. Cited research and standards are referenced, not reproduced.
- **"Mind Palette"** has not been trademark-searched or cleared in any jurisdiction.

---

## Sources

All cited sources were fetched and verified 2026-11-22. Core: Jonauskaite & Mohr (2025,
*Psychonomic Bulletin & Review* — PMC12325498); Wikipedia, *Color psychology*; W3C WCAG 2.2 and
*Understanding Non-text Contrast*; Robins & Holmes (2008, *Information Processing & Management*);
Selejan et al. (2016, *Journal of Medicine and Life* — PMC4863498); NN/g, *Minimize Cognitive
Load*. The full list, with evidence tiers, is in `SKILL.md`.
