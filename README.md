Emergence of Discrete Spacetime Structure from Quantum
Network Dynamics:
Effective-Language Foundations and Audit-Oriented Diagnostics
Haizhong An1, ∗
1
Independent Researcher
(Dated: February 9, 2026)
1
Abstract
We develop a conservative, audit-oriented foundation for a phenomenological framework in which
an approximately continuous spacetime description may arise as a low-energy effective account of
quantum dynamics on an underlying discrete network. A central goal is to provide definitions,
conventions, and reproducible baseline diagnostics that can be cited by companion phenomenolog￾ical applications. We introduce a phenomenological discreteness scale ΛN and define the associated
regulator spacing a ≡ 1/ΛN, emphasizing that ΛN is an organizing parameter whose empirical
value must be constrained (or refuted) in concrete implementations. We state minimal interface
hypotheses: (i) correlation patterns can induce a coarse-grained proxy notion of locality, and (ii)
standard lattice gauge-theory ingredients (link variables, plaquettes, Wilson action) provide a ro￾bust representation of gauge redundancy on a discrete substrate. We further formulate an “audit
principle” for later loop-level calculations: when two numerical pipelines are constructed to be
exactly matched except for a controlled deformation, their difference must exhibit a demonstra￾ble zero point in the strictly matched limit. As numerical diagnostics (not proofs), we report
second-order consistency tests of centered discretizations (confirming O
(
a
2
)
scaling for the lat￾tice Laplacian in 1D and 3D, and for the lattice momentum pˆ
2
), and a finite-size 3D Poisson test
with monopole-inspired boundary conditions showing near-machine-precision interior residuals and
far-field scaling consistent with 1/r and 1/r2 up to finite-volume and binning effects.
I. CONVENTIONS, SCOPE, AND WHAT THIS PAPER DOES NOT CLAIM
We use natural units ℏ = c = 1 unless stated otherwise. We adopt a Euclidean-signature
lattice notation as an effective regulator language when discussing lattice momenta and topo￾logical quantities. When a Minkowski-signature interpretation is required (e.g. for on-shell
form factors), Wick-rotation relations and matching prescriptions must be stated explicitly
in the companion applications.
The aim of Paper I is deliberately limited:
• to define common notation and a minimal network-to-lattice effective interface,
∗ 81754599@qq.com
2
• to state conservative hypotheses and interface-level propositions (not microscopic
derivations),
• to provide reproducible, audit-style numerical diagnostics validating discretization and
analysis pipelines.
We do not claim a complete microscopic derivation of the Standard Model or dynamical
gravity from a specified network Hamiltonian. Phenomenological applications and model￾dependent deformations are deferred to later papers.
For numerical conversion, we use 1 GeV−1 = 0.19732698 fm.
II. QUANTUM NETWORK SETTING
A. Graph and Hilbert-space data
We consider an abstract graph G = (V, E) with vertex set V and edge set E ⊆ V × V ,
taken as primary data without an assumed embedding. To each vertex v ∈ V we associate
a finite-dimensional Hilbert space Hv, and the total Hilbert space is
H =
⊗
v∈V
Hv. (1)
A graph-local Hamiltonian can be written schematically as
H =
∑
v∈V
Hv +
(u,v
∑
)∈E
Huv, (2)
where Huv acts on Hu ⊗ Hv.
B. Correlation-based locality proxy
Given a state |Ψ⟩ ∈ H, define the mutual information between vertices u, v as
I(u : v) = S(ρu) + S(ρv) − S(ρuv), (3)
with S(ρ) = −Tr(ρ ln ρ) and reduced density matrices ρu, ρv, ρuv.
As a phenomenological locality proxy, define
d(u, v) = f
(
I0
I(u : v) + ϵI
)
, (4)
where f is monotonically increasing, I0 a normalization, and ϵI > 0 a regulator.
3
Proposition 1 (Interpretation of the proxy). For suitable choices of f and sufficiently
regular correlation decay, d(u, v) can induce approximate neighborhoods and locality relations
after coarse-graining. Without additional constraints, Eq. (4) is not guaranteed to define a
strict metric on V .
III. EFFECTIVE LATTICE DESCRIPTION AND THE DISCRETENESS SCALE
A. Definition of the scale and intended use
When the coarse-grained network appears approximately homogeneous and isotropic, it
is convenient to model effective fields on a hypercubic lattice with spacing a. We define the
phenomenological network scale
a ≡
1
ΛN
. (5)
In this series ΛN is used as an organizing parameter for leading departures from contin￾uum expressions. Its empirical value, if any, must be constrained (or refuted) by explicit
comparisons with data and precision tests in concrete implementations.
B. Brillouin zone, lattice momentum, and dispersion
Momentum space is restricted to the Brillouin zone
BZ = {
p : −
π
a
< pµ ≤
π
a
}
. (6)
A standard lattice replacement of the continuum p
2
in free propagators is
pˆ
2 ≡
a
4
2
3
∑
µ=0
sin2
(apµ
2
)
. (7)
1. Expansion of pˆ
2 and leading deviation
Using
sin x = x −
x
3
6
+
x
5
120
+ O
(
x
7
)
, (8)
one finds
pˆ
2 = p
2 −
a
2
12
3
∑
µ=0
p
4
µ +
a
4
360
3
∑
µ=0
p
6
µ + O
(
a
6
p
8
)
. (9)
4
Thus the leading deviation pˆ
2−p
2
is O(a
2
) for fixed physical momenta. Equivalently, writing
a = 1/ΛN, the leading correction is organized as O(p
4/Λ
2
N).
Proposition 2 (EFT-organized departure from continuum kinematics). In a regime where
an effective lattice surrogate is appropriate and the only new microscopic scale is ΛN, leading
deviations from continuum kinematics and propagator denominators can be organized as an
expansion in 1/Λ
2
N. In particular, any smooth, parity-symmetric modification of a quadratic
dispersion relation admits a parameterization of the form
E
2 = p
2 + m2 +
∑
n≥2
c2n
p
2n
Λ
2n−2
N
, (10)
with dimensionless coefficients c2n determined by the microscopic realization.
2. Numerical verification (diagnostic)
As a minimal diagnostic, we compare Eq. (7) against p
2 at fixed physical p while varying
a. A log-log fit of |pˆ
2 − p
2
| versus a yields slopes consistent with 2 (representative test:
1.9996 for a 4D equal-component momentum vector), and the leading correction coefficient
matches Eq. (9).
IV. AUDIT PRINCIPLE FOR MATCHED NUMERICAL COMPARISONS
Later papers in this series use “matched-comparator” numerical differences to isolate
small effects in the presence of large common contributions. The present section states the
methodological principle that must hold independent of the physical interpretation.
Proposition 3 (Matched-comparator zero-point audit). Consider two numerical estimators
E1 and E2 constructed to evaluate integrals (or expectation values) with identical external
kinematics, identical integration domain, and identical sampling streams, differing only by a
controlled deformation parameter η in the integrand kernel. If η = 0 makes the two kernels
identical, then the difference estimator
∆E(η) ≡ E1(η) − E2(η) (11)
must satisfy ∆E(0) = 0 within statistical error. Failure of this null test indicates bias,
estimator mismatch, or an implementation error.
5
Proposition 3 supplies the methodological foundation for the one-loop difference-method
audits reported in Paper II. It is an audit requirement, not a dynamical prediction.
V. DISCRETE LAPLACIAN CONSISTENCY: O
(
a
2
)
(1D TO 3D)
We record a standard consistency check: the centered finite-difference Laplacian approx￾imates the continuum Laplacian with second-order accuracy in the lattice spacing a.
A. 1D derivation
Let ϕ(x) be smooth. Expanding ϕ(x ± a) around x and combining terms yields
∆
(1
d
D)
ϕ(x) ≡
ϕ(x + a) − 2ϕ(x) + ϕ(x − a)
a
2
= ϕ
′′(x) + a
2
12
ϕ
(4)(x) + O
(
a
4
)
. (12)
B. 3D extension
On a cubic lattice with spacing a, define the standard 7-point Laplacian
∆dϕ(x) ≡
ϕ(x + axˆ) + ϕ(x − axˆ) + ϕ(x + ayˆ) + ϕ(x
a
2
− ayˆ) + ϕ(x + azˆ) + ϕ(x − azˆ) − 6ϕ(x)
.
(13)
Then
∆dϕ(x) = ∇2ϕ(x) + a
2
12
(
∂
4
x + ∂y
4 + ∂z
4
)
ϕ(x) + O
(
a
4
)
. (14)
C. Numerical verification of O
(
a
2
)
scaling
As a minimal check, we apply ∆d to analytic test functions and compare against the
continuum Laplacian. A log-log fit of the RMS error versus a yields slopes consistent with 2
(representative results: 2.006 in 1D and 2.02–2.04 in 3D), confirming the expected second￾order consistency.
6
VI. GAUGE STRUCTURE AS AN INTERFACE: LINKS, PLAQUETTES, AND
COMPACTNESS
This section is an organizational interface for companion phenomenological work. The
goal is to fix common definitions and emphasize which statements are hypotheses rather than
derivations.
A. Gauge redundancy as a local re-labeling symmetry
Hypothesis 1 (Gauge symmetry from redundancy). Local gauge transformations corre￾spond to re-labelings of internal degrees of freedom at network vertices that leave all physical
observables invariant.
In the Wilson lattice formulation [15], gauge fields are represented by group-valued link
variables
Uµ(x) = P exp(
ig
∫
x
x+aµˆ
Aµ(y) dy
)
∈ G. (15)
Under a lattice gauge transformation Ω(x) ∈ G,
Uµ(x) → Ω(x) Uµ(x) Ω†
(x + aµˆ), (16)
and the plaquette
UP = Uµ(x)Uν(x + aµˆ)U
†
µ
(x + aνˆ)Uν
†
(x) (17)
transforms by conjugation, implying Re TrUP is gauge invariant.
B. Compact variables and large gauge transformations (forward compatibility)
For later use (Paper III), we record the standard compact U(1) representation on a
periodic lattice:
Uℓ = eiθℓ ∈ U(1), θℓ ∼ θℓ + 2π. (18)
On a torus, large gauge transformations shift the gauge function by 2πn along noncon￾tractible cycles. Single-valuedness of charged matter fields under such transformations re￾stricts consistent charge normalizations once a fundamental unit is chosen. This paper does
not attempt a classification; it only fixes the language and conventions.
7
TABLE I. Structural (hypothesized) network origin of the interactions, stated as an interface-level
summary.
Interaction Symmetry language Network ingredient (hypothesis)
Strong SU(3)c Internal multiplicity; non-Abelian links
Weak SU(2)L Orientation / chiral propagation structure
Electromagnetic U(1) Phase redundancy / compact phases
Gravity Diffeomorphism (effective) Emergent metric from connectivity
C. Structural hypotheses for the interactions
Hypothesis 2 (Color from internal multiplicity). A non-Abelian gauge structure can be
represented effectively by internal multi-component degrees of freedom and corresponding
noncommutative link variables on the network.
Hypothesis 3 (Chirality from orientation). A network orientation (or an equivalent dis￾crete structure) may distinguish left- and right-handed propagation modes in an effective
description.
Hypothesis 4 (Abelian phase symmetry). A residual phase redundancy can provide an
effective U(1) gauge symmetry in the coarse-grained regime.
Hypothesis 5 (Gravity from emergent geometry). Gravity may arise as an effective descrip￾tion of collective network connectivity dynamics, in which coarse-grained distance relations
behave approximately as a metric field.
VII. TOPOLOGICAL-SECTOR WEIGHTING: A MINIMAL PARAMETER LAN￾GUAGE (FORWARD COMPATIBILITY)
For later phenomenological hypotheses (Papers II and III), it is useful to record a conser￾vative parameterization of how a discrete microstructure might reweight topological sectors
in an effective Euclidean description.
Assumption 1 (Effective reweighting parameterization). In a network-regularized effective
description, the partition function can be written schematically as a sum over topological
8
sectors Q,
Z =
∑
Q
ZQ
(eff)
, (19)
and microstructure effects can be parameterized as
ZQ
(eff) = ZQ
(0)
e
−∆Snet(Q)
, (20)
where ∆Snet(Q) summarizes the net effect of microstructure on the relative sector weights.
This assumption is not a derivation; it defines a falsifiable parameter language for lattice
measurements and phenomenological constraints.
VIII. NUMERICAL DIAGNOSTIC: 3D POISSON FAR-FIELD STRUCTURE
We present a minimal numerical diagnostic on a controlled lattice PDE problem. The
aim is to check that (i) the discrete operator is solved to high accuracy, and (ii) far-field
scaling is consistent with continuum expectations on finite volumes. This diagnostic supports
reliability of discretization and analysis pipelines used in related tests.
A. Setup
We solve
∇2ϕ = −ρ (21)
on a cubic lattice of size L
3 with spacing dx. The source ρ is a uniform-density sphere of
radius Rsrc (in lattice units), centered in the box. We impose a monopole-inspired Dirichlet
boundary condition,
ϕbnd(x) = A
r(x)
, A =
M
4π
, (22)
with M =
∑
x
ρ(x)(dx)
3 and a small “softening” r → r + soft used only to avoid division
by zero at boundary points. The solution is obtained using red-black SOR iterations on the
interior sites.
B. Residual audit
Define the interior discrete residual
R(x) ≡ ∆dϕ(x) + ρ(x), (23)
9
where ∆d is the centered 7-point lattice Laplacian. In representative runs, the interior
residual reaches near machine precision (e.g. max |R| ∼ 10−13 in a GPU implementation),
indicating that the discrete equation is satisfied to high accuracy.
C. Far-field power laws (representative fits)
We compute shell-averaged profiles ϕ(r) and |∇ϕ|(r), where shells are defined by rounding
the distance to the geometric center. We fit the potential tail to
ϕ(r) ≃ C +
A
r
p
ϕ
ϕ
, (24)
and the gradient magnitude to
|∇ϕ|(r) ≃
A
r
p
∇
∇
. (25)
Sliding-window scans in the far field yield stable plateaus with representative values consis￾tent with
pϕ ≈ 1, p∇ ≈ 2, (26)
with mild dependence on finite volume, boundary prescription, and fitting window selection.
D. Continuum cross-check
For a uniform-density sphere, the continuum solution of Eq. (21) is
ϕcont(r) =



ρ0
(
R2
2
−
r
2
6
)
+ C, r ≤ R,
ρ0R3
3
1
r
+ C, r > R,
(27)
up to an additive constant C. A least-squares fit for C performed in an outer window provides
a direct cross-check of the shell-averaged numerical profile. Representative tests show good
agreement in the far field (RMS ∼10−3
in an outer window), while larger deviations inside
the source region are consistent with finite-volume effects, discrete source geometry, and
shell binning.
IX. ROADMAP: HOW PAPERS II AND III USE THIS FOUNDATION
This paper fixes conventions and audit requirements used later:
10
• Paper II uses the scale definition in Eq. (5), the lattice momentum replacement in
Eq. (7), and the EFT organization in Proposition 2 to motivate leading corrections
suppressed by 1/Λ
2
N. It also applies the matched-comparator null requirement in
Proposition 3 to establish a numerical zero point before introducing controlled de￾formations.
• Paper III uses the compact-variable language in Sec. VI B and the reweighting param￾eterization in Assumption 1 as conservative interfaces for discussing charge normal￾ization constraints and topological-sector phenomenology.
X. REPRODUCIBILITY AND CODE AVAILABILITY
The diagnostics reported here (lattice Laplacian O(a
2
) scaling checks, lattice momentum
pˆ
2
expansion checks, and the 3D Poisson solver and analysis scripts) are implemented in
Python and are intended to be released in a public repository together with representative
parameter files and run instructions. The repository URL will be provided in a future
revision; until then, code and parameter sets are available upon request.
XI. DISCUSSION AND LIMITATIONS
Key limitations and open requirements include:
• The correlation-based quantity d(u, v) is a proxy and is not guaranteed to satisfy
metric axioms without additional assumptions and coarse-graining.
• The use of a single phenomenological scale ΛN is an organizing choice; compatibility
with precision constraints must be assessed in concrete implementations.
• The interaction discussion is structural and interface-level; it does not uniquely derive
the Standard Model gauge group, spectrum, or couplings from a specified microscopic
network Hamiltonian.
• The Poisson study is a controlled PDE diagnostic; connecting such diagnostics to
dynamical gravity requires additional steps beyond the present paper.
11
• Any loop-level phenomenology requires careful matching, symmetry checks (e.g. Ward
identities where appropriate), and explicit statements of regulator conventions.
ACKNOWLEDGMENTS
The author thanks the open-source scientific computing community for essential tools.
[1] J. A. Wheeler, “On the nature of quantum geometrodynamics,” Ann. Phys. 2, 604 (1957).
[2] S. W. Hawking, “Spacetime foam,” Nucl. Phys. B 144, 349 (1978).
[3] M. P. Bronstein, “Quantentheorie schwacher Gravitationsfelder,” Phys. Z. Sowjetunion 9, 140
(1936).
[4] C. A. Mead, “Possible connection between gravitation and fundamental length,” Phys. Rev.
135, B849 (1964).
[5] C. Rovelli, Quantum Gravity (Cambridge University Press, Cambridge, 2004).
[6] T. Thiemann, Modern Canonical Quantum General Relativity (Cambridge University Press,
Cambridge, 2007).
[7] L. Bombelli, J. Lee, D. Meyer, and R. D. Sorkin, “Space-time as a causal set,” Phys. Rev.
Lett. 59, 521 (1987).
[8] R. D. Sorkin, “Causal sets: Discrete gravity,” Lect. Notes Phys. 633, 63 (2003).
[9] J. Ambjørn, A. Görlich, J. Jurkiewicz, and R. Loll, “Nonperturbative quantum gravity,” Phys.
Rept. 519, 127 (2012).
[10] J. Polchinski, String Theory (Cambridge University Press, Cambridge, 1998).
[11] M. Van Raamsdonk, “Building up spacetime with quantum entanglement,” Gen. Rel. Grav.
42, 2323 (2010).
[12] B. Swingle, “Entanglement renormalization and holography,” Phys. Rev. D 86, 065007 (2012).
[13] J. Maldacena and L. Susskind, “Cool horizons for entangled black holes,” Fortsch. Phys. 61,
781 (2013).
[14] S. Ryu and R. Takayanagi, “Holographic derivation of entanglement entropy from AdS/CFT,”
Phys. Rev. Lett. 96, 181602 (2006).
[15] K. G. Wilson, “Confinement of quarks,” Phys. Rev. D 10, 2445 (1974).
12
