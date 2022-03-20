load("@rules_cuda//cuda:defs.bzl", "cuda_library", "requires_cuda_enabled")

cuda_library(
    name = "hello_world_gpu_lib",
    srcs = ["hello_world.cu"],
    target_compatible_with = requires_cuda_enabled(),
)

# Run with 'bazel run --cuda hello_world'
cc_binary(
    name = "hello_world",
    deps = [
        ":hello_world_gpu_lib",
    ],
)

cuda_library(
    name = "vector_add_gpu_lib",
    srcs = ["vector_add.cu"],
    target_compatible_with = requires_cuda_enabled(),
)

# Run with 'bazel run --cuda vector_add'
cc_binary(
    name = "vector_add",
    deps = [
        ":vector_add_gpu_lib",
    ],
)
