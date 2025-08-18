# Changelog for release 0.1.3

### Resolved issues

- Fixed an issue where large traces (~GB) would fail to parse or return _INVALID_SHADER_DATA
- Fixed timing of fp64 ops in gfx12

### Added

- Support for MacOS x86 and ARM
  - Minimum version MAC OSX 12.7.3
- Headers are now included as part of this repository
  - ROCprof Trace Decoder is experimental and subject to API changes

####  New record: REALTIME
  - API types:
    - rocprofiler_thread_trace_decoder_realtime_t
    - ROCPROFILER_THREAD_TRACE_DECODER_RECORD_REALTIME
    - ROCPROFILER_THREAD_TRACE_DECODER_RECORD_RT_FREQUENCY
  - This is the realtime clock timestamp. Some use cases:
    - Calculate the gfxclock
    - Correlate the trace with timestamps from other profiling methods
    - Correlate with s_memrealtime
  - For now, gfx9 only generates RT timestamps at trace endpoints

#### New record: SHADERDATA
  - API types:
    - rocprofiler_thread_trace_decoder_shaderdata_t
    - ROCPROFILER_THREAD_TRACE_DECODER_RECORD_SHADERDATA
  - This record is generated when the shader program executes:
    - s_ttracedata
    - s_ttracedata_imm (gfx11+)
  - Usage:
    ```bash
    # The 32-bit contents of the m0 register are sent to the SQTT buffer and surfaced via SHADERDATA
    asm volatile("s_mov m0, 0x1234;"
                 "s_nop 1;"
                 "s_ttracedata;");
    # Note gfx9 requires a waitstate
    # gfx11 and gfx12 can also accept a 8-bit immediate value with reduced bandwidth use
    asm volatile("s_ttracedata_imm 0x12");
    ```
    - Typical usage: Binary instrumentation
    - If ttracedata is used often, we recommend to reduce the SQTT bandwidth with:
      - ROCPROFILER_THREAD_TRACE_PARAMETER_NO_DETAIL
      - This will remove instruction profiling from the trace, related to the rocprofiler_thread_trace_decoder_wave_t record
    - If thread trace is disabled, s_ttracedata is executed as s_nop
    - Example usage in profiler tests: [Kernel](https://github.com/ROCm/rocm-systems/blob/develop/projects/rocprofiler-sdk/tests/thread-trace/kernel_lds.cpp#L57) and [Record](https://github.com/ROCm/rocm-systems/blob/develop/projects/rocprofiler-sdk/tests/thread-trace/trace_callbacks.cpp#L88)
