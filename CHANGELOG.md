# ROCprof Trace Decoder Release Notes

## Descripton

A plugin library for rocprofiler-sdk: https://github.com/rocm/rocprofiler-sdk

Thread trace is a profiling method that provides fine-grained insight into GPU kernel execution by collecting detailed traces of shader instructions executed by the GPU. This feature captures GPU occupancy, instruction execution times, fast performance counters, and other detailed performance data. Thread trace utilizes GPU hardware instrumentation to record events as they happen, resulting in precise timing information about wave (threads) execution behavior.

This library is responsible for transforming thread trace binary data (.att) into a tool consumable format.

<!-- Release Description -->

<!-- Uncomment only the parts that are needed for this release -->

<!--
### Breaking Changes
*
*
-->

## Release 0.1.2

### Resolved issues

- Fixed an issue where stalls were delayed by 1 cycle on gfx10
- Fixed an issue where gfx10 would not properly find the code object id
- Further fixes for PC Sampling (PCS) + Thread trace (TT) combination on MI300

### Changed

- xnack is now reported as stall (was idle time)
- For TT + PCS, the time inside the trap handler is marked as ``ROCPROFILER_THREAD_TRACE_DECODER_INST_CONTEXT``. This type will not have a PC address.

### Added
- new TT2 header versions from aqlprofile

### Upgrade Steps
* Replace the previous installed library by this one
  * First, uninstall previous decoder version to avoid conflicts

## End User License Agreement

See: [LICENSE](LICENSE)
