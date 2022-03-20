# Run with 'bazel run --cuda conv_sample'
cc_binary(
    name = "main",
    srcs = ["main.cc"],
    deps = [
        "@local_config_cuda//cuda:cudnn",
    ],
)
