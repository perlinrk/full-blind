# Final fresh blind audit: nonuniform nonresonant theorem

## 1. Executive verdict

**VERIFIED**

I audited the theorem as a fresh, self-contained argument, using only
`barnes-hut-clt.tex`.  In particular, I did not use the uniform-input conclusions
as substitutes for any of the nonuniform estimates: the physical-profile lemma,
nonfair-bit martingale construction, fixed-window variance calculation,
all-depth covariance exhaustion, signed cutoff passage, and nonuniform adaptive
stabilization were each checked on their own terms.

The manuscript proves the stated nonuniform, nonresonant variance asymptotic and
centered CLT, including normalization by the true variance.  It also proves the
claimed first-moment asymptotic by a separate absolute-majorant argument.  I found
no mathematical defect requiring repair.

## 2. Exact theorem audited

The theorem actually proved has the following scope.

* The Barnes--Hut parameter is fixed with \(0<\theta<1\).
* \(X_1,\ldots,X_n\) are iid on \([0,1]\) with probability density
  \[
  f\in C^1([0,1]),\qquad 0<m_f\leq f\leq M_f<\infty.
  \]
* Dyadic cells are half open, with the final cell containing 1.  Empty cells cost
  zero; a nontarget singleton costs one; a target singleton costs zero; a
  nonsingleton target cell is opened; an admissible disjoint cell is accepted
  when \(w/D\leq\theta\), including equality; and one-child chains are retained.
* The parameter is nonresonant:
  \[
  \theta\ne 2/Q\quad(Q=3,4,5,\ldots).
  \]
  Equivalently, the canonical Perron--Gordin martingale difference
  \(d_\theta\) is nonzero, and
  \(c(\theta)=\|d_\theta\|_{L^2(du)}^2>0\).

Under those hypotheses, as \(n\to\infty\), the manuscript proves
\[
 \mathbb E_fT_{\theta,n}={2\over\theta}n\log_2n+O_{f,\theta}(n),
\]
\[
 \operatorname {Var}_fT_{\theta,n}
 \sim c(\theta)n\log_2n,
\]
and
\[
 {T_{\theta,n}-\mathbb E_fT_{\theta,n}
  \over\sqrt{c(\theta)n\log_2n}}
 \Longrightarrow N(0,1).
\]
Because the variance ratio tends to one, it also proves
\[
 {T_{\theta,n}-\mathbb E_fT_{\theta,n}
  \over\sqrt{\operatorname {Var}_fT_{\theta,n}}}
 \Longrightarrow N(0,1).
\]

The manuscript expressly does **not** assert a nonuniform resonant theorem.

## 3. Dependency graph

The proof dependency graph is the following directed acyclic chain.  Branches
that later recombine are shown explicitly.

1. **Exact filled-half root toll.**  The stopping, equality, empty-cell,
   singleton, and one-child conventions give the pathwise toll \(F_\theta\), its
   finite moments, and \(\int F_\theta=2/\theta\).
2. **Perron--Gordin algebra.**  The row identity and inverse-branch calculation
   give
   \[
   F_\theta-\mathbb EF_\theta=d_\theta+h_\theta\circ T-h_\theta,
   \qquad Pd_\theta=0.
   \]
3. **Resonance criterion.**  Fourier reduction, the endpoint-collapse tree, and
   the simultaneous odd-chain lemma prove
   \(\|d_\theta\|_2=0\) exactly for \(\theta=2/Q\), \(Q\ge3\).
4. **Deterministic stopped decomposition.**  Finite pathwise telescoping yields
   \[
   V_{\theta,n}=(2/\theta)L_n+M_{\theta,n}+H_{\theta,n}.
   \]
5. **Physical-cell profile framework.**  Exact labelled conditional
   factorization supplies the nonuniform suffix densities and nonfair child-bit
   parameters used in all subsequent nonuniform arguments.
6. **External path estimates.**  Exact activity probabilities give
   \(\mathbb EL_n=n\log_2n+O(n)\); an add-one/Efron--Stein argument gives
   \(\operatorname {Var}L_n=O(n)\).
7. **Finite Walsh window.**  Whole-column revelation and exact Bernoulli
   centering split \(M_n^{(m)}=N_n^{(m)}+R_n^{(m)}\).
8. **Fixed-window bracket and CLT.**  Profile cancellation, bracket
   concentration, fourth moments, Lindeberg, and time truncation give the
   fixed-window centered CLT.
9. **Fixed-window variance.**  Martingale isometry plus the separately bounded
   drift and covariance gives the explicit variance asymptotic.
10. **Infinite-Walsh tail at finite cutoff.**  The exact covariance identity is
    partitioned by label and dyadic-cell geometry; the activity kernel and all
    geometry-specific estimates give a uniform finite-cutoff bound.
11. **Signed cutoff removal.**  The same nonnegative majorants restricted to a
    tail window prove an \(L^2\)-Cauchy estimate; a separate absolute first-moment
    bound identifies the limit with the stopped sum.
12. **Full canonical stopped sum.**  Centered converging together gives the full
    canonical CLT, while an independent centered \(L^2\) triangle argument gives
    its variance asymptotic.
13. **Endpoint and path remainders.**  Their variances are \(O(n)\), so the
    canonical result transfers to \(V_{\theta,n}\).
14. **Adaptive stabilization.**  The arithmetic-free guard, coefficient-one
    inward copy, uniform root-defect moments, support inclusion, dense/sparse
    ancestor bounds, Minkowski, and Efron--Stein give
    \(\operatorname {Var}\Delta_{\theta,n}=O(n)\).
15. **Adaptive variance and CLT transfer.**  With \(T=V+\Delta\), covariance
    control transfers both the leading variance and centered CLT.
16. **True-variance normalization.**  The proved variance equivalence, not weak
    convergence alone, supplies the final Slutsky replacement.
17. **First moment (separate branch).**  The external-path mean, endpoint bound,
    absolutely controlled canonical mean, and root-defect sum give the stated
    expectation before recombining with \(T=V+\Delta\).

Every arrow points from an earlier identity or estimate to a later one.  The
fixed-window CLT is not used to prove fixed-window variance; the final CLT is not
used to prove full variance; and the discrepancy mean is not inferred from its
variance.  I found no circular dependency.

## 4. Component-by-component audit

### Exact toll / Perron--Gordin — **PASS**

The root toll follows the declared strict-opening/weak-acceptance convention.
The residue-tree argument handles the clipping depths and equality cases and
proves the Kraft identity used to obtain \(\int F_\theta=2/\theta\).  The row
identity is obtained first for finite rows and passed in finite \(L^p\); the
Perron correction \(k\) is uniformly convergent.  The displayed definitions
then give the exact coboundary decomposition and \(Pd_\theta=0\).  The stopped
decomposition is finite and pathwise, so it makes no optional-stopping
assumption.

### Nonresonance — **PASS**

The Fourier coefficients reduce to the simultaneous family
\(\Psi_u(\{b\})\).  Endpoint collapse is proved with a finite prefix tree and
retains coincident numerical labels with their multiplicities.  Irrational,
odd-denominator rational, and power-of-two denominator cases are separately
covered.  Thus \(d_\theta=0\) iff \(b\in\frac12\mathbb Z\), equivalently iff
\(\theta=2/Q\), \(Q\ge3\).  Therefore the claimed coefficient is strictly
positive at every parameter in the audited scope.

### Profile framework — **PASS**

For a physical interval \(I=[a,a+s)\), the manuscript uses exactly
\[
 p_I=\int_I f,
 \qquad f_I(u)={s f(a+su)\over p_I}.
\]
Substitution proves normalization, while \(m_fs\le p_I\le M_fs\) and the
Lipschitz estimate give uniform \(L^\infty,L^1,L^2\) flatness.  Child
restriction is normalized by the actual physical masses and gives the exact
nonfair parameter \(q_I=p_{I_1}/p_I\).  The derivative scaling for dyadic and
iterated middle-half restrictions is recorded and remains uniform in physical
depth.  Conditional iid suffix laws are proved only after conditioning on the
labelled allocation; distinct fixed-depth coordinate families are then
independent.  No physical mass is replaced by dyadic length.

### Fixed-window CLT — **PASS**

The filtration reveals complete columns.  Conditional on its past, the next
bits are independent Bernoulli variables with cell-specific parameters; they
are centered by \(\eta_{i,t}=\epsilon_{i,t}-(1-2q_{i,t})\), not by a fair-bit
fiction.  Activity is predictable because its base depth is at most \(t-1\).
The exact two-label formula distinguishes direct witnesses, nesting, equality,
and disjoint multinomial avoidance.

The bracket mean expansion retains all ordered Walsh cross-pairs.  Its diagonal
is the external path mean up to \(O(n)\), while the finite-window cancellation
lemma makes all profile cross-errors summable with a \(2^{-r}\) gain.  The
bracket variance is \(O(n\log^2n)\), and the fourth-moment sum is
\(O(n^2\log n)\).  These imply bracket convergence and conditional Lindeberg.
The omitted bracket after deterministic time truncation has expectation
\(o(1)\), and the centered drift is negligible.  Deconditioning is therefore
valid.  No fair-Rademacher premise remains.

### Fixed-window variance asymptotic — **PASS**

The manuscript explicitly proves, rather than infers from weak convergence,
\[
 \operatorname {Var}_fN_n^{(m)}=\mathbb E_fQ_n^{(m)}
 =\|d_\theta^{(m)}\|_{L^2(du)}^2n\log_2n+O(n)
\]
and \(\operatorname {Var}_fR_n^{(m)}=O(n)\).  It then uses
\[
 |\operatorname {Cov}(N_n^{(m)},R_n^{(m)})|
 \leq O(\sqrt{n\log n})O(\sqrt n)
 =O(n\sqrt{\log n})=o(n\log n)
\]
to conclude
\[
 \operatorname {Var}_fM_n^{(m)}
 =\|d_\theta^{(m)}\|_{L^2(du)}^2n\log_2n+o(n\log n).
\]
The coefficient comes from \(\mathbb EL_n=n\log_2n+O(n)\); hence it is the
Lebesgue \(L^2\) norm with base-two logarithm and no missing \(1/\log2\).

### Infinite-Walsh tail — **PASS**

The argument begins at finite \(R\) with the exact identity
\(\operatorname {Var}Z_R=\sum_{i,j,r,s}\operatorname {Cov}(Y_{i,r},Y_{j,s})\).
Its partition is disjoint and exhaustive:

* same label: \(r=s\), \(r<s\), and \(r>s\);
* different labels: equal cell, each of the two strict-nesting orientations,
  and disjoint cells.

For different labels the exact activity kernel is derived by
inclusion--exclusion:
\[
K=1-(1-a)(1-p)^N-(1-b)(1-q)^N
 +(1-a)(1-b)(1-p-q+u)^N,
\]
and it is centered by the product of the two correct \((N+1)\)-witness
activity probabilities.  The equal, nested, and disjoint specializations
follow algebraically.  In particular, disjoint occupancies are treated through
\((1-p-q)^N\), never as independent binomials.

For the same label, the diagonal, shifted product, stopping/activity error, and
product-of-means correction are all retained.  The shifted Lebesgue comparator
vanishes by \(P^he=0\), and the BV/profile perturbation is summable in depth.

For equal cells, both direct witnesses and the centered product are contained
in the exact specialized kernel, and the complete depth sum is bounded.  For
strict nesting, the direct-witness term is treated separately in both
orientations.  The centered coincidence term is expanded in affine coordinates
with frozen density and oscillation terms; the Haar square-sum, descendant sum,
and ancestor sum are displayed.  Conditional centering eliminates the first
\(m\) Haar scales and yields the stated \(2^{-m}\) gain.

For disjoint cells, the manuscript writes the actual bilinear form, defines its
matrix entries, computes row and column sums, invokes Schur only after those
computations, inserts the cell-energy estimate, and sums all four terms of the
nonindependent kernel bound over both depths.

The shallow/critical/deep split checks both critical scalar sums and all mixed
strips.  The geometry ledger assigns an \(n\log n\) coefficient and lower-order
remainder to every partition element.  Its total coefficient is
\[
b_m=C_f\{\|e_m\|_2^2+2^{-m}\|e_m\|_1\|e_m\|_2
                   +2^{-m}\|e_m\|_1^2\},
\]
which tends to zero by dyadic martingale convergence and
\(\|e_m\|_1\le\|e_m\|_2\).

### Cutoff removal — **PASS**

For \(R_2>R_1\), the variance of the actual difference contains exactly all
pairs with both indices in the tail window.  Restricting each previously
displayed nonnegative, summable majorant to that window makes its tail vanish;
thus the cutoffs are \(L^2\)-Cauchy.  Separately,
\[
 \mathbb E|W_{R_1,R_2}|
 \le n\|e_m\|_\infty\sum_{r>R_1}\min(1,C_fn2^{-r})\to0.
\]
This absolute first-moment estimate, together with almost-sure finite isolation,
identifies the \(L^2\) limit as the stopped sum.  There is no monotone-convergence
argument for a signed series.

### Stopped variance — **PASS**

The tail transfer compares centered \(L^2\) norms, takes \(n\to\infty\) first
and \(m\to\infty\) second, and combines the tail bound with the already proved
fixed-window variance asymptotic.  This independently proves
\(\operatorname {Var}M_{\theta,n}\sim c(\theta)n\log_2n\).  The external-path
and endpoint variances are \(O(n)\), while their covariance with the canonical
term is \(O(n\sqrt{\log n})\), so the same leading variance holds for
\(V_{\theta,n}\).  No variance statement is deduced from a CLT.

### Stopped CLT — **PASS**

The approximation error is exactly
\(M_n(e_m)-\mathbb E_fM_n(e_m)\), not its uncentered version.  Chebyshev gives
centered converging together in the required order of limits.  The path and
endpoint remainders are independently \(O_{L^2}(\sqrt n)\), hence negligible on
the \(\sqrt{n\log n}\) scale.  Slutsky gives the centered stopped CLT.

### Adaptive discrepancy — **PASS**

The root defect and barred root defect are distinguished, with the bar removing
occupancies 0 and 1.  The finite guard respects equality and all one-child
chains.  On guard success there is exactly one inward middle-half copy and no
boundary toll.  The guard is removed before invoking the conditional iid inward
law, avoiding conditioning bias.  Polynomial bad-event growth times exponential
guard failure gives uniform moments for every fixed order over the enlarged
profile family.

The add-one support inclusion correctly separates the new point (middle-half
events) from the old sample (guard events), so the asserted independence is
legitimate.  It yields a local increment bound decaying in dense cells.  Along
the ancestor chain, the dense regime uses a binomial negative-moment estimate;
the sparse regime uses the support event \(K_r\ge1\) and high root-defect
moments.  The two geometric tails have a uniformly bounded Minkowski sum.
Replacement is removal plus insertion into the common sample, giving bounded
squared influence and hence \(\operatorname {Var}\Delta_{\theta,n}=O(n)\) by
Efron--Stein.

### Adaptive variance — **PASS**

With \(T=V+\Delta\), the manuscript explicitly uses
\[
 |\operatorname {Cov}(V,\Delta)|
 \le\sqrt{\operatorname {Var}V\operatorname {Var}\Delta}
 =O(n\sqrt{\log n})=o(n\log n).
\]
Thus the adaptive variance has the same leading coefficient as the stopped
variance.

### Adaptive CLT — **PASS**

The centered discrepancy has \(L^2\) size \(O(\sqrt n)\), so divided by
\(\sqrt{n\log n}\) it vanishes in \(L^2\).  Centered Slutsky applied to the
stopped CLT proves the adaptive CLT.  No bound on the uncentered discrepancy is
incorrectly substituted here.

### True-variance normalization — **PASS**

The adaptive variance equivalence is proved before normalization is changed.
The ratio of the deterministic asymptotic scale to the true standard deviation
tends to one, so the final use of Slutsky is justified.

### First moment — **PASS**

The mean is treated separately.  The external path contributes
\((2/\theta)n\log_2n+O(n)\).  For the canonical signed observable, the proof
subtracts the cellwise constant density and dominates the absolute integrand by
\(\|f'\|_\infty2^{-2r}|d_\theta(u)|\); summation over the \(2^r\) cells leaves
an integrable geometric series.  Tonelli is applied only to that nonnegative
majorant, not to the signed observable.  Endpoint absolute moments are linear.
The discrepancy is bounded in expectation by summing the probabilities of
cells with occupancy at least two, giving \(O(n)\).  These estimates establish
the stated first moment without relying on the centered CLT or on the variance
bound.

## 5. Detailed defects

No mathematical defect found.

I also found no isolated typographical ambiguity that changes a hypothesis,
normalization, covariance term, power of two, logarithm base, or limiting
argument in the audited theorem.

## 6. Circularity and hidden-assumption audit

**Circularity:** none found.  In particular:

* the fixed-window variance is proved from martingale isometry and drift bounds,
  not from the fixed-window CLT;
* the full stopped variance is proved from the fixed-window variance and tail
  exhaustion, not from the full CLT;
* the adaptive variance is proved from stopped variance and discrepancy
  variance before true-variance normalization;
* the first moment has independent absolute estimates; and
* adaptive stabilization does not assume the desired adaptive variance result.

**Hidden uniform-input assumptions:** none found in the nonuniform proof.  The
audit specifically checked the following possible failure modes.

* No \(\operatorname {Bin}(n,1/2)\) split is used for physical nonuniform child
  allocations; actual masses \(p_I\) and ratios \(q_I\) are used.
* Fair Rademacher centering is replaced by exact cell-specific Bernoulli
  centering.
* Child profiles are neither equated to each other nor to the uniform profile.
* Suffixes are declared independent only after conditioning on labelled cell
  allocation, and retain their profile densities.
* Disjoint occupancies are handled with the multinomial avoidance term
  \((1-p-q)^N\), not as independent binomials.
* Translation invariance is not used; profile errors are controlled by physical
  \(C^1\) oscillation.
* Physical probability mass is never silently replaced by dyadic length; the
  two are compared only through the displayed \(m_f,M_f\) bounds.

The earlier uniform sections supply algebraic and deterministic identities
(the toll, Perron decomposition, resonance criterion, and finite-tree
decomposition).  Where probability laws change under nonuniform input, the
manuscript supplies new profile-based proofs rather than importing fair-bit
claims.

## 7. Final theorem table

| Claim | Verdict | Reason |
|---|---|---|
| Exact root toll and mean \(2/\theta\) | VERIFIED | Equality, clipping, singleton, empty, and one-child cases are included in the finite-tree calculation. |
| Canonical Perron--Gordin decomposition | VERIFIED | Exact inverse-branch identities give \(Pd_\theta=0\) and a finite-\(L^p\) coboundary. |
| Nonresonance iff \(\theta\ne2/Q\) | VERIFIED | Fourier endpoint collapse and simultaneous odd-chain analysis prove the exact zero set. |
| Physical profile factorization | VERIFIED | Correct normalized density, mass bounds, child restriction, derivative scaling, and labelled conditional iid laws are proved. |
| External-path mean and variance | VERIFIED | Exact activity formula gives the mean; add-one stabilization and Efron--Stein give linear variance. |
| Fixed-window centered CLT | VERIFIED | Exact nonfair centering, bracket convergence, fourth moments, Lindeberg, truncation, and deconditioning are complete. |
| Fixed-window variance asymptotic | VERIFIED | Martingale isometry, \(O(n)\) drift variance, and explicit covariance control give the Lebesgue \(L^2\) coefficient with \(\log_2\). |
| Infinite-Walsh centered tail bound | VERIFIED | Finite identity, exhaustive covariance partition, exact activity kernel, Haar estimate, Schur estimate, critical strips, and ledger are present. |
| Signed \(R\to\infty\) removal | VERIFIED | Tail-window covariance majorants are summable, and absolute mean convergence identifies the stopped sum. |
| Full canonical variance | VERIFIED | Centered \(L^2\) comparison plus fixed-window variance proves it independently of weak convergence. |
| Canonical centered CLT | VERIFIED | Centered converging together uses \(n\to\infty\) before \(m\to\infty\). |
| Endpoint/path remainder control | VERIFIED | Both have variance \(O(n)\), and endpoint conditional means use prefix-free physical cells. |
| Stopped variance and CLT | VERIFIED | Remainders and all covariances are lower order on the \(n\log n\) scale. |
| Adaptive discrepancy variance | VERIFIED | Guard/copy stabilization, uniform moments, dense/sparse ancestor sums, and Efron--Stein yield \(O(n)\). |
| Adaptive variance transfer | VERIFIED | The covariance is explicitly \(O(n\sqrt{\log n})=o(n\log n)\). |
| Adaptive centered CLT | VERIFIED | The centered discrepancy is negligible in \(L^2\) and Slutsky applies. |
| True-variance normalization | VERIFIED | It follows from the separately proved variance equivalence. |
| First-moment asymptotic | VERIFIED | A nonnegative integrable majorant controls the signed canonical mean; all other remainders are \(O(n)\). |
| Nonuniform resonant theorem | NOT CLAIMED | The manuscript expressly leaves this outside its boundary. |

## 8. Final disposition

COMPLETE NONUNIFORM NONRESONANT THEORY VERIFIED.
