# ROCprof Trace Decoder

> [!CAUTION]
> The rocprof-trace-decoder repository is retired, please use the [ROCm/rocm-systems](https://github.com/ROCm/rocm-systems) repository

## Description

A plugin library for rocprofiler-sdk: https://github.com/ROCm/rocm-systems/tree/develop/projects/rocprofiler-sdk

Thread trace is a profiling method that provides fine-grained insight into GPU kernel execution by collecting detailed traces of shader instructions executed by the GPU. This feature captures GPU occupancy, instruction execution times, fast performance counters, and other detailed performance data. Thread trace utilizes GPU hardware instrumentation to record events as they happen, resulting in precise timing information about wave (threads) execution behavior.

This library is responsible for transforming thread trace binary data (.att) into a tool consumable format.
