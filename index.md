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
group.

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

SCRMshaw scores a target genome against *Drosophila* training sets, each a
collection of known regulatory sequences for one tissue plus a matched
background. It slides a window along the genome and asks how much more that
window resembles the positives than the background. Three scoring methods do
this differently and all three are run:

- **IMM**, an interpolated Markov model, backing off to lower orders where data
  is sparse, so effective word length adapts to the sequence.
- **HexMCD**, a fixed fifth-order Markov chain, scoring each hexamer's
  likelihood ratio under positive versus background models.
- **PAC**, word overrepresentation, asking which short words occur more often
  than a Poisson expectation.

They are run together because they fail differently, not because they are
independent. What comes out is enhancer-like sequence. It is not demonstrated
function, it is not validated in this species, and it is tied to a gene by
proximity alone.

### From windows to predictions

500 bp windows at a 250 bp slide, repeated at 25 phase offsets 10 bp apart, each
scored by all three methods. Windows more than 5% N are dropped. Each of the 25
instances gets its own elbow-point threshold rather than a fixed top-N cut.
Surviving windows aggregate into a 10 bp genome-wide signal, MACS2 calls broad
peaks, and a second elbow pass on peak amplitudes selects the final set.
Parameters are in [methods](#methods-in-full).

Two failures shaped this, and neither announced itself.

**IMM looked broken and was not.** With repeats masked, 714 of 1,200 training
set by method combinations had no detectable threshold. SCRMshaw's k-mer routine
strips N rather than skipping masked windows, so a mostly-N window returns a
likelihood ratio of exactly zero, and on IMM's unbounded scale zero outranks the
million windows scoring negative. No evidence was beating evidence of absence.
Filtering at 5% N removed all 714, and IMM turned out to be the most selective
method rather than a failed one.

**Peak calling was calling the whole genome.** The first implementation used a
per-window threshold as the cutoff on the summed 25-offset signal, which sums
routinely exceed, so most training sets returned 80,000 to 103,000 peaks
covering nearly the entire retained footprint. Filling empty 10 bp bins with
zero made it worse, since zero beats any negative cutoff and blank genome read
as signal. Fixed with a negative sentinel fill and by reinstating the reference
pipeline's two-stage design.

### From predictions to redundant loci

Raw prediction counts per locus are not interpretable. A long locus in
favourable sequence collects more predictions than a short one for reasons that
have nothing to do with biology. The permutation test replaces the count with a
comparison against that locus's own expectation.

Per training set, the observed prediction intervals are shuffled 1,000 times
within eligible sequence, everything not repeat or N masked plus the real peak
footprints, staying on the same scaffold and not overlapping. A locus is called
redundant when its real count exceeds all 1,000 shuffles. About 1.8% of loci
carrying predictions clear this, against roughly 3% reported for *Drosophila*.
That call is Test 1's independent variable.

### From loci to genes

A **testable locus** carries at least one real prediction in at least one
training set. Loci with no predictions anywhere are absence of data rather than
evidence of absence, so they are excluded rather than counted as non-redundant.

The unit of analysis is the gene, since caste-biased status is a property of
genes. A gene counts as **redundant** if it touches at least one locus called
significant in at least one training set. The obvious worry is that taking a
maximum over 36 or 74 sets inflates that call. It does not, because the
multiplicity already sits inside the permutation test: each set's call is itself
a test against that locus's own null. What the maximum does introduce is a size
dependence, since a longer locus gets more chances, and that is handled with
covariates rather than ignored.

Gene universes differ by method, because the methods predict in different
places. Each method is analysed against its own.

### Result on 36 training sets

Null. Odds ratios from 0.84 to 1.27, every confidence interval crossing 1, every
Fisher p above 0.15, in both tissues and all three methods. The one nominally
significant result (PAC, fat body, logistic OR 1.27) fails the standard set in
advance that a result appearing under a single method is fragile rather than
evidence.

A power audit asked whether this was a real null or a detectability artefact.
Three checks agreed. A locus with one prediction can reach significance, so
there is no hard floor. Caste-biased genes sit at larger loci with more
predictions than other genes, the opposite of what a masking explanation
requires. Matching on locus length and prediction count changes nothing.
Simulation gives 69 to 99.8% power at OR 1.5 and 98 to 100% at OR 2.0; below
about OR 1.2 power is genuinely limited, 20 to 59%.

A well-powered null, then, against any effect worth caring about. The proposal
predicted enrichment.

### Result on 74 and 86 training sets

The original run excluded 12 training sets with defective background models.
Since that exclusion was a judgement call and 38 further sets became available,
the test was rerun on wider universes. Brain, `retained74`:

| Method | OR | 95% CI | Fisher p |
|---|---|---|---|
| IMM | 0.684 | 0.519, 0.900 | 0.0054 |
| merged | 0.783 | 0.636, 0.963 | 0.0189 |
| HexMCD | 0.876 | 0.721, 1.064 | 0.198 |
| PAC | 0.901 | 0.723, 1.123 | 0.385 |

Fat body is null under every method. The pattern strengthens in `all86` (IMM
0.655, p = 0.0004) and appears in the 38 new sets on their own (IMM 0.635,
p = 0.0036).

The direction is depletion. Caste-biased brain genes are *less* likely to sit at
redundant loci, not more, which is the opposite of the proposal's prediction.
Two earlier findings point the same way: the queen-associated WGCNA modules are
also less redundant, and the original five-set neural analysis gave OR 0.30.

Under covariate adjustment merged survives (p = 0.0089) and IMM does not
(p = 0.080). This is a follow-up rather than a pre-specified test, and it rests
on the same gene definition questioned in Test 2, so it is reported as a
direction that needs explaining rather than as a finding.

### What the method disagreement means

The methods predict in very different places. Median final peaks per training
set: IMM about 1,036 covering 1.2% of the genome, HexMCD 8,164 covering 6%, PAC
5,520 covering 4.9%. Base-pair Jaccard between any two is 0.04 to 0.13, and the
relationship is nested rather than symmetric, with 86% of IMM's footprint inside
HexMCD's against 19% the other way. Merged is a union, 40.5% of its base pairs
HexMCD-private and 39.3% PAC-private with 2.4% three-way, yet at the level of
which loci are called significant it correlates 0.93 with HexMCD.

So are the four odds ratios above four effects or one? The methods share data, so
a standard heterogeneity test does not apply. A paired bootstrap over genes was
used instead, resampling the same genes for all four methods. In `retained74` no
pairwise difference excludes zero. Cochran's I², reported descriptively only, is
0.6% in brain and 0% in fat body.

The methods do not disagree. Merged is the best-powered estimate of one shared
effect, and its association lives entirely in the slice where at least two
methods agree (OR 0.787, p = 0.024, covering 98.2% of its significant loci). No
significant locus is IMM-exclusive.

Two explanations are ruled out here. Covariate confounding does not account for
adjustment weakening IMM and strengthening merged: IMM shows the *weakest*
locus-length confounding of the four and merged the strongest, the reverse of
what that story needs. Power does account for it, merged having about 1.7 times
more redundant genes. And the depletion is not neural-specific. Expanding the
neural training-set tier from 5 sets to 20 moves IMM's brain OR from 0.30 to
0.704, almost exactly the full tissue-unrestricted result of 0.684, with no
matched versus mismatched divergence and a clean fat-body negative control. The
original neural finding was an extreme small-sample estimate regressing toward
the dataset's real effect size, not a concentrated neural signal.

## Test 2. Expression canalization

Test 2 was meant to test the canalization idea on data that does not depend on
enhancer prediction. It ended up testing something else: the caste-biased gene
definition that both tests rely on.

### Prediction and design

If caste determination is canalized, genes that distinguish castes should vary
*less* between individuals of one caste than other genes do. The direction was
fixed in advance.

Six groups, one per caste and tissue combination. Dispersion is the pydeseq2
per-gene estimate, refit within each group so nothing is shared across the
comparison. Roughly 10,200 to 10,900 genes tested per group. Egg-laying workers
excluded at n = 2. Queen and worker one-sided in the predicted direction,
foundress two-sided, because a foundress has not committed to a trajectory the
way a queen or a mature worker has. Brain versus fat body was specified as a
required control. Run 16 September 2026.

### Result

The effect runs the other way, in every group. Caste-biased genes are *more*
dispersed. The one-sided queen and worker tests return p = 1.0. Foundress,
two-sided, gives p = 1.4 x 10^-169 in brain and 1.6 x 10^-87 in fat body.

| Group | caste-biased | other | rank-biserial r |
|---|---|---|---|
| queen, brain | 0.122 | 0.019 | -0.58 |
| worker, brain | 0.120 | 0.021 | -0.51 |
| foundress, brain | 0.133 | 0.030 | -0.54 |
| queen, fat body | 0.074 | 0.033 | -0.25 |
| worker, fat body | 0.150 | 0.071 | -0.31 |
| foundress, fat body | 0.104 | 0.051 | -0.31 |

Median within-caste dispersion. The gradient inside the caste-biased set points
the same way: the genes that most sharply separate queens from workers are also
the genes that vary most between individuals of the same caste, which is the
opposite of what a reliable caste marker should look like (Spearman 0.33 to
0.41, all p < 2 x 10^-35).

### Robustness

Dispersion depends on mean expression, and caste-biased genes might simply sit at
different expression levels. Regressing log dispersion on log baseMean with
caste-biased status as a covariate leaves that status a significant positive
predictor in all eight groups, p from 5.8 x 10^-12 downwards. Stratifying by
baseMean quintile agrees: caste-biased genes are more dispersed in the top four
quintiles of all eight groups, p < 10^-6 throughout, breaking down only in the
lowest quintile where low-count inflation would live. A real mean confound
exists, stronger in brain, and accounts for part of the effect size but not for
the effect.

The analysis was also run with a caste-matched classification, adding queen
versus foundress and worker versus foundress contrasts, with the same result in
every group.

### The brain versus fat body control

This decides whether the result is about caste at all.

Genes distinguishing brain from fat body, an axis unrelated to caste, show the
same reversal at the same effect size: p effectively 0 in brain, 7 x 10^-276 in
fat body, rank-biserial r -0.47 and -0.41 against -0.25 to -0.58 for the caste
groups.

The control was pre-specified with its reading attached. If it came back positive
too, the honest conclusion would be that strong differential expression in
general goes with higher dispersion in this dataset, and the caste result is not
caste-specific. That is what happened.

### What this says about the caste-biased gene definition

Caste-biased genes are defined by strong differential expression. The control
shows that strong differential expression brings high dispersion with it on any
axis, and the gradient shows the same coupling inside the caste set. The
criterion used to select the genes and the quantity measured on them are two
views of the same thing.

That is a finding about the definition, not about caste. The definition selects
on effect size rather than on mechanism, and carries properties along with it
that have nothing to do with caste.

Test 1 uses the same definition. The coupling is looser, since redundancy is not
tied to effect size by construction, but the same problem shows in Test 1's own
data: caste-biased genes sit at loci two to seven times larger than other genes.
That is why the covariate-adjusted model rather than the raw two-by-two is the
quantity to trust there.

### What the literature already said

The prediction ran against published work. The reversal is not surprising in
hindsight.

**Expression variance is not low where function is high.** Across genetically
diverse individuals, high-variance genes are the ones with narrow promoters and
few stabilising features, while low-variance genes are held steady either by
constitutively accessible chromatin or by layers of pausing, distal elements and
post-transcriptional control. And high-variance genes are significantly more
likely to be differentially expressed under perturbation (Sigalova et al. 2020).
That link between being variable and being differentially expressed is the
paper's own conclusion, not an inference from it.

**Noise and plasticity share a mechanism.** The promoter architecture that lets a
gene respond to the environment is the architecture that lets it drift
stochastically, so responsiveness and noise are coupled rather than separately
optimisable (Lehner 2010, with the general selection argument in Lehner 2008). A
gene that must respond to a cue cannot also be quiet.

**Theory predicts the same.** In evolving network models, genetic and
noise-driven variance are proportional, so the genes most able to respond are the
most variable (Furusawa and Kaneko 2011). In bistable switches driven by a
morphogen, intrinsic noise is maximal near the switching boundary, which is where
switch-associated genes sit (Perez-Carrasco et al. 2016).

So the prediction of lower variance in caste-biased genes was in tension with the
literature before it was tested. Caste-biased genes are by definition strongly
responsive genes, and responsive genes are noisy.

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
> Rohlfs and Nielsen 2015; Sigalova et al. 2020; Lehner 2008; Lehner 2010;
> Furusawa and Kaneko 2011; Perez-Carrasco et al. 2016; Masel et al. 2007.
