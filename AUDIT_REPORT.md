# Fresh blind re-audit: nonuniform nonresonant theorem

## 1. Executive verdict

**VERIFIED AFTER MINOR REPAIR**

The complete nonuniform nonresonant argument is mathematically coherent and the claimed theorem follows from the estimates proved in the manuscript. I found no structural gap, circularity, illicit fixed-​(n) independence assumption, or hidden reversion to uniform input. I found one local auditability defect: the proof of the tail theorem invokes a “fixed-​(m) variance asymptotic,” but Theorem N.29 states only the fixed-window CLT and four estimates, not that variance asymptotic. The missing conclusion follows immediately from those displayed estimates by one covariance calculation, so this is a minor repair rather than a failure of the theorem.

## 2. Exact theorem audited

The audited setting is the following.

* (0<\theta<1) is fixed and nonresonant:
  
  \[
  \theta\ne 2/Q\qquad(Q=3,4,5,\ldots).
  \]
* (X_1,\ldots,X_n) are iid on ([0,1]) with density
  
  \[
  f\in C^1([0,1]),\qquad 0<m_f\le f\le M_f<\infty.
  \]
* The Barnes--Hut conventions are those fixed in Section 1: dyadic cells are half open (with the final endpoint convention later stated explicitly), equality (w/D=\theta) is accepted, empty cells cost zero, a source singleton distinct from the target costs one, a singleton containing the target costs zero, and one-child chains are retained.
* (T_{\theta,n}) is the adaptive cost, (V_{\theta,n}) is the strict-stopped/filled cost, and (T_{\theta,n}=V_{\theta,n}+\Delta_{\theta,n}).
* The canonical Perron--Gordin innovation is (d_\theta), with Lebesgue norm
  
  \[
  c(\theta)=\|d_\theta\|_{L^2(du)}^2.
  \]

The audited conclusions are

\[
\mathbb E_fT_{\theta,n}={2\over\theta}n\log_2n+O_{f,\theta}(n),
\]

\[
\operatorname{Var}_fT_{\theta,n}\sim c(\theta)n\log_2n,
\qquad c(\theta)>0,
\]

and

\[
{T_{\theta,n}-\mathbb E_fT_{\theta,n}\over
 \sqrt{c(\theta)n\log_2n}}\Rightarrow N(0,1),
\qquad
{T_{\theta,n}-\mathbb E_fT_{\theta,n}\over
 \sqrt{\operatorname{Var}_fT_{\theta,n}}}\Rightarrow N(0,1).
\]

The first-moment statement is not needed for the centered CLT, but it is also supported independently.

## 3. Dependency graph

The logical chain reconstructed from the manuscript is:

1. **Model conventions and exact root toll.** Section 1 fixes empty, singleton, equality, and one-child behavior and proves the filled-half toll (F_\theta), including (int F_\theta=2/\theta) and all finite moments.
2. **Perron--Gordin algebra.** Section 2 first obtains (F_\theta-\mathbb EF_\theta=H^0+A\circ T-A), then constructs (k), (d_\theta), and (h_\theta) so that
   
   \[
   F_\theta-\mathbb EF_\theta=d_\theta+h_\theta\circ T-h_\theta,
   \qquad Pd_\theta=0.
   \]
3. **Nonresonance.** Section 3 computes the odd Fourier coefficients, collapses the endpoint tree, proves the simultaneous odd-chain lemma, and concludes
   
   \[
   \|d_\theta\|_2^2=0\iff \theta=2/Q,\quad Q\ge3.
   \]
4. **Deterministic stopped decomposition.** Applying the exact toll and the coboundary identity along each active label path yields
   
   \[
   V_{\theta,n}={2\over\theta}L_n+M_{\theta,n}+H_{\theta,n}.
   \]
5. **Nonuniform profiles.** The physical-cell profile theorem supplies exact conditional iid factorization, labelled-allocation conditional independence, nonfair child parameters, flatness (O(|I|)), and uniform bounds.
6. **External path.** Exact activity probabilities give (mathbb EL_n=n\log_2n+O(n)); an add-one calculation and Efron--Stein give (operatorname{Var}L_n=O(n)).
7. **Finite Walsh window.** Whole-column filtration + exact nonfair centering gives a martingale (N_n^{(m)}), predictable bracket (Q_n^{(m)}), and drift (R_n^{(m)}). Activity and cancellation estimates give bracket mean/concentration, fourth moments, Lindeberg, truncation, and the fixed-window CLT with leading Lebesgue constant (|d_\theta^{(m)}|_2^2).
8. **Infinite Walsh tail.** Starting at finite depth (R), the proof expands (operatorname{Var}Z_R), partitions every covariance geometry, uses the exact fixed-size activity kernel, and establishes the global (b_m) ledger with (b_m\to0).
9. **Signed cutoff removal.** The same covariance majorants, restricted to a tail window, prove (Z_R) is (L^2)-Cauchy; absolute first-moment control identifies the limit with the stopped sum.
10. **Stopped canonical theorem.** Centered converging together gives the CLT for (M_{\theta,n}), and the (L^2) triangle inequality gives its variance asymptotic independently of weak convergence.
11. **Endpoint and path remainders.** Their centered (L^2) sizes are (O(\sqrt n)), giving the stopped variance and CLT for (V_{\theta,n}).
12. **Adaptive discrepancy.** The deterministic coefficient-one inward-copy theorem gives uniform root-defect moments; support stabilization gives a decaying local add-one moment; ancestor-chain Minkowski and Efron--Stein give (operatorname{Var}\Delta_{\theta,n}=O(n)).
13. **Final transfer.** (T=V+\Delta), Cauchy--Schwarz makes the mixed covariance (o(n\log n)), and centered Slutsky yields both deterministic and true-variance normalization.

This graph is acyclic. The uniform geometric inward-copy result is used only as a deterministic local identity in the later profile-uniform stabilization argument; the nonuniform theorem is not used to prove any of its own inputs. The manuscript's large resonant-uniform dossier is not a dependency of the nonuniform nonresonant theorem.

## 4. Component-by-component audit

### Exact toll / Perron--Gordin — **PASS**

The toll derivation honors strict opening versus accepted equality, explicitly includes clipped initial depths, proves the Kraft identity used in the mean, and controls endpoint singularities in every finite (L^p). The row identity is obtained by a finite truncation before passage to (L^p). The series defining (k) is uniformly convergent, (Pd_\theta=0) is obtained by direct index shifting, and the stopped coboundary telescopes with the correct entrance/terminal signs. Empty, singleton, and one-child conventions are fixed before the calculation.

### Nonresonance — **PASS**

The proof does not assume a scalar zero-set assertion for the lacunary series. It proves simultaneous vanishing for all positive odd frequencies only at (0) and (1/2), treating irrational, odd-denominator, and power-of-two denominator cases. Together with the exact endpoint-collapse tree and Parseval, this gives precisely

\[
c(\theta)>0\iff\theta\ne2/Q\quad(Q\ge3).
\]

### Profile framework — **PASS**

The profile is correctly normalized as

\[
f_I(u)={|I|f(a_I+|I|u)\over \mu_f(I)}.
\]

The manuscript proves (m_f|I|\le\mu_f(I)\le M_f|I|), flatness and derivative scaling, exact child restrictions, and labelled conditional iid statements. For inward/middle-half restrictions it enlarges the family explicitly and obtains bounds independent of physical depth. It consistently uses physical mass (p_I), not dyadic length, in occupancy probabilities.

### Fixed-window nonuniform CLT — **PASS AFTER MINOR REPAIR**

The whole-column filtration is correct: at time (t), all new bits are conditionally independent but nonfair Bernoulli variables with physical-cell parameters. The centered innovations (eta_{i,t}) are used, while the nonzero conditional means are retained in a drift. Predictability follows because stopping is known by the relevant earlier depth and every remaining bit index is at most (t-1).

The one- and two-label activity formulae retain fixed-size multinomial dependence and cover direct companionship, equal cells, both nesting orientations, and disjoint cells. The finite-window cancellation lemma supplies the necessary (2^{-r}) profile-error factor. Diagonal Walsh terms give (mathbb EL_n); cross terms cost only (O(n)). Hence the leading bracket constant is the Lebesgue norm (|d_\theta^{(m)}|_2^2). Replacement bounds give bracket concentration and (O(n)) drift variance. Conditional fourth moments imply Lindeberg, and the infinite time axis is cut off with vanishing expected omitted bracket before applying a finite triangular-array martingale CLT.

The one missing sentence is the fixed-window variance asymptotic; see Defect 1.

### Infinite-Walsh tail — **PASS**

The proof genuinely begins with finite (R): it defines (Y_{i,r}), (Z_R), and writes the literal finite covariance identity. Its partition is disjoint and exhaustive:

* same label: (r=s), (r<s), (r>s);
* different labels: same cell, each strict-nesting orientation, disjoint cells.

The exact activity kernel is correctly derived by inclusion--exclusion with (N=n-2), witness indicators (a,b), physical masses (p,q,u), followed by subtraction of the two one-label activity probabilities. Direct substitution yields the same-cell, nested, and disjoint specializations. No independence of disjoint occupancies is used.

For the same label, the manuscript gives the exact (r<s) integral, uses (P^he=0) for Perron cancellation, separately controls diagonal, off-diagonal, and products of means, and sums all depths with correct (n)-factors. For equal cells, the exact centered kernel and the cell-energy bound control all witness/product pieces.

For strict nesting, both direct-witness and centered-coincidence terms are separated. The weighted Haar calculation is carried out in affine coordinates with (F_A=f_A+\rho_A); all four frozen/oscillation terms are displayed. The descendant square-sum identity and ancestor sum have the required powers of two. The other orientation is derived as an exact algebraic transpose rather than assumed from pointwise symmetry.

For disjoint cells, the matrix (M_{A,B}), bilinear form, row and column sums, Schur norm, profile energy, and depth sums are all explicit. The expansion keeps the multinomial correction (R_0-PQ).

The two scalar critical-depth estimates are correct after writing (s=\lfloor\log_2n\rfloor+k): the first is (O(\log n)), while the second is (O(n)). Shallow, critical, mixed, and deep strips are all represented in the preceding sums.

Finally, ledger (N.31) assigns an (n\log n) coefficient and lower-order remainder to every geometry. Its

\[
b_m=C_f\bigl(\|e_m\|_2^2+2^{-m}\|e_m\|_1\|e_m\|_2+2^{-m}\|e_m\|_1^2\bigr)
\]

tends to zero by Lebesgue martingale convergence and $\|e_m\|_1\le\|e_m\|_2$.

### Cutoff removal — **PASS**

For (R_2>R_1), the manuscript expands the variance of the actual difference (W_{R_1,R_2}), so exactly the pairs with both indices in the tail window occur. Restricting each earlier nonnegative scalar majorant to that window produces tails of convergent series. This is a genuine (L^2)-Cauchy proof, not monotone convergence for a signed sum. Absolute mean control uses boundedness of (e_m) and a summable activity tail. Almost-sure finite isolation identifies the (L^2) limit with (M_n(e_m)).

### Stopped variance — **PASS AFTER MINOR REPAIR**

The variance of the full canonical stopped term is obtained separately from the CLT by the (L^2) triangle inequality and the tail bound. The path and endpoint pieces have (O(n)) variances, and their covariances with the canonical term are (O(n\sqrt{\log n})). Subject only to inserting the immediate fixed-window variance calculation in Defect 1, the stated stopped variance follows.

### Stopped CLT — **PASS**

The converging-together difference is explicitly centered:

\[
M_n(e_m)-\mathbb E_fM_n(e_m).
\]

Chebyshev is applied first as (n\to\infty), then (m\to\infty). No uncentered tail is substituted. Path and endpoint remainders vanish on the (sqrt{n\log n}) scale, so Slutsky applies.

### Adaptive discrepancy — **PASS**

The barred root defect is maintained at local occupancies zero and one. The guard argument respects accepted equality, one-child chains, and produces exactly one inward copy with no boundary toll. For nonuniform profiles, every guard atom has a uniform lower mass, and the inward restriction remains in the enlarged profile family. The moment recursion removes the guard indicator before invoking the unconditional inward iid law, avoiding conditioning bias.

The support inclusion compares old and inserted configurations under an old-sample guard; the inserted point and guard event are independent. The bar threshold causes no exception on guard success and is explicitly discussed for sizes zero and one. Hölder plus uniform defect moments yields local stabilization. Along an inserted point's ancestor chain, large occupancies use a proved negative-binomial-moment estimate, sparse occupancies use the fact that the increment vanishes at occupancy zero, and both sides of the critical depth are geometrically summable. Minkowski gives a uniform add-one (L^2) bound and Efron--Stein gives linear variance.

### Adaptive variance — **PASS**

(operatorname{Var}_f\Delta_{\theta,n}=O_{f,\theta}(n)) is established directly by replacement Efron--Stein, independently of the earlier uniform signed-renewal proof. This direct proof is sufficient for the final theorem and does not assume independence between root defects and descendant discrepancies.

### Adaptive CLT — **PASS**

There is no separate nondegenerate CLT for (Delta), nor is one needed. The manuscript proves the precise required statement:

\[
{\Delta_{\theta,n}-\mathbb E_f\Delta_{\theta,n}\over\sqrt{n\log n}}
\longrightarrow0
\quad\text{in }L^2,
\]

so adding it to the stopped statistic is a valid centered Slutsky transfer.

### True-variance normalization — **PASS**

From (operatorname{Var}V\sim cn\log n) and (operatorname{Var}\Delta=O(n)), Cauchy--Schwarz gives

\[
|\operatorname{Cov}(V,\Delta)|
\le\sqrt{\operatorname{Var}V\operatorname{Var}\Delta}
=O(n\sqrt{\log n})=o(n\log n).
\]

Thus (operatorname{Var}T\sim cn\log n). Since (c>0), the ratio of deterministic and true standard deviations tends to one, and Slutsky justifies true-variance normalization.

## 5. Detailed defects

### Defect 1 — fixed-window variance asymptotic invoked but not stated

* **Location:** Theorem “Nonuniform fixed-window theorem,” equation (N.29) and its proof; later invocation in the final paragraph of Theorem “Stopped-energy exhaustion” after equation `tail-centered-identity`.
* **Issue:** The fixed-window theorem states (operatorname{Var}R_n^{(m)}=O(n)), the bracket mean asymptotic, bracket concentration, fourth moments, and the CLT. The tail theorem subsequently says to use “the fixed-​(m) variance asymptotic,” but no displayed conclusion has stated or derived
  
  \[
  \operatorname{Var}_fM_n(d^{(m)})
  =\|d^{(m)}\|_2^2n\log_2n+o(n\log n).
  \]
  
  Weak convergence alone cannot supply this, so the omitted calculation should be present under the requested audit standard.
* **Classification:** **Local.** All inputs are already proved immediately above it.
* **Smallest repair:** Add the following calculation to Theorem N.29 or its proof. Orthogonality of martingale differences gives
  
  \[
  \operatorname{Var}N_n^{(m)}=\mathbb EQ_n^{(m)}
  =\|d^{(m)}\|_2^2n\log_2n+O(n).
  \]
  
  Since (M_n^{(m)}=N_n^{(m)}+R_n^{(m)}) and (operatorname{Var}R_n^{(m)}=O(n)),
  
  \[
  |\operatorname{Cov}(N_n^{(m)},R_n^{(m)})|
  \le O(\sqrt{n\log n})O(\sqrt n)
  =O(n\sqrt{\log n})=o(n\log n).
  \]
  
  Therefore the required fixed-window variance asymptotic holds. This insertion uses no new lemma or hypothesis.

No other mathematical defect was found.

## 6. Circularity and hidden-assumption audit

**Circularity:** None found. The canonical tail variance is proved from finite-cutoff covariance estimates, not from the desired CLT. The stopped variance is proved independently of weak convergence. The adaptive linear variance is proved by stabilization/Efron--Stein and is then used only in the final transfer. The mean proof is independent of the variance proof.

**Hidden uniform-input assumptions:** None found in the nonuniform chain.

* Child bits are centered with their physical conditional parameters (q_I), not (1/2).
* Conditional suffix iid statements are made only after labelled allocations or the relevant cell/occupancy conditioning.
* Disjoint cell occupancies are treated through multinomial avoidance probabilities, never as independent binomials.
* Physical masses (p_I) appear in activity and avoidance factors; dyadic lengths enter only through bounds (m_f|I|\le p_I\le M_f|I|).
* Translation invariance and uniform-within-cell laws are replaced by normalized profiles plus explicit (C^1) oscillation errors.
* The inward-copy identity is geometric and affine, while the probabilistic law after copying is the corresponding restricted profile, not a uniform law.

**First moments and signed limits:** The all-depth mean of (M) is bounded with a nonnegative geometric majorant and Tonelli. The signed Walsh cutoff is removed by absolute mean convergence plus (L^2)-Cauchy control. No use of monotone convergence on a signed observable was found. The first-moment theorem is logically separate from, and unnecessary for, the centered CLT.

## 7. Final theorem table

| Claim | Verdict | Reason |
|---|---|---|
| Exact root toll and mean (2/\theta) | PASS | Equality, clipping, endpoints, and Kraft identity are handled explicitly. |
| Perron--Gordin decomposition with (Pd_\theta=0) | PASS | Constructed in finite (L^p), with convergent correction series and exact coboundary. |
| (c(\theta)>0\iff\theta\ne2/Q) | PASS | Exact Fourier collapse plus the simultaneous odd-chain lemma and Parseval. |
| Physical-cell profile framework | PASS | Correct normalization, bounds, restrictions, and labelled conditional iid factorization. |
| External path expectation/variance | PASS | Exact activity formula and centered add-one Efron--Stein proof. |
| Fixed-window nonuniform CLT | PASS AFTER MINOR REPAIR | Martingale CLT is complete; its immediately implied variance asymptotic should be stated and proved. |
| Infinite-Walsh centered tail exhaustion | PASS | Finite-cutoff start, exhaustive kernel geometry, explicit Haar/Schur sums, and (b_m\to0). |
| (R\to\infty) cutoff removal | PASS | Genuine signed (L^2)-Cauchy and absolute-mean argument. |
| Canonical stopped variance | PASS AFTER MINOR REPAIR | Independent (L^2) argument is valid once the local fixed-window variance line is inserted. |
| Canonical/stopped centered CLT | PASS | Correct centering and order of limits; lower-order path/endpoint terms handled by Slutsky. |
| Endpoint variance | PASS | Prefix-free terminal conditioning gives independent suffix profiles and bounded conditional-mean error. |
| Adaptive discrepancy variance | PASS | Guarded inward copy, uniform moments, support inclusion, ancestor summability, Efron--Stein. |
| Full adaptive variance | PASS | Mixed covariance is (o(n\log n)) by Cauchy--Schwarz. |
| Full adaptive CLT | PASS | Centered discrepancy is (o_{L^2}(\sqrt{n\log n})). |
| True-variance normalization | PASS | Variance equivalence and positivity make the final Slutsky step valid. |
| Mean asymptotic | PASS | Signed terms have explicit nonnegative dominating majorants; not used for centered CLT. |

## 8. Final disposition

COMPLETE NONUNIFORM NONRESONANT THEORY VERIFIED AFTER MINOR REPAIR.
