load("//cuda:defs.bzl", "cuda_library", "requires_cuda_enabled")

cuda_library(
    name = "vectorAdd",
    srcs = ["vectorAdd.cu"],
    hdrs = ["vectorAdd.h"],
    target_compatible_with = requires_cuda_enabled(),
)

# Run with 'bazel run --cuda main'
cc_binary(
    name = "main",
    srcs = ["main.cc"],
    deps = [":vectorAdd"],
)
