# Fresh blind audit: nonuniform nonresonant theorem

## 1. Executive verdict

**NOT VERIFIED**

The exact toll, Perron--Gordin reduction, nonresonance criterion, profile
factorization, finite-Walsh martingale argument, endpoint estimate, and final
algebraic transfer are substantially supported.  The decisive failure is the
claimed infinite-Walsh stopped-energy exhaustion theorem.  Its proof announces
an “exhaustive covariance partition,” but the difficult two-label terms are
then disposed of in prose.  It does not display the promised finite-cutoff
covariance formula, define the asserted multinomial kernel, derive the Schur
matrix bounds, or show the summations leading to the stated value of (b_m).
Those missing estimates are the bridge from a fixed finite Walsh window to the
full canonical observable.  Consequently the full stopped variance/CLT and
everything downstream of them are not established by the manuscript.

This is a fresh audit of `barnes-hut-clt.tex` only.  Numerical evidence and
external material were not used.

## 2. Exact theorem audited

Fix (0<\theta<1).  Let (X_1,\ldots,X_n) be iid on ([0,1]) with density

\[
 f\in C^1[0,1],\qquad 0<m_f\le f\le M_f<\infty.
\]

The Barnes--Hut conventions are: half-open dyadic cells (with the final cell
containing (1)); empty cells cost zero; the target singleton costs zero;
another singleton costs one; a non-singleton containing the target is opened;
and a disjoint non-singleton is accepted exactly when (w/D\le\theta), so
equality is accepted and one-child chains are retained.

For the adaptive cost (T_{\theta,n}), the audited claim is that whenever

\[
 \theta\ne 2/Q\quad(Q=3,4,5,\ldots),
\]

the canonical Perron--Gordin martingale difference (d_\theta) has
(c(\theta)=\|d_\theta\|_{L^2(du)}^2>0), and

\[
 \mathbb E_fT_{\theta,n}={2\over\theta}n\log_2n+O_{f,\theta}(n),
 \qquad
 \operatorname {Var}_fT_{\theta,n}\sim
 c(\theta)n\log_2n,
\]

\[
 {T_{\theta,n}-\mathbb E_fT_{\theta,n}\over
  \sqrt{c(\theta)n\log_2n}}\Rightarrow N(0,1),
 \qquad
 {T_{\theta,n}-\mathbb E_fT_{\theta,n}\over
  \sqrt{\operatorname {Var}_fT_{\theta,n}}}\Rightarrow N(0,1).
\]

The requested audit focuses on the variance and centered CLTs, while also
checking the stated mean and true-variance normalization.

## 3. Dependency graph

The manuscript's intended dependency graph is:

1. **Exact geometry and toll:** the strict acceptance convention gives
   (F_\theta), with (int F_\theta=2/\theta).
2. **Perron--Gordin algebra:** (F_\theta-\mathbb EF_\theta
   =d_\theta+h_\theta\circ T-h_\theta), with (Pd_\theta=0).
3. **Nonresonance:** Fourier endpoint collapse and the simultaneous odd-chain
   lemma give
   (|d_\theta|_2^2=0\iff\theta=2/Q), (Q\ge3).
4. **Exact stopped decomposition:**
   (V_{\theta,n}=(2/\theta)L_n+M_{\theta,n}+H_{\theta,n}).
5. **Profiles:** conditional rescaling in every physical dyadic cell, plus
   closure and uniform control for later middle-half restrictions.
6. **External path length:**
   (mathbb EL_n=n\log_2n+O(n)) and (operatorname {Var}L_n=O(n)).
7. **Finite Walsh window:** for each fixed (m), exact nonfair-bit martingale
   centering, bracket asymptotics with coefficient
   (|d_\theta^{(m)}|_2^2), bracket concentration, and Lindeberg imply the
   centered finite-window CLT.
8. **Infinite-Walsh exhaustion:** for
   (e_m=d_\theta-d_\theta^{(m)}), prove
   (operatorname {Var}M_n(e_m)\le b_mn\log(n+1)+Cn), (b_m\to0), and an
   (L^2)-cutoff construction.
9. **Full canonical stopped sum:** use centered converging-together and an
   independent second-moment argument to obtain the variance asymptotic and
   CLT for (M_{\theta,n}).
10. **Endpoint and stopped theorem:** (L_n) and (H_{\theta,n}) are
    (O_{L^2}(\sqrt n)), so transfer the canonical results to (V_{\theta,n}).
11. **Adaptive discrepancy:** exact barred root-defect decomposition,
    profile-uniform guards and stabilization, ancestor summation, and
    Efron--Stein give
    (operatorname {Var}\Delta_{\theta,n}=O(n)).
12. **Adaptive transfer:** (T=V+\Delta), Cauchy--Schwarz covariance control,
    centered Slutsky, variance equivalence, and true-variance normalization.

The graph is formally acyclic.  However, node 8 is not proved at referee
standard, so nodes 9, 10, and 12 have an unsupported incoming edge.

## 4. Component-by-component audit

### 4.1 Profile framework — **PASS**

The physical-cell profile is correctly normalized as
(f_I(u)=|I|f(a_I+|I|u)/p_I).  The bounds
(m_f|I|\le p_I\le M_f|I|), the (L^\infty,L^1,L^2) flatness bounds, and
the child formulas are proved directly.  The conditional iid statement is
made only after conditioning on labelled allocation, and distinct cells are
then conditionally independent.  This avoids the false assertion that
multinomial cell counts are independent.

For stabilization, the manuscript enlarges the family to normalized
restrictions obtained by iterated middle-half restriction.  It derives
(m_f/M_f\le f_I\le M_f/m_f) and
(|f_I'|_\infty\le (L_f/m_f)|I|), so the family is closed under the guard's
inward map and the constants remain uniform in physical depth and location.

### 4.2 Finite-window CLT — **PASS**

The whole-column filtration is appropriate.  Conditional on the labelled
prefix allocation, the next bits are independent Bernoulli variables with
physical-cell parameters (q_I), not fair bits.  The variables
(eta_{i,t}=\epsilon_{i,t}-(1-2q_{i,t})) are exactly conditionally centered,
and the coefficient (C_{i,t-1}) is predictable because its activity and all
remaining bits are measurable one column earlier.

The manuscript explicitly treats one-label activity and all two-label
geometries (direct companionship, equal cells, strict nesting, and disjoint
cells).  The bracket expansion retains activity/bit dependence.  Its
finite-window cancellation lemma supplies the essential extra (2^{-r}),
making the profile errors summable rather than logarithmic.  Diagonal Walsh
modes contribute
(sum_Sa_S^2=\|d_\theta^{(m)}\|_{L^2(du)}^2); cross modes cost (O(n)).
Thus the leading coefficient is the Lebesgue norm and is independent of
(f).

Replacement bounds yield bracket concentration on the required scale, while
the fourth-moment calculation implies conditional Lindeberg.  The infinite
time array is truncated with vanishing omitted bracket, and the drift is
centered separately.  No hidden fair-bit assumption is used here.

### 4.3 Infinite-Walsh tail — **FAIL**

This is the structural gap.  Equation (N.30), the displayed covariance
partition, is merely the tautological first expansion.  The proof then says:

* the same-label term is controlled after “Cauchy--Schwarz ... and
  summation”;
* the disjoint two-label term has an “exact fixed-(n) multinomial kernel”
  (R-PQ), but (R,P,Q) are never defined and the exact formula is not
  displayed;
* “Schur's test” controls the resulting matrix, but neither the matrix nor
  its row/column sums are shown;
* nested terms split into direct-witness and centered-coincidence terms, but
  their formulas and summation ranges are absent;
* several bounds for “same-cell,” “direct-witness,” “disjoint Schur,” and
  “density-weighted nested Haar” sums are asserted only after the narrative,
  without a chain of inequalities from the finite-cutoff covariance.

Consequently a reader cannot verify that every covariance term has been
counted exactly once, that the stated profile errors have the claimed factors,
or that constants in the (O(n)) remainder are uniform in (m).  Most
importantly, the displayed choice

\[
b_m=C_f\{\|e_m\|_2^2+2^{-m}\|e_m\|_1\|e_m\|_2
                   +2^{-m}\|e_m\|_1^2\}
\]

is announced rather than derived from an auditable finite sum.  Naming every
geometry is not a proof of its estimate.

The final sentence about restricting both depths to (R_1<r,s\le R_2) also
does not supply an (L^2)-Cauchy proof: it refers to “every scalar majorant”
without having displayed those majorants or proved their absolute summability.
Thus the finite-cutoff-to-infinite signed-sum passage is unsupported as well.

The proof does correctly state that the converging-together error must be
(M_n(e_m)-\mathbb EM_n(e_m)), not the uncentered tail, but correct centering
cannot repair the missing variance estimate.

### 4.4 Centered stopped theorem — **FAIL**

Conditional on the tail theorem, this transfer is correct: the external path
and endpoint terms have (L^2) norm (O(\sqrt n)), covariance with the
canonical sum is (O(n\sqrt{\log n})), and the variance asymptotic is obtained
separately rather than inferred from weak convergence.

Unconditionally, however, both the full (M_{\theta,n}) variance asymptotic
and CLT depend on the failed stopped-energy exhaustion result.  Therefore the
stopped theorem is not verified.

### 4.5 Adaptive discrepancy — **PASS**

The deterministic defect is defined with the exact empty/singleton/equality
conventions.  The finite-tree identity uses the **barred** defect at every
occupied internal cell.  This is essential at occupancies zero and one and is
preserved in the nonuniform add-one argument.

The guard proof gives a coefficient-one inward copy, not two copies and no
boundary toll.  In the nonuniform extension, every fixed guard atom has a
profile-uniform positive mass.  The proof avoids conditioning the inward iid
sample on guard success: it removes the guard indicator before invoking the
conditional iid law.  Root-defect moments are then bootstrapped uniformly
over the closed profile family.

The support inclusion explicitly handles the bars: a successful guard forces
at least two old points; at old size zero or one the guard fails and the event
remains on the right side.  The new-point inward event and old-sample guard
failure are independent.  This yields the local add-one decay.

Along the physical ancestor chain, dense cells use the binomial negative
moment estimate and sparse cells use the fact that the barred increment is
zero at old occupancy zero plus a high-moment/Hölder estimate.  The two
geometric depth sums are uniform, and the (L^2) limit is justified before
Efron--Stein.  No singleton defect is silently set to zero: it is barred by
definition.

### 4.6 Final transfer — **FAIL**

The transfer algebra itself is correct.  From a proved
(operatorname {Var}V\sim cn\log n) and
(operatorname {Var}\Delta=O(n)), one gets

\[
 |\operatorname {Cov}(V,\Delta)|
 \le\sqrt{\operatorname {Var}V\operatorname {Var}\Delta}
 =O(n\sqrt{\log n})=o(n\log n),
\]

and the centered discrepancy is negligible in (L^2) on the CLT scale.
Variance equivalence would then justify true-variance normalization.

But the premise concerning (V) is not established because of the
infinite-tail gap.  Hence neither adaptive variance equivalence nor either
adaptive CLT is verified.

## 5. Detailed defects

### Defect 1: no auditable finite-cutoff two-label covariance expansion

**Location:** Section “Infinite-tail transfer and the all-depth covariance
sum,” proof of Theorem “Stopped-energy exhaustion,” beginning with equation
`eq:covpartition` and the paragraphs beginning “For different labels” and
“In the nested case.”

**Why insufficient:** `eq:covpartition` only separates same-label from
different-label covariances.  It does not give the finite-cutoff formulas for
the witness events produced by stopping.  The later terms (R-PQ), “direct
witness,” and “centered indicator” are not defined algebraically.  Without
those formulas, the claimed cancellation and estimates cannot be checked for
same cells, both nesting directions, disjoint cells, or transposed mixed-depth
strips.

**Severity:** Structural.  This is the principal estimate needed to remove
the finite-Walsh cutoff.

**Smallest repair:** State a finite cutoff (M_{n,R}(e_m)); write the exact
covariance for each ordered ((i,j,r,s)); partition it explicitly into equal,
strictly nested in each direction, and disjoint cells; define every witness
probability; and prove a summable bound for each resulting term before taking
(R\to\infty).

### Defect 2: the Schur and Haar summations are asserted, not proved

**Location:** The same theorem, from “the mean-value theorem bounds it ...”
through equation `eq:haar` and the two displayed occupancy sums.

**Why insufficient:** The manuscript does not exhibit the scalar matrix to
which Schur's test is applied, nor its row and column sums.  Equation
`eq:haar` controls a particular family of integrals, but the proof does not
derive the covariance weights multiplying those integrals or show how their
sum reduces to the two displayed occupancy series.  Nor does it show in
detail where the claimed (2^{-m}) and (2^{-m/2}) factors enter every
mixed strip.

**Severity:** Structural, not a cosmetic omission: these are precisely the
large two-label sums that can be of order (n\log n).

**Smallest repair:** Display the kernels and indices, prove the Schur row and
column estimates, apply the Haar square-sum with all density and occupancy
weights present, and sum separately over (r<s), (r>s), and the transition
strip around (log_2 n), with constants declared uniform in (m,n,R).

### Defect 3: (b_m\to0) is announced rather than derived

**Location:** The paragraph beginning “These cases exhaust all
((i,j,r,s))” and the subsequent displayed formula for (b_m).

**Why insufficient:** The preceding prose gives no chain of inequalities
whose (n\log n) coefficients add to the displayed (b_m).  Some asserted
intermediate bounds even appear without their finite-cutoff sums or scaling
context.  Parseval proves that the *displayed expression* tends to zero, but
not that it bounds the omitted covariance expansion.

**Severity:** Structural.

**Smallest repair:** After proving every geometry estimate, tabulate its
(n\log n) coefficient and (O(n)) remainder, then sum the table to an
explicit (b_m) and an (O_{f,\theta}(n)) constant independent of (m).

### Defect 4: the signed (R\to\infty) passage is not established

**Location:** The final-cutoff paragraph in the stopped-energy exhaustion
proof: “Applying the same estimates with both depths restricted to
(R_1<r,s\le R_2) makes every scalar majorant a tail of a convergent series.”

**Why insufficient:** No scalar majorants were fully stated or shown to be
absolutely summable.  Moreover, to prove the stopped sum Cauchy one must
bound all covariance pairs in which at least one depth lies in the cutoff
tail, not merely a square strip unless the omitted cross strips are separately
controlled.  The sentence does not do that.  Monotone convergence is
unavailable for this signed sum, as the manuscript correctly observes.

**Severity:** Structural, though it can be repaired together with Defects
1--3.

**Smallest repair:** Prove a uniform (L^2) estimate for
(M_{n,R_2}(e_m)-M_{n,R_1}(e_m)), including cross-depth strips generated by
the difference, and show its bound tends to zero as (R_1\to\infty).

### Defect 5: the first-moment argument for the full canonical sum is too terse

**Location:** Lemma “Linear first moments,” the sentence “first truncate
(d_\theta), then use its structured (L^1) tail and pass monotonically.”

**Why insufficient:** (d_\theta) is signed, so monotone passage does not
apply to the function itself.  The “structured (L^1) tail” and a dominating
nonnegative series are not supplied at that location.  This affects the
claimed (O(n)) mean remainder, not the centered CLT if the variance theory
were otherwise complete.

**Severity:** Local but real.

**Smallest repair:** State an explicit nonnegative (L^1) majorant for the
truncation error, prove the conditional cell-mean bound uniformly in depth,
and use dominated convergence/Tonelli on that majorant rather than saying the
signed observable passes monotonically.

## 6. Circularity and hidden-assumption audit

### Circularity

No circular dependency was found in the stated ordering.  The finite-window
CLT is proved before tail exhaustion; tail exhaustion is then used for the
full stopped theorem; the discrepancy proof is independent of the stopped
CLT; and final transfer uses both.  The manuscript also explicitly avoids
using adaptive discrepancy in the strict-stopped argument.

The problem is not circularity but an unproved node: the infinite-tail theorem
is treated as established downstream even though its central covariance
estimates are only summarized.

### Hidden uniform-input assumptions

No fatal hidden uniform assumption was found in the **finite-window** or
**adaptive stabilization** portions:

* occupancies are binomial with physical mass (p_I), not automatically
  (2^{-r});
* next bits are Bernoulli((q_I)) and exactly recentered;
* conditional independence is invoked only after labelled prefix allocation;
* child profiles are not identified with each other;
* the guard uses lower profile-mass bounds rather than uniform atom masses;
* suffix laws after rescaling are the appropriate restricted profiles.

The infinite-tail proof repeatedly compares a local profile to Lebesgue
density, which is the right strategy, but its omitted formulas prevent a
determination that no uniform-input cancellation has slipped into the
two-label terms.  This uncertainty is itself part of the tail-theorem failure.

## 7. Final theorem table

| Claim | Verdict | Reason |
|---|---|---|
| Exact toll and Perron--Gordin decomposition | PASS | Equality conventions, telescoping, integrability, and (Pd_\theta=0) are addressed. |
| Nonresonance (c(\theta)>0\iff\theta\ne2/Q) | PASS | Fourier endpoint collapse and the simultaneous odd-chain lemma cover irrational, odd-denominator, and dyadic-denominator cases. |
| Nonuniform profile framework | PASS | Correct normalization, quantitative flatness, labelled conditional factorization, child restriction, and guard-family closure. |
| Fixed-window nonuniform CLT | PASS | Exact nonfair centering, predictability, activity geometry, bracket coefficient, concentration, and Lindeberg are supplied. |
| Infinite-Walsh centered tail theorem | FAIL | The finite-cutoff two-label covariance expansion and its Schur/Haar summations are not actually derived. |
| Finite-cutoff to full stopped signed sum | FAIL | No complete (L^2)-Cauchy estimate, including cross strips, is written. |
| Stopped nonuniform variance asymptotic | FAIL | Depends on the failed tail theorem. |
| Centered stopped nonuniform CLT | FAIL | Depends on centered tail exhaustion; correct centering is stated but the needed variance bound is unsupported. |
| Adaptive discrepancy (O(n)) | PASS | Barred defect, guards, singleton cases, profile-uniform stabilization, dense/sparse sums, and Efron--Stein are handled. |
| Full adaptive nonuniform variance asymptotic | FAIL | The final covariance algebra is correct, but the stopped variance premise is unproved. |
| Full adaptive centered nonuniform CLT | FAIL | Slutsky is correctly formulated, but the stopped CLT premise is unproved. |
| True-variance normalization | FAIL | It would follow from variance equivalence, which is not established because the stopped variance theorem fails. |

## 8. Final disposition

**COMPLETE NONUNIFORM NONRESONANT THEORY NOT VERIFIED.**
