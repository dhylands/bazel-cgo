## Steps to reproduce

Build Machine: MacBookn Pro 15 inch (2019) running macOS Catalina 10.15.7

`bazel --version` reports `bazel 3.1.0`

`go version` reports `go version go1.15.2 darwin/amd64`

I can run `bazel run //hello` and `bazel run //cgo-puts` and everything works fine.

I can also do: `bazel build --platforms=@io_bazel_rules_go//go/toolchain:linux_amd64 //hello` and that seems to be working.

If I try: `bazel build --platforms=@io_bazel_rules_go//go/toolchain:linux_amd64_cgo //cgo-puts` I get the following error:

```
ERROR: While resolving toolchains for target @io_bazel_rules_go//:cgo_context_data: No matching toolchains found for types @bazel_tools//tools/cpp:toolchain_type. Maybe --incompatible_use_cc_configure_from_rules_cc has been flipped and there is no default C++ toolchain added in the WORKSPACE file? See https://github.com/bazelbuild/bazel/issues/10134 for details and migration instructions.
ERROR: Analysis of target '//cgo-puts:cgo-puts' failed; build aborted: No matching toolchains found for types @bazel_tools//tools/cpp:toolchain_type. Maybe --incompatible_use_cc_configure_from_rules_cc has been flipped and there is no default C++ toolchain added in the WORKSPACE file? See https://github.com/bazelbuild/bazel/issues/10134 for details and migration instructions.
INFO: Elapsed time: 0.325s
INFO: 0 processes.
FAILED: Build did NOT complete successfully (20 packages loaded, 370 targets configured)
```
