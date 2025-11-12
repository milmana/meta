Here are 10 tightly scoped math/DSP projects where C++20+ template metaprogramming (TMP) isn’t just “nice”—it’s the point. Each item states the core idea, why TMP beats a naïve/runtime approach, and 3 scores (/10): **Math**, **Impl**, **Real**.

---

### 1) Mixed-radix FFT code generator

**Idea:** Generate a fully unrolled, size-specialized Cooley–Tukey FFT for any N with compile-time radix decomposition and `constexpr` twiddles.
**Why TMP:** Factorization (`N = 2^a·3^b·5^c…`) at type level picks kernels, loop nests, and stride patterns at compile time; `if constexpr` erases dead branches; no runtime planner/dispatch. Enables inlining, register reuse, and vector-friendly access patterns.
**Scores:** Math 6 • Impl 8 • Real 9

### 2) FIR/Symmetric-FIR kernel generator

**Idea:** A header-only FIR that takes tap count, symmetry, and coefficient type as template params; emits unrolled kernels with optional compile-time half-band/linear-phase constraints.
**Why TMP:** Symmetry, even/odd length, and alignment become type traits → compile-time unroll and FMA grouping; `concepts` enforce valid designs; `constexpr` quantization tables for fixed-point. Avoids branches and temp buffers.
**Scores:** Math 5 • Impl 7 • Real 10

### 3) Polyphase L/M resampler (decimator/interpolator)

**Idea:** Generate polyphase filter banks and schedule (phase index, stride, offsets) at compile time for arbitrary L/M with optional half-band cascades.
**Why TMP:** Phases, sub-filter partitions, and tap routing are structural facts → building the graph with templates removes index math at runtime and fuses copies. Achieves cache-local, SIMD-friendly inner loops.
**Scores:** Math 7 • Impl 8 • Real 9

### 4) Static-size Kalman filter (EKF/UKF variants as policies)

**Idea:** A family of Kalman filters where state dim, measurement dim, and noise models are template params; choose Cholesky vs. LDLᵀ updates and float vs. fixed via policies.
**Why TMP:** Static dimensions enable stack allocation, loop unrolling, and algorithm selection via `if constexpr`; `requires` clauses ensure positive-definiteness policies; no heap/BLAS dispatch for small fixed sizes → big latency wins.
**Scores:** Math 8 • Impl 8 • Real 9

### 5) Lifting-scheme wavelet transform generator

**Idea:** Compile-time lifting steps for families (Daubechies, CDF 9/7, etc.) and levels; emits fused predict/update passes with boundary handling as policies.
**Why TMP:** Lifting coefficients, step order, and boundary conditions are type-level → erase branches; specialize memory access patterns (in-place vs. out-of-place) without runtime flags.
**Scores:** Math 7 • Impl 7 • Real 8

### 6) Auto-selector for fast convolution (direct/overlap-save/FFT/Winograd)

**Idea:** A `convolve<TSignal, TKernel, Sizes...>` that picks algorithm at compile time from sizes and traits; emits the chosen path with fused copy/FFT/pointwise/iFFT stages.
**Why TMP:** Size/shape are known in many pipelines; TMP picks thresholds and stitches a zero-overhead pipeline. Avoids virtual dispatch and generality cost of “do-everything” runtime engines.
**Scores:** Math 6 • Impl 7 • Real 9

### 7) Finite-difference stencil DSL (PDEs) with shape/layout policies

**Idea:** A small DSL to write stencils (e.g., 7-point, 27-point, WENO) as expression templates; compile-time grid extents, halo, and memory layout (AoS/SoA/Tiled).
**Why TMP:** Expression templates fuse multi-stage updates, remove temporaries, and choose kernel variants (`if constexpr` on layout/BC). Static shapes enable unrolling and blocking decisions encoded in types.
**Scores:** Math 8 • Impl 9 • Real 8

### 8) Chebyshev/Piecewise polynomial approximator codegen

**Idea:** Compile-time generation of minimax (Chebyshev) or Remez-fed piecewise polynomials for `exp/sin/tanh/log1p` over fixed ranges; emits Horner or Estrin kernels.
**Why TMP:** Coefficient tables and segment boundaries are `constexpr`; templates choose Horner/Estrin, degree, and error budget; branchless, inlined evaluators with no runtime table lookups.
**Scores:** Math 7 • Impl 6 • Real 8

### 9) Multi-rate DSP graph with type-level sample-rate arithmetic

**Idea:** A static data-flow graph where edges carry `sample_rate<L/M>` types; compile-time verification of rate compatibility, buffer sizes, and latency; generates a static schedule.
**Why TMP:** Unit/rate safety via concepts prevents illegal connections; compile-time scheduling removes runtime topological checks; buffer sizes and strides become constants → better codegen and cache predictability.
**Scores:** Math 6 • Impl 8 • Real 8

### 10) Fixed-point (Q-format) pipeline generator with saturation/rounding policies

**Idea:** End-to-end fixed-point DSP blocks where word length, Q format, and rounding/saturation are template policies; emits saturated arithmetic kernels and scale-tracking at compile time.
**Why TMP:** All scaling and guard-bit math known at compile time → no dynamic checks; policy mixing selects fast intrinsics for target ISA; eliminates branching on mode flags.
**Scores:** Math 6 • Impl 7 • Real 9

---

## Picking a starter set

* **Quick wins:** (2) FIR, (6) Fast convolution selector.
* **Showcase pieces:** (1) FFT codegen, (4) Kalman, (7) Stencil DSL.

If you want, I’ll draft a minimal skeleton for one of these (e.g., #2 FIR or #6 selector) using concepts, traits, and expression templates, plus a micro-benchmark harness.

### link
https://chatgpt.com/s/t_6914ea5c697c81919d57227aca0bc065
