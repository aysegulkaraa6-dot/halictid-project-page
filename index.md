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
[Proposal and scope of work](#what-the-proposal-asked-for-and-what-was-done) ·
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
ones is an assumption rather than a definition. Test 2 bears on this assumption directly, and it is taken up
again in [what the tests could and could not measure](#what-the-tests-could-and-could-not-measure).

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
  assembly, scored against *Drosophila* training data. The section on what SCRMshaw predicts covers what that licenses.

**One confound.** Foundress samples were collected April 2024, queen and worker
July 2023. Caste and season are fully confounded for foundress, so any foundress
result is caste plus batch. Queen versus worker is unaffected, which is why it
is the primary contrast.

**One control.** Brain versus fat body identity is tested the same way as caste.
A pattern appearing there too is not caste-specific.

## What the proposal asked for, and what was done

The inherited proposal reasons in four steps. SCRMshaw predicts enhancer locations
from sequence using *Drosophila* training data. Some loci carry several
predictions, which is regulatory redundancy. Redundancy buffers regulatory
variation, letting it accumulate unexpressed until conditions expose it. Therefore
caste-biased genes, taken to be the genes whose regulation changed with the origin
of eusociality, should carry more redundancy than other genes.

The last step is the testable claim, and **Test 1 is that test**, run as the
proposal frames it: caste-biased status against locus redundancy, separately for
the three scoring methods and both tissues. Most of the effort in this leg went
into building the machinery the test needs, which is why the prediction pipeline
takes up as much space below as the result does.

**Test 2 is not in the proposal.** It follows from the same framing rather than
from the proposal text. Buffering is a claim about variance, and within-caste
expression variance is measurable directly in the 44 RNA-seq samples, with no
enhancer predictions anywhere in the chain. It was added because it tests the
underlying idea using data that does not depend on cross-order transfer.

Both tests had their hypothesis and their predicted direction written down before
the analysis ran. That matters most for Test 2, where the prediction was lower
dispersion in caste-biased genes and the result came out the other way in every
group (`prompts/canalization-test-prompt.md`, 15 September 2026).

**Added afterwards.** These were decided once a result was in hand, and are
follow-ups rather than tests of the proposal's claim:

- Rerunning Test 1 on 74 and 86 training sets, after the first run excluded 12
  defective ones. The brain depletion appears here.
- Characterising what the three scoring methods actually predict, and the
  heterogeneity and tissue-matching work that came out of it.
- A power audit, to bound what the null excludes.
- The mean-expression correction and the caste-matched reclassification in Test 2,
  each answering a specific objection.
- The WGCNA module arm of Test 1.

## Test 1. Regulatory redundancy

### What SCRMshaw predicts, and what it does not

> What it is, the three scoring methods and what each computes, why all three
> are run. Then the limit: enhancer-like sequence, not demonstrated function.

### From windows to predictions

> The chain with parameters: 500 bp windows at 25 offsets, three scores,
> nfrac <= 0.05, per-instance elbow, 10 bp signal, MACS2 stage 1, stage-2 elbow
> on amplitudes, final peaks. Include the two failures that shaped it: IMM's
> degenerate elbows under N-masking, and the zero-fill bug.

### From predictions to redundant loci

> The permutation test: the question it answers, why raw counts are not
> interpretable, the shuffling constraint, 1000 replicates, empirical p, BH
> within training set. Defines the independent variable.

### From loci to genes

> Testable locus and why the filter exists. Binary and count redundancy. Why
> "at least one significant training set" is the right threshold and where the
> multiplicity actually lives. Gene as unit of analysis. Different gene
> universes per method.

### Result on 36 training sets

> The null with odds ratios, and the power audit. State what it rules out and
> to what effect size.

### Result on 74 and 86 training sets

> Fat body unchanged, brain depleted under IMM and merged. Numbers, direction,
> caveats, and the two earlier findings pointing the same way. Hold until the
> follow-up lands.

### What the method disagreement means

> Peak profiles, base-pair Jaccard, the IMM/HexMCD asymmetry, what merged is.
> Hold until the heterogeneity test lands.

## Test 2. Expression canalization

Test 2 was meant to test the canalization idea on data that does not depend on
enhancer prediction. It did not manage that. What it produced instead is a check
on the caste-biased gene definition that both tests rely on, and that is how it
is presented here: the design and the result first, then the control that changed
what they mean.

### Prediction and design

The prediction was directional and fixed in advance: if caste determination is
canalized, genes that distinguish castes should show *lower* within-caste
expression dispersion than other genes.

Six groups, one per caste and tissue combination. Dispersion is the pydeseq2
per-gene estimate, refit separately within each group rather than taken from one
whole-dataset fit, so no information is shared across the groups being compared.
11,802 genes before filtering, roughly 10,200 to 10,900 tested per group after it.
Egg-laying workers were excluded at n = 2 per tissue. Queen and worker were
tested one-sided in the predicted direction. Foundress was two-sided and
exploratory, because a foundress has not committed to an irreversible trajectory
the way a queen or a mature worker has, and no direction could be justified in
advance. The brain versus fat body comparison was specified as a required control
rather than an optional extra. Run 16 September 2026.

### Result

The prediction is not merely unsupported. The effect runs the other way, in every
group.

Caste-biased genes are *more* dispersed than other genes in all six. The
one-sided queen and worker tests return p = 1.0, which is as non-significant as a
one-sided test can be, because the effect is large and points the wrong way.
Foundress, tested two-sided, gives p = 1.4 x 10^-169 in brain and 1.6 x 10^-87 in
fat body. Median dispersions, caste-biased against the rest:

| Group | caste-biased | other | rank-biserial r |
|---|---|---|---|
| queen, brain | 0.122 | 0.019 | -0.58 |
| worker, brain | 0.120 | 0.021 | -0.51 |
| foundress, brain | 0.133 | 0.030 | -0.54 |
| queen, fat body | 0.074 | 0.033 | -0.25 |
| worker, fat body | 0.150 | 0.071 | -0.31 |
| foundress, fat body | 0.104 | 0.051 | -0.31 |

There is also a dose response. Within caste-biased genes, the size of the caste
difference predicts the noise: |log2 fold change| correlates positively with
dispersion in every group (Spearman 0.33 to 0.41, all p < 2 x 10^-35). A bigger
caste effect goes with more variability, not less.

### Robustness

Two objections, both anticipated, both tested.

**Dispersion depends on mean expression**, and caste-biased genes might simply
sit at different expression levels. Regressing log per-gene dispersion on log
baseMean with caste-biased status as a covariate leaves that status a significant
positive predictor in all eight groups, the six caste groups and both tissue
controls, with p from 5.8 x 10^-12 downwards. Stratifying by baseMean quintile
gives the same answer from another direction: caste-biased genes are more
dispersed in every one of the top four quintiles in all eight groups, p < 10^-6
throughout. The pattern breaks down only in the lowest-expression quintile, which
is where a pure low-count inflation artefact would live, and even there it is
inconsistent rather than uniform. So a real mean confound exists, stronger in
brain than in fat body, and it accounts for part of the raw effect size but not
for the effect.

**The classification used the wrong contrast for foundress.** The original
caste-biased gene set came from queen versus worker, which uses no foundress data
at all, so applying it to foundress groups was not justified. Rerunning with a
caste-matched classification, adding queen versus foundress and worker versus
foundress, changes foundress's gene set substantially (Jaccard 0.31 to 0.32
against the old set) and changes nothing about the conclusion. Foundress becomes
*more* significant, brain from 1.4 x 10^-169 to 3.0 x 10^-188 and fat body from
1.6 x 10^-87 to 7.4 x 10^-184. Queen and worker shift only slightly, as expected
given that about 60% of their classification is unchanged by construction.

### The brain versus fat body control

This control decides whether the Test 2 result is about caste at all.

Genes that distinguish brain from fat body, an axis with nothing to do with
caste, show the same reversal at comparable effect size. Tissue-biased genes are
more dispersed, p effectively 0 in brain and 7 x 10^-276 in fat body,
rank-biserial r -0.47 and -0.41 against -0.25 to -0.58 for the caste groups.

The control was pre-specified with its reading attached: if it comes back
positive too, the honest conclusion is that strong differential expression in
general goes with higher dispersion in this dataset, and the caste result is not
caste-specific. That is what happened. Under mean correction the two axes behave
the same way as each other as well, a real confound in brain, a weaker one in fat
body, an independent effect surviving in both. Whatever produces the reversal
does not distinguish the caste axis from an axis with no bearing on plasticity.

### What this says about the caste-biased gene definition

Caste-biased genes are defined by strong differential expression between queens
and workers. The control shows that strong differential expression comes with
high dispersion whatever the axis, and the dose response shows the coupling
directly: within caste-biased genes, the larger the fold change the noisier the
gene. In Test 2, the criterion used to select the genes and the quantity measured
on them are two views of the same thing.

That is a finding about the definition rather than about caste. The definition is
a selection on effect size, not a neutral pointer at caste biology, and it drags
along properties that have nothing to do with caste.

Test 1 uses the same definition. The coupling is looser there, since redundancy
of regulatory architecture is not tied to effect size by construction, but the
same class of problem is visible in Test 1's own data: caste-biased genes sit at
loci two to seven times larger than other genes. That is why the
covariate-adjusted model rather than the raw two-by-two is the quantity to trust
in Test 1.

### What the literature already said

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
> between them. Test 2's tissue control turns this from an
> argument into an observation. A gene can be queen-biased purely as a consequence of ovary
> activation without its regulation having changed at the origin of caste. Both
> tests inherit this proxy and neither can check it. Larval data during the
> commitment window is what replaces the proxy with genes that actually respond
> to the cue.
>
> Parked, not yet done: the permutation null places shuffled intervals anywhere
> outside repeat and N masked sequence, without matching sequence composition.
> "Redundant" is therefore partly a proxy for "composition looks enhancer-like".
> For the pre-specified null this only attenuates, but it is a live alternative
> explanation for the depletion result. Cheapest check is GC content and repeat
> proximity as covariates in the existing logistic model.
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
