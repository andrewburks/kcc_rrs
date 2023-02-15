
load("@gm_deps//:requirements.bzl", "requirement")

load("@rules_python//python:defs.bzl", "py_library")

py_library(
    name = "webapp",
    srcs = ["webapp.py"],
    deps = [
        requirement("fastapi"),
        requirement("grpcio"),
        "//proto:helloworld_py_grpc"
        ],
)

# to add additionals parameters place them after "--" in bazel call, like:
# `bazel run //tourney_service:run -- --reload`
py_binary(
    name = "run",
    srcs = ["run.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    visibility = ["//visibility:public"],
    deps = [
        ":webapp",
        requirement("uvicorn"),
    ],
)

py_binary(
    name = "main",
    srcs = ["main.py"],
    deps = [
        requirement("attrs"),
        requirement("more-itertools"),
        requirement("packaging"),
        requirement("pluggy"),
        requirement("py"),
        requirement("pytest"),
        requirement("wcwidth"),
    ],
    python_version = "PY3",
    srcs_version = "PY3",
)

py_test(
    name = "main_test",
    srcs = ["main_test.py"],
    deps = [
        requirement("attrs"),
        requirement("more-itertools"),
        requirement("packaging"),
        requirement("pluggy"),
        requirement("py"),
        requirement("pytest"),
        requirement("wcwidth"),
    ],
)