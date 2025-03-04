---
layout: page
title: Temporal Relation Extraction
description: Leverage language models and formal logic to extract temporal relations of events from text
img: assets/img/project_Temporal/header.png
importance: 3
category: work
---

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <a href="https://arxiv.org/pdf/2112.00894" target="_blank">
            <button class="btn btn-primary">View Research Paper</button>
        </a>
    </div>
</div>


Our research focuses on improving temporal relation extraction from unstructured text. We've developed a novel model that employs deep learning techniques and integrates temporal logic for more effective relation extraction. This approach addresses the limitations of traditional models by generating a synthetic dataset, which is then used in conjunction with dependency parsers and a temporal logic solver. This method improves the model's ability to learn and understand complex temporal relationships in text.

## Approach

Our approach utilizes a layered architecture to extract temporal relations from text:

1. **BERT embeddings** capture contextual information from the input
2. **Bi-LSTM layer** adds sequential understanding 
3. **Biaffine attention mechanism with MLPs** focuses on the dependency (arc) and the type of relationship (relation) between events

This structure enables precise predictions of temporal relations, forming a graph that represents the interconnectedness of events within the text.
<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/project_Temporal/arch1.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/project_Temporal/arch2.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Architecture diagram of our temporal relation extraction model.
</div>

## Parser Component

Our system incorporates a specialized parser that processes input text to identify events and temporal expressions. The parser works by:

1. Recognizing event mentions and their attributes (tense, aspect, modality)
2. Identifying temporal expressions (dates, times, durations, frequencies)
3. Establishing initial temporal anchoring points
4. Creating a preliminary structure of the text's timeline

The parser leverages dependency parsing techniques and named entity recognition to isolate event structures. This preprocessing step significantly enhances the quality of input for the subsequent temporal relation extraction model.

## Temporal Logic Solver

A key innovation in our approach is the implementation of a temporal logic solver that:

1. Enforces temporal consistency across detected relations
2. Resolves conflicts using constraint propagation algorithms
3. Completes the temporal graph using transitive closure rules
4. Integrates domain-specific knowledge where available
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/project_Temporal/training.png" title="Training Process" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Temporal Logic Solver is used for generating the error signal for the model. This enforces temporal consistency across detected relations.
</div>

The solver applies Allen's interval algebra and point-based temporal calculus to maintain logical coherence within the extracted relations. This ensures that impossible temporal configurations (such as circular dependencies) are eliminated from the final output.

## Performance

Benchmarks show that in a fixed amount of time, our model processes more sentences than previous studies, while providing comparable accuracy. This is primarily due to our model design that removes the event extraction dependency for relation extraction. The prediction of temporal relation labels is performed in parallel with arc prediction, eliminating the need for the non-parallelizable, nested for-loop for extracting event pairs in previous studies.

## Advantages

This work is valuable because it exploits the logical structure of temporal relation tasks. By aligning with temporal logic principles and employing sophisticated language models, it has the potential to surpass current performance benchmarks in understanding textual timelines. This has applications in areas that require detailed, precise comprehension of events over long time horizons.

## Limitations

The approach may be less impactful in certain contexts, particularly in light of advances made by large language models (LLMs). These LLMs have demonstrated superior accuracy in temporal relation tasks and are adept at recognizing even subtle and obscure events. This capability stems from their extensive training on diverse datasets, enabling them to understand and predict complex temporal patterns.

## Future Potential

This work might be particularly useful in the future given significant breakthroughs in Neuro-symbolic AI, where the structured approach to temporal relation extraction could complement the patterns learned by large language models.