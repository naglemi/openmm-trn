# OpenMM-Trainium Agent Rules

Current at time of writing: 2026-06-19. Proper official Neuron Explorer profiling is
the first dependency for Trainium performance work, not a cleanup gate.

Read `/home/ubuntu/popcorn/docs/neuron-explorer-profiling/README.md`, the vendored
official pages in `/home/ubuntu/popcorn/docs/neuron-explorer-profiling/official-pages/`,
and the live AWS index at
`https://awsdocs-neuron.readthedocs-hosted.com/en/latest/tools/neuron-explorer/index.html`
before launching a profiled run.

Choose the official capture path before the run: `neuron-explorer inspect -o <dir>
<real route command>` or the documented `NEURON_RT_INSPECT_*` environment variables
on the real workload. Required artifacts are claim-specific: `ntrace.pb` +
`trace_info.pb` for system timeline claims, non-empty `cpu_util.pb` for host CPU
claims, non-empty `host_mem.pb` for host memory claims, and non-empty `.ntff` plus
matching `.neff` for device/kernel claims.

Missing or zero-byte required artifacts mean profiling is broken. Do not pick a
bottleneck, optimize, tune kernels, or make a performance claim until the official
Neuron Explorer profile is repaired. `py-spy`, wall-clock arithmetic, route logs,
`neuron-monitor`, source inspection, and launch counts may help diagnose profiling,
but they do not replace official Neuron Explorer evidence.
