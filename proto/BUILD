load("@rules_proto//proto:defs.bzl", "proto_library")
load("@com_github_grpc_grpc//bazel:python_rules.bzl", "py_grpc_library", "py_proto_library")



proto_library(
    name = "helloworld_proto",
    srcs = ["helloworld.proto"],
)

py_proto_library(
    name = "helloworld_py_proto",
    deps = [":helloworld_proto"],
)

py_grpc_library(
    name = "helloworld_py_grpc",
    srcs = [":helloworld_proto"],
    deps = [":helloworld_py_proto"],
)