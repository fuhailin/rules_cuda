load("@rules_cuda//cuda:defs.bzl", "cuda_library", "requires_cuda_enabled")

cc_library(
    name = "cuda_exception",
    hdrs = ["cuda_exception.h"],
)

cc_library(
    name = "cuda_helper_timer",
    hdrs = ["cuda_helper_timer.h"],
    deps = [":cuda_exception"],
)

cuda_library(
    name = "reduction_cg_kernel",
    srcs = ["reduction_cg_kernel.cu"],
    hdrs = ["reduction_cg_kernel.h"],
    target_compatible_with = requires_cuda_enabled(),
)

# Run with 'bazel run --cuda reduction_cg'
cc_binary(
    name = "reduction_cg",
    srcs = ["reduction_cg.cpp"],
    deps = [
        ":cuda_helper_timer",
        ":reduction_cg_kernel",
    ],
)
