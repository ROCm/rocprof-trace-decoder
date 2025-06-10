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

## Release 0.1.1

### New Features
* (Experimental) Support for PC sampling to be run at the same time as thread trace in MI300

### Bug Fixes
* Fixed an issue where gfx11 and gfx12 GPUs would not report packet losses
* Fixed an issue where decoding would not work under CWSR on gfx11 and gfx12 GPUs
* Fixed some issues caught by sanitizers
* Stochastic traps should no longer cause parsing to fail

### Performance Improvements
* Increased performance and reduced memory usage of gfx9 traces

### Other Changes
* Invalid instructions are reported as category == 0, "NONE" (was category == 16)

### Upgrade Steps
* Replace the previous installed library by this one

## End User License Agreement

See: [LICENSE](LICENSE)
