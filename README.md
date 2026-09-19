# Synaptic Plasticity as Short-Term Memory

**DataForge 2026 · Pathway Track · Problem Statement Round (PS1)**

## Concept

### Central claim

Recent neural activity can temporarily change synaptic strength, allowing a small network to store short-term associations. However, decay and competing writes can make those memories interfere with one another.

This project turns that idea into an interactive learning artifact. Instead of only reading about synaptic plasticity, learners can write associations into a small synaptic memory, observe their strength, let them decay, introduce a competing association, and test what the network recalls.

## Interactive artifact

The main artifact is a self-contained browser-based simulation.

**[Open the interactive Synaptic Memory Lab](https://homelander2005-creator.github.io/Tejas/)**

It requires no sign-in, external libraries, or build process.

### Main interactions

- **Learning rate (η):** controls how strongly each new write changes a synapse.
- **Retention:** controls how much existing synaptic strength survives from one time step to the next.
- **Write A → X:** creates or strengthens an association between A and X.
- **Compete with A → Y:** repeatedly writes a competing association and demonstrates interference.
- **Query A:** reads the strongest current association for A.
- **Advance time:** applies decay without adding a new write.
- **Reset:** returns the model to its initial state.
- **60-second experiment:** runs a compact sequence showing learning, decay, interference, and adaptation.
- **Synaptic memory matrix:** makes the current state directly observable.
- **Live synaptic view:** visualizes the relative strength of competing associations.

## Toy model

The artifact uses the following simplified update rule:

`w(t+1) = retention × w(t) + η × pre(t) × post(t)`

where:

- `w(t)` is the current synaptic strength.
- `retention` determines how much existing strength remains.
- `η` is the learning rate or write strength.
- `pre(t)` indicates presynaptic activity.
- `post(t)` indicates postsynaptic activity.

This is an educational toy model. It is **not** presented as the official Brain-inspired Dynamic Hardware (BDH) equation or as a biologically complete model of synaptic plasticity.

## What the learner can observe

The artifact is designed around three observable behaviors:

### 1. Learning

Writing A → X increases the corresponding synaptic strength. Repeated writes make the association stronger.

### 2. Forgetting / decay

Advancing time reduces existing synaptic strength according to the retention parameter. This demonstrates how a short-lived memory can fade without further reinforcement.

### 3. Interference and adaptation

After A → X has been learned, repeatedly writing A → Y creates a competing association. The learner can observe the two strengths crossing and see how the recalled association changes.

With the default parameters, the toy model demonstrates that adaptation does not happen instantaneously after the environment switches: several competing writes may be required before the new association becomes stronger than the old one. This result belongs to the toy model and should not be interpreted as a biological or BDH benchmark.

## Connection to BDH

The Brain-inspired Dynamic Hardware (BDH) provides the broader motivation for treating memory as a changing synaptic state.

The primary BDH paper describes working memory during inference in terms of synaptic plasticity and Hebbian learning with spiking neurons. It reports that individual synapses can strengthen when the model processes specific concepts.

Our artifact uses a deliberately smaller and easier-to-understand abstraction:

**recent activity → local synaptic update → changing synaptic state → recall**

The interactive model therefore illustrates the *idea* of synaptic memory and plasticity. It does not claim to reproduce the architecture, equations, training procedure, or performance of the full BDH system.

## Learning objectives

After using the artifact, a learner should be able to:

1. Explain how a synaptic state can act as a temporary memory.
2. Describe how repeated activity can strengthen an association.
3. Explain how retention/decay causes a temporary memory to fade.
4. Observe how competing writes can interfere with an existing association.
5. Relate the simplified mechanism to the synaptic-memory idea used in BDH.
6. Distinguish an educational toy model from evidence about a full biological or AI system.

## Intended audience

The artifact is designed for students and technically curious learners who know basic ideas such as neurons, connections, or vectors but do not need prior expertise in neuroscience or BDH.

The interface is intentionally small so that the effect of each control can be understood directly.

## Suggested 60-second walkthrough

A judge or learner can demonstrate the core idea quickly:

1. Start with the empty synaptic matrix.
2. Click **Write A → X** several times.
3. Click **Query A** and observe that X is recalled.
4. Use **Advance time** to observe decay.
5. Write **A → X** again to restore the association.
6. Click **Compete with A → Y** repeatedly.
7. Watch A → Y grow while A → X weakens through competition and decay.
8. Run the experiment to compare plastic memory with a frozen-memory counterfactual.

This walkthrough makes the central claim testable rather than relying only on explanatory text.

## Evidence and research basis

The project is grounded in recent primary research and supporting technical material, including:

- Kosowski et al. (2025), *The Dragon Hatchling: The Missing Link between the Transformer and Models of the Brain.*
- Rodriguez, Guo, and Moraitis (2022), *Short-Term Plasticity Neurons Learning to Learn and Forget.*
- Brito and Gerstner (2024), *Learning what matters: Synaptic plasticity with invariance to second-order input correlations.*
- Koprinkova-Hristova et al. (2023), *Learning cortical hierarchies with temporal Hebbian updates.*

See `REFERENCES.md` for the full citations and links.

## Project structure

```text
.
├── AI_DISCLOSURE.md
├── README.md
├── REFERENCES.md
├── index.html
├── artifact/
│   └── index.html
└── docs/
    ├── blog.pdf
    └── one_page_concept_summary.pdf
```

## Running locally

No installation is required.

1. Download or clone the repository.
2. Open `artifact/index.html` in a modern web browser.
3. Interact with the controls.

The artifact is implemented with HTML, CSS, and vanilla JavaScript and has no external runtime library dependency.

## Publishing the artifact

The repository is configured for GitHub Pages using the `main` branch and repository root.

The public interactive artifact is available at:

**https://homelander2005-creator.github.io/Tejas/**

## Accessibility and usability

The artifact includes:

- keyboard-accessible controls,
- visible focus states,
- responsive layouts for smaller screens,
- readable labels and explanatory text,
- reduced-motion support where applicable,
- charts with explicit axis labels and values.

## Limitations

This project intentionally simplifies several aspects of real neuroscience and BDH.

- The synaptic update rule is a toy educational abstraction.
- The network is extremely small compared with biological neural systems and modern AI models.
- The model does not simulate realistic neuronal dynamics, biochemical mechanisms, or biological timescales.
- The interference experiment demonstrates behavior of this toy rule rather than establishing a biological result.
- The project does not claim that its numerical results reproduce BDH results.

These limitations are important because the artifact is intended to teach a mechanism and encourage experimentation, not to serve as a scientific simulator.

## Reproducibility and provenance

The interactive artifact was written specifically for this educational submission using HTML, CSS, and vanilla JavaScript.

- No external JavaScript library is required.
- No external font or image asset is required.
- Graphics are generated within the page.
- No pretrained weights or external datasets are used.
- Research claims are attributed to the cited sources.
- The project includes an AI assistance disclosure describing where AI tools were used during development.

## Supporting materials

- `docs/blog.pdf` — explanatory blog/article accompanying the artifact.
- `docs/one_page_concept_summary.pdf` — concise concept summary.
- `REFERENCES.md` — research references and evidence notes.
- `AI_DISCLOSURE.md` — disclosure of AI assistance.

## License and source record

The interactive code was written for this submission. Research material remains the property of its respective authors and publishers. See `REFERENCES.md` and the provenance notes above for attribution and source information.

---

**Core idea:** a synapse can be treated as a small piece of changing state. Recent activity can write into that state, retention can let it fade, and competing activity can overwrite or interfere with what was remembered.
