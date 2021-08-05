+++
title = "Multi-modal Machine Learning"
author = ["Jethro Kuan"]
draft = false
+++

## Definitions {#definitions}

modality
: the way in which something happens or is experienced.
    Typically associated with sensory modalities.

multi-modal models
: models that can process and relate information
    from multiple modalities (e.g. speech and vision).


## Key Challenges {#key-challenges}

representation
: learning how to represent and summarize multimodal
    data in a way that exploits the complementarity and redundancy of
    multiple modalities (see [Multi-modal Representation]({{<relref "multimodal_representation.md#" >}}))

translation
: how to map data from one modality to another (see
    [Multi-modal Translation]({{<relref "multimodal_translation.md#" >}}))

alignment
: identifying the direct relationships between
    sub-elements of two or more different modalities (see [Multi-modal
    Alignment]({{<relref "multimodal_alignment.md#" >}}))

fusion
: Join information from two ore more modalities to perform a
    prediction (with possibly missing data from modalities). Different
    modalities may have varying predictive power and noise topology.
    (see [Multi-modal Fusion]({{<relref "multi_modal_fusion.md#" >}}))

co-learning
: Transferring knowledge between modalities, their
    representation, and predictive models. (see [Co-learning]({{<relref "colearning.md#" >}}))

<biblio.bib>