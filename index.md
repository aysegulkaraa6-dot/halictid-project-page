---
---

# Canalized plasticity in caste evolution

*Companion page to the GEvol 2026 poster. Ayşegül Kara, Evolutionary Biology,
LMU München. PI: Sonja Grath. Last updated 23 September 2026.*

> **Lead paragraph, written last.** Two or three sentences: what the project
> asks, what the two tests found, where it stands.

**Contents**

[Project scope](#project-scope) ·
[Background](#background) ·
[The system](#the-system) ·
[What was pre-specified](#what-was-pre-specified-and-when) ·
[Test 1](#test-1-regulatory-redundancy) ·
[Test 2](#test-2-expression-canalization) ·
[Limits](#what-the-tests-could-and-could-not-measure) ·
[Next](#where-this-goes-next) ·
[Questions](#questions-for-the-committee) ·
[Methods](#methods-in-full) ·
[References](#references)

## Project scope

This is a DFG-funded project on the regulatory basis of eusociality in halictid
bees, running in three work packages: predicting regulatory elements across
halictid genomes, quantifying selection and testing for convergence across
independent origins, and asking whether regulatory switches are novel or
co-opted from existing developmental pathways.

**Why halictids.** Eusociality is not fixed in this group. It has been gained
and lost repeatedly, and species at every stage are alive and collectable
today, which is unusual. The phylogeny on the poster shows five of them:

| Species | Social state |
|---|---|
| *D. dentriventris* | solitary, ancestrally so |
| *H. quadricinctus* | solitary, secondarily |
| *H. rubicundus* | socially polymorphic |
| *L. marginatum* | eusocial |
| *L. malachurum* | eusocial |

Eusociality is gained once on the branch leading to the eusocial clade, and
lost again in *H. quadricinctus*. Two points follow. "Solitary" in this group
usually means derived rather than ancestral, so a solitary halictid is not a
proxy for the ancestral state. And because polymorphic and reverted lineages
still exist, a comparison across them is possible in principle rather than
having to be reconstructed.

**Everything below concerns one genome only.** *L. malachurum* is the case
study used to build and validate the prediction pipeline before it is applied
across the other genomes. Results here are properties of this species and this
dataset, not claims about halictids in general. Where the work bears on the
wider comparison it is flagged as such.

> **Fill in:** the genome set. The repository only evidences *L. malachurum*
> and *Nomia melanderi*, so list the rest yourself rather than trusting me.
> Also expand the abbreviated species names above, since the poster carried
> only the initials and I am not going to guess the genera.

## Background

*L. malachurum* is obligately eusocial. Every colony produces workers, and then
queens, every year. That is the starting point of this work rather than something
it tests. The question is what regulatory architecture sits behind a caste system
like that, and whether it carries any signature of how the system came about.

One account says caste systems begin as plasticity. A solitary ancestor already
adjusts development to conditions, and in halictids the plausible raw material is
seasonal and nutritional polyphenism: females provisioned poorly or late in the
season emerge smaller, with less developed ovaries. Something like both phenotypes
is producible before eusociality exists. Selection then acts on the shape of that
conditional response, making the outcome more reliably predicted by the cue
(West-Eberhard 2003; Jones and Robinson 2018). Note what this does not claim.
Caste here is still environmentally set, so a larva is not genetically a queen.
What is proposed to have changed is how cleanly the environment's decision gets
executed.

**Canalization** is that increase in reliability: the same cue giving the same
outcome, with fewer intermediates and less scatter, despite variation in genes or
environment. Two things follow. It is a property of individual development rather
than of the colony, so obligate caste production is the observation it tries to
explain and not a restatement of it. And it is comparative. More reliable than
what needs an answer, and one obligately eusocial species does not supply one.
That comparison belongs to the five-species arm of the project, not here.

What this case study can ask is narrower: does caste-associated regulation in this
genome have the properties the framing predicts. Two were tested.

**Regulatory redundancy.** A switch that must fire reliably should be buffered,
for instance by controlling its genes through several regulatory elements rather
than one. Caste loci should then carry more redundant regulatory architecture
than the background.

**Tighter expression control.** If the outcome is reliable, the expression
underlying it should be too, so caste genes should vary less between individuals
of one caste than other genes do.

The project proposal reaches the redundancy prediction by a different route.
There, extra elements are a hiding place, letting regulatory variation accumulate
unexpressed until conditions expose it and selection can act (genetic
accommodation). Same direction, different claim: one is about how caste regulation
was assembled, the other about how reliably it now fires. Test 1 does not separate
them.

**How caste regulation is located.** Neither account is a claim about queens or
workers as such, so both tests need a way to point at caste-associated regulation
using adult data. Caste-biased expression is that pointer: genes differentially
expressed between queens and workers stand in for genes whose regulation has
something to do with caste. The comparison locates, it does not date. It cannot
say when or whether anything changed, and treating those genes as the relevant
ones is an assumption rather than a definition. It is taken up in
[what the tests could and could not measure](#what-the-tests-could-and-could-not-measure).

Both predictions are inferences from the framing, not consequences of it. How much
weight they bear is the subject of this page.

## The system

*L. malachurum* is a primitively eusocial sweat bee with an annual cycle, so all
three adult female roles can be sampled in one season from one population.

- **Castes:** foundress, queen, worker.
- **Tissues:** brain and fat body, dissected separately.
- **Samples:** 44 RNA-seq libraries. Queen n = 5 per tissue, worker n = 9,
  foundress n = 8.
- **Caste-biased genes:** differentially expressed between castes. Primary
  contrast queen versus worker, DESeq2, padj < 0.05 and |log2FC| >= 1.
- **Predictions:** regulatory elements predicted from the *L. malachurum*
  assembly, scored against *Drosophila* training data. Section 5.1 covers what
  that licenses.

**One confound.** Foundress samples were collected April 2024, queen and worker
July 2023. Caste and season are fully confounded for foundress, so any foundress
result is caste plus batch. Queen versus worker is unaffected, which is why it
is the primary contrast.

**One control.** Brain versus fat body identity is tested the same way as caste.
A pattern appearing there too is not caste-specific.

## What was pre-specified, and when

> Both predictions, including effect direction, written down before analysis;
> say where that is recorded. Mark which later analyses were follow-ups rather
> than pre-registered tests.

## Test 1. Regulatory redundancy

### 5.1 What SCRMshaw predicts, and what it does not

> What it is, the three scoring methods and what each computes, why all three
> are run. Then the limit: enhancer-like sequence, not demonstrated function.

### 5.2 From windows to predictions

> The chain with parameters: 500 bp windows at 25 offsets, three scores,
> nfrac <= 0.05, per-instance elbow, 10 bp signal, MACS2 stage 1, stage-2 elbow
> on amplitudes, final peaks. Include the two failures that shaped it: IMM's
> degenerate elbows under N-masking, and the zero-fill bug.

### 5.3 From predictions to redundant loci

> The permutation test: the question it answers, why raw counts are not
> interpretable, the shuffling constraint, 1000 replicates, empirical p, BH
> within training set. Defines the independent variable.

### 5.4 From loci to genes

> Testable locus and why the filter exists. Binary and count redundancy. Why
> "at least one significant training set" is the right threshold and where the
> multiplicity actually lives. Gene as unit of analysis. Different gene
> universes per method.

### 5.5 Result on 36 training sets

> The null with odds ratios, and the power audit. State what it rules out and
> to what effect size.

### 5.6 Result on 74 and 86 training sets

> Fat body unchanged, brain depleted under IMM and merged. Numbers, direction,
> caveats, and the two earlier findings pointing the same way. Hold until the
> follow-up lands.

### 5.7 What the method disagreement means

> Peak profiles, base-pair Jaccard, the IMM/HexMCD asymmetry, what merged is.
> Hold until the heterogeneity test lands.

## Test 2. Expression canalization

### 6.1 Prediction and design

> The directional prediction, six caste by tissue groups, how dispersion is
> estimated.

### 6.2 Result

> The reversal, in all six groups.

### 6.3 Robustness

> Mean-expression correction and the caste-matched fix. The objection each
> answers.

### 6.4 The brain versus fat body control

> The same pattern appears in the tissue comparison, so it is not
> caste-specific.

### 6.5 What the literature already said

> The prediction runs against published work. Summarise the findings, not just
> the citations: expression variance is not low where function is high, and
> differentially expressed or condition-responsive genes are systematically
> noisier (Sigalova et al. 2020; Lehner 2010, and whatever else the literature
> pass turns up). This section is why the Test 2 result is unsurprising in
> hindsight, and it belongs before rather than after the result is discussed.

## What the tests could and could not measure

> Bounded claims, not apologies. What is ruled out and to what effect size.
> What could not be measured: functional redundancy, an uncanalized baseline.
> Then the stage argument: canalization acts at the switch, adults are past it,
> so what was measured is how tightly the outcome is held. A canalized switch
> predicts fewer intermediates rather than lower variance, visible only in
> larvae.
>
> Then the gene-set argument, which is the larger of the two: caste-biased genes
> are the difference between two finished outcomes, not the machinery that chose
> between them. A gene can be queen-biased purely as a consequence of ovary
> activation without its regulation having changed at the origin of caste. Both
> tests inherit this proxy and neither can check it. Larval data during the
> commitment window is what replaces the proxy with genes that actually respond
> to the cue.
>
> **Pending (asked Ana, 23 Sep):** whether larvae are being collected now, and
> whether larval RNA-seq exists from phase 1. If phase-1 larval data exists the
> stage limitation is addressable with data in hand rather than a future plan,
> which changes this section and the next one substantially.

## Where this goes next

> The three open questions plus the analyses now running. For each: what it
> would establish, what data it needs, what would count as a negative result.

## Questions for the committee

> Written as questions, not a summary.

## Methods in full

> Parameters, thresholds, software versions, and the universe definitions
> (retained36, all48, retained74, all86, new38) with what each is for.

## Data and code

> Where reports, tables and scripts live. What is available on request.

## References

> Everything cited anywhere on this page and on the poster, in one list.
> Currently expected: West-Eberhard 2003; Jones and Robinson 2018;
> Kantorovitz et al. 2009; Kazemian et al. 2011; Asma et al. 2024;
> Rohlfs and Nielsen 2015; Sigalova et al. 2020; Lehner 2010;
> Masel et al. 2007.
