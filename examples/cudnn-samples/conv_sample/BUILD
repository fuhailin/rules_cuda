load(
    "@rules_cuda//cuda:defs.bzl",
    "cuda_library",
    "requires_cuda_enabled",
)

cuda_library(
    name = "fp16_emu_lib",
    srcs = ["fp16_emu.cpp"],
    hdrs = ["fp16_emu.h"],
    target_compatible_with = requires_cuda_enabled(),
)

cuda_library(
    name = "error_util",
    hdrs = ["error_util.h"],
    target_compatible_with = requires_cuda_enabled(),
)

cuda_library(
    name = "fp16_dev_lib",
    srcs = ["fp16_dev.cu"],
    hdrs = ["fp16_dev.h"],
    deps = [
        ":error_util",
        ":fp16_emu_lib",
    ],
)

cuda_library(
    name = "conv_sample_lib",
    srcs = ["conv_sample.cpp"],
    deps = [
        ":fp16_dev_lib",
        ":fp16_emu_lib",
    ],
)

# Run with 'bazel run --cuda conv_sample'
cc_binary(
    name = "conv_sample",
    deps = [
        ":conv_sample_lib",
        "@local_config_cuda//cuda:cudnn",
    ],
)
