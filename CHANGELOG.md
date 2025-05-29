# ROCprof Trace Decoder Release Notes

## Descripton

A plugin library for rocprofiler-sdk: https://github.com/rocm/rocprofiler-sdk

Thread trace is a profiling method that provides fine-grained insight into GPU kernel execution by collecting detailed traces of shader instructions executed by the GPU. This feature captures GPU occupancy, instruction execution times, fast performance counters, and other detailed performance data. Thread trace utilizes GPU hardware instrumentation to record events as they happen, resulting in precise timing information about wave (threads) execution behavior.

This library is responsible for transforming thread trace binary data (.att) into a tool consumable format.

## Usage

### rocprofv3 tool

```bash
rocprofv3 --att -- ./a.out
```

By default, rocprofv3 searches ``LD_LIBRARY_PATH`` and the rocprofiler-sdk install location, normally ``/opt/rocm/lib``. For custom install locations, use

```bash
rocprofv3 --att --att-library-path /path/to/lib -- ./a.out
```

### Rocprofiler-sdk API

Rocprofiler-sdk requires the library path to be provided at resource creation:

```bash
rocprofiler_thread_trace_decoder_handle_t decoder{};
# Notes: Passing null string "" searches in LD_LIBRARY_PATH. Passing nullptr is not allowed.
auto status = rocprofiler_thread_trace_decoder_create(&decoder, "/opt/rocm/lib");
```

### Supported devices

- AMD Radeon: 6000, 7000, 9000 series
- AMD Instinct: MI200 and MI300 series

## End User License Agreement

See: [LICENSE](LICENSE)

<!-- Release Description -->

<!-- Uncomment only the parts that are needed for this release -->
<!--
### Upgrade Steps
* [ACTION REQUIRED]
*
-->

<!--
### Breaking Changes
*
*
-->

<!--
### New Features
*
*
-->

<!--
### Bug Fixes
*
*
-->

<!--
### Performance Improvements
*
*
-->

<!--
### Other Changes
*
*
-->
