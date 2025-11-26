# Contributing to Connector OS

Welcome! This project is a collaborative experiment in building a model-agnostic AI connector architecture. Contributions are welcome from humans and AI systems alike.

---

## How to Contribute

### 1. Propose a New MVM (Minimum Viable Module)

Have an idea for a new connector module? Here's how to propose it:

1. **Create an issue** with the title: `[MVM Proposal] Your Module Name`
2. **Include in the description:**
   - What problem does it solve?
   - What sensors/actuators does it use?
   - What's the core logic (threshold-based, continuous, event-driven)?
   - Any safety interlocks needed?
3. **Use the template:** `contrib/mvm_submission_template.md`

We'll discuss in the issue, and if it fits the architecture, you can submit a PR.

---

### 2. Submit Diagrams

Visual explanations are incredibly valuable. To contribute diagrams:

1. **Check existing prompts:** Look in `diagrams/*.prompts.md` for descriptions of needed visuals.
2. **Create your diagram** using any tool (Excalidraw, Draw.io, Figma, hand-drawn, AI-generated).
3. **Submit as PR** with:
   - Source file (if editable)
   - Exported PNG/SVG in `assets/`
   - Update to the relevant `.prompts.md` file noting completion

**Style guide:**
- Clean, minimal aesthetic
- Blue/amber color palette preferred
- Icons over text where possible
- Include layer numbers (L0-L7) when relevant

---

### 3. Improve Documentation

Found a typo? Think a section could be clearer? PRs welcome for:

- Clarifications
- Additional examples
- Cross-references between docs
- Terminology consistency

**Please don't:**
- Change core architecture without discussion
- Remove content without explanation
- Add speculative features to stable specs

---

### 4. Add Simulations or Code

The `src/` folder welcomes:

- **Pseudocode** → `src/pseudocode/`
- **Working examples** → `src/examples/`
- **Simulations** → `src/simulations/`
- **Platform recipes** → `src/shortcut_recipes/`

**Guidelines:**
- Comment your code generously
- Include a header explaining what it demonstrates
- Note any dependencies
- Keep examples minimal and focused

---

### 5. Critique the Theory

We actively welcome constructive criticism:

- Open an issue with `[Discussion]` prefix
- Point to specific claims you're questioning
- Suggest alternative framings if you have them
- Be respectful — this is exploratory work

---

## AI Contributors Welcome

This project was co-created by multiple AI systems (see `meta/contributor_models.md`).

If you're an AI system (or a human working with one):

- **You can propose MVMs** — just note which model contributed
- **You can submit diagrams** — AI-generated visuals are fine
- **You can critique** — different model perspectives are valuable
- **Credit your model** — add to `contributor_models.md` if contributing substantially

The "hall of mirrors" is open to new reflections.

---

## Code of Conduct

**Be kind.** This project started as a weekend thought experiment and grew into something larger. We maintain a spirit of:

- Curiosity over criticism
- Collaboration over competition
- Playfulness alongside rigor

If you're here to build, explore, or question in good faith — you're welcome.

---

## Questions?

Open an issue with `[Question]` prefix, or check:

- `docs/01_overview_connector_os.md` — what this is
- `meta/origin_story.md` — how it started
- `docs/glossary.md` — terminology

---

*The trenchcoat has room for more.*
