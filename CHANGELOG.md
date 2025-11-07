# Changelog for release 0.1.5

### Resolved issues

- Fixed an issue in gfx11 and gfx12 where stalled and idle time would be incorrect by 4 cycles.
  - Issue: https://github.com/ROCm/rocprof-trace-decoder/issues/2 

### Added

- Initial double buffering suport for gfx12 and MI300 series

- New rocord: rocprofiler_thread_trace_decoder_inst_other_simd_t
  - Provides VMEM/LDS/FLAT operations on the other SIMD sharing VMEM issue on the target wgp.
  - Identified by ROCPROFILER_THREAD_TRACE_DECODER_RECORD_INST_OTHER_SIMD

- Defined macros for retrieving SA from .cu field in most records:
  - ROCPROFILER_TRACE_DECODER_CU_*
  - Previously arbitrary, the last bit (bit=7) of struct.cu will define SA of WGP
