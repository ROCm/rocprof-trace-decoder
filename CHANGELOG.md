# Changelog for release 0.1.6

### Resolved issues

- Fixed an issue where rocprof-trace-decode could read memory out of bounds with a specific trace pattern.
- Fixed the shaderdata record not properly reporting the Shader Array:
  - [Issue #5](https://github.com/ROCm/rocprof-trace-decoder/issues/5)
- Fixed classification of scalar prefetch (was reported as SALU)

### Changes

- s_barrier behaved differently on RDNA2/3:
  - The time spent waiting on s_barrier was mostly reported as idle time.
  - It is now changed to stalled/wait time starting from the last executed instruction.
  - This is an approximation, but will be closer to what RDNA4 and MI series reports.
