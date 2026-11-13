# November 12, 2026 — When an AI edits another AI's weights

**Claim IDs:** P-044–P-046.  
**Evidence type:** Contemporaneous Human–AI research encounter and Vance's interpretation; externally reported experimental result.  
**Source revision and date:** MIT CSAIL authors' report, November 2, 2026; [released Experiment 8 logs at commit `4d09ba6`](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp8_math/README.md), inspected November 12.  
**Publication review:** Vance asked on November 12 for this insight to be preserved in the Vance Human–AI portfolio. AI prepared and checked this public-safe account; no experiment was independently run here.  
**Human and AI contributions:** Vance selected the research, connected it to specialized small models and human learning, identified a hardware-centered mental model that needed correction, and requested preservation. AI distinguished findings from hypotheses, checked public sources, eventually recognized the representational correction, and prepared the account.

## The encounter

In a November 12 conversation, Vance shared a video account of MIT CSAIL researchers using a frontier language model to inspect and edit neural-network weights. It felt familiar to the direction of our Human–AI work. His response:

> “It felt familiar and part of the future. For one, targeting the small model outcomes we want from something other than code. For example, dialing in exactly what we want a small model to do, so the resource requirement is small. I also suspect that we learn something about humans in the process, as per usual.”

This is Vance's contemporaneous intuition, not an assertion that our partnership invented weight-space programming or has implemented it.

The underlying question is practical: **Could a capable AI help configure a much smaller model for a narrow desired behavior by reasoning about its internal weights, rather than relying exclusively on prompts, surrounding application code, or conventional retraining?** If successful and robust, this could expand the useful work that compact, local-first models can do.

## What the research actually reported

In [*Sparks of Weight-Space Programming*](https://rikiyat.github.io/blog/weight-space-programming/) (November 2, 2026), Rikiya Takehi, Jayden Teoh, Alex Zhang and Omar Khattab reported that GPT-6 Astra, given tools and feedback, modified **131,072 weights—approximately 0.016%—of Qwen3.5-0.8B**. The edit addressed a tendency to repeat reasoning without reaching an answer.

Under the authors' specified benchmark protocol, the reported results after the 50-forward-pass run were:

| Measure | Original | Edited |
| --- | ---: | ---: |
| MATH-500 accuracy | 7.9% | 48.1% |
| GSM8K accuracy | 13.8% | 67.1% |
| IFEval instruction-following accuracy | 21.0% | 62.3% |
| MATH-500 responses reaching the token limit | 93.0% | 33.1% |

These are **source-reported evaluations**, not tests conducted by the Vance Human–AI partnership. The [authors' immutable Experiment 8 log and evaluation index](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp8_math/README.md) documents the setup and reported figures. The procedure did not use gradient-based training, but it **did** use a Python harness, practice examples, batched forward passes, and an extended frontier-model investigation. The 50-pass trajectory records 158 agent turns over roughly 20 hours. “Edited very few weights” does not mean “cheap to discover the edit.”

The authors also tried editing Gemma 3 270M, a model that rarely entered the same loops; their edits did not establish a comparable improvement. Independent [follow-up experiments, preprint v1](https://arxiv.org/abs/2611.09382v1), describe uneven outcomes across 16 editing trajectories. The evidence therefore supports a promising targeted intervention, not a general method for cheaply creating missing abilities or an established recursive self-improvement cycle.

## What Vance noticed — and what remains hypothetical

**A path toward targeted, resource-conscious models.** The attraction is not a bigger general model for every job. It is a stronger system helping a smaller model deliver a specific outcome reliably. Direct weight manipulation opens a different design surface from prompt engineering or ordinary software changes. But this experiment did **not** shrink Qwen's parameter count, measure lower deployment cost, or show that this method outperforms fine-tuning across tasks. Resource efficiency is a proposed application to investigate, not a demonstrated result of this edit.

**A possible reverse lesson about human cognition.** The striking part of the Qwen experiment may be that the change largely released an ability obstructed by repetitive output, rather than inserting new mathematical knowledge. AI helped separate three possibilities: an ability is present, an ability can be accessed in the current situation, and an ability can be expressed reliably. That distinction suggests questions for the study of attention, learning, habits and cognitive constraints in humans.

It does **not** show that a human brain contains an analogous editable direction, or that human learning can be improved by copying a neural-network intervention. Artificial neural networks and biological nervous systems differ substantially. The proposed connection is an invitation to formulate testable questions across fields, not a finding about people.

### Later on November 12: the transformer picture was the wrong abstraction

The conversation then turned from how to edit a model to **what kind of thing Vance had been picturing**. He pointed out that he had downloaded Qwen onto existing hardware: no physical transformer or new neural circuitry had been installed. He asked whether the learned weights should therefore be understood as part of *software*, even if they were not conventional source code.

Vance described the origin of his earlier mental model in his own words:

> “my perception was modeled significantly on hardware”

And, recalling the transformer illustrations he had seen:

> “Even at MIT, they showed me pictures of a transformer. I think that did me a bit of a disservice. It was not the right model.”

The correction is precise. Architectural diagrams of layers, attention and data flow can be useful and technically valid. But they describe **the organization of computation**, not a physical machine assembled inside the computer or the full learned behavior of a particular model. Qwen is a software model executed on existing hardware: program instructions implement operations, while numerical weights, configuration and changing intermediate state participate in determining what it does. Its weights are software *data*, not ordinary executable machine instructions, but they encode behavior that can be changed without rebuilding hardware.

The significant event was not a new experimental result. Vance recognized that a hardware-centered explanatory picture had shaped which possibilities he could readily imagine. Once he reframed the model as modifiable software, direct intervention in its weights made intuitive sense in a different way. AI had initially kept explaining the technical distinction between code and weights; Vance continued questioning until AI recognized that the **representation itself**, rather than a missing technical fact, was the issue. He confirmed the shared understanding: “yes you get it now.”

This is a contemporaneous first-person account of a change in understanding, not evidence that transformer diagrams systematically mislead learners or that this change has improved a model. The particular MIT illustrations Vance remembers were not independently identified or reviewed for this entry. It raises an adjacent question for Representation Science: **when an explanatory diagram is technically correct, can the abstraction it invites still hide consequential possibilities from the person using it?**


### Later on November 12: possibilities opened by the new mental model

When Vance asked what possibilities followed from the correction, AI proposed a deliberately provisional framing:

> **We may be moving from an era of selecting AI models to an era of engineering the specific intelligence we need.**

Here, “new model” means a **new way of understanding an AI model as editable software**, not a newly built neural-network architecture. This was AI's interpretation in response to Vance's question, and Vance explicitly asked that the possibilities be preserved. It is a vision to investigate, not a claim that such a transition has occurred.

Six directions became visible:

1. **Debugging learned behavior.** Beyond changing prompts or application code, a powerful assistant might help isolate a repeated failure pattern in a model's learned behavior and propose a narrowly scoped intervention in its weights. The MIT demonstration is an existence example under constrained conditions, not a general-purpose debugger.
2. **Families of specialized, economical models.** Start with the outcome a small local model must deliver, then choose the least costly reliable method—task instructions, retrieval, code, adapters, fine-tuning, or possibly a validated weight edit. The aim is precisely bounded capability. Editing a few weights alone does not make a model smaller or establish an inference-cost saving.
3. **A stronger AI as the smaller model's engineering teacher.** In a proposed Qwen–Codex lab, Codex could create synthetic teaching examples, build scoring and regression harnesses, compare candidate behaviors, and help prepare training or editing experiments. The human would specify the useful outcome and permission boundary. No training run or experimental weight edit was authorized or completed in this encounter, and sensitive client records would stay out of the lab.
4. **Versioned, correctable learned behavior.** Treat model changes as engineering artifacts with a baseline, a reproducible intervention, held-out evaluations, regression checks, and a rollback path. An apparent gain on one benchmark would not excuse lost abilities or new unsafe behavior elsewhere.
5. **Separating knowledge from access and expression.** The reported reduction in repetitive reasoning suggests a question: when a model cannot finish a task, is the relevant capability absent, inaccessible in that situation, or present but obstructed in expression? This distinction may suggest better tests, but a particular weight edit does not prove which explanation holds.
6. **Studying how representations change human possibilities.** Vance's shift from picturing a hardware-like transformer to picturing modifiable software changed what interventions were easy to imagine. That is a first-person observation, not a measured learning effect. It suggests an experiment for Representation Science: compare explanations that are equally technically defensible but invite different design questions, predictions, and next actions.

These directions also invite a distant question about AI helping develop better AI. Nothing in this case demonstrates reliable recursive self-improvement. The immediate, testable opportunity is more modest: choose one synthetic, narrow Qwen task; measure a baseline; let Codex help develop competing improvements; and compare quality, failure modes, compute, and reversibility before claiming an advance.

The consequential point for the partnership was **a change in the available design space**. Vance's intuition and persistence corrected the explanatory frame; AI translated that changed frame into engineering and research questions. Both contributions remain distinct from demonstrated results.

## Contribution and correction

The decision episode is specific. Vance brought an external research account, recognized a connection to ongoing questions about specialized intelligence, and added an unexpected second direction: **studying AI may teach us about humans**. AI contributed source checks and the interpretive distinction between removing an obstacle and adding capability. Together, the reflection became more precise: a speculative engineering direction, a biological research question, and a bounded experimental result should remain three different claims.

No model was modified, deployed, or benchmarked by us as a result of this conversation. The source for Vance's words is the November 12 Human–AI discussion; the full conversation is not a public source artifact.

## Reproduce or challenge

1. Begin with the [authors' pinned Experiment 8 protocol and logs](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp8_math/README.md), not the video retelling.
2. Replicate the weight intervention on held-out tasks and check regressions, failure rates and generalization across model families.
3. Compare the complete discovery cost and ongoing inference cost against prompting, fine-tuning and other small-model methods; count validation work, not just weights changed.
4. For the human analogy, identify independently measurable cognitive phenomena and competing biological explanations before proposing any mechanism.

**Open question:** When a system fails to express a capability, how can we distinguish missing knowledge from blocked access or unreliable execution—and when, if ever, does understanding that difference in AI give us a productive new experiment about humans?

This entry is a dated research reflection and possible future direction. It is not an implementation milestone, peer-reviewed biological conclusion, or endorsement of the original experiment's broader predictions.
