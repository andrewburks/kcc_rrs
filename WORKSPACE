workspace(name="tourney_service")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "bazel_skylib",
    sha256 = "f24ab666394232f834f74d19e2ff142b0af17466ea0c69a3f4c276ee75f6efce",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.4.0/bazel-skylib-1.4.0.tar.gz",
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.4.0/bazel-skylib-1.4.0.tar.gz",
    ],
)

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")
bazel_skylib_workspace()

http_archive(
    name = "rules_python",
    sha256 = "36362b4d54fcb17342f9071e4c38d63ce83e2e57d7d5599ebdde4670b9760664",
    strip_prefix = "rules_python-0.18.0",
    url = "https://github.com/bazelbuild/rules_python/releases/download/0.18.0/rules_python-0.18.0.tar.gz",
)

load("@rules_python//python:repositories.bzl", "python_register_toolchains", "py_repositories")

python_register_toolchains(
    name = "python3_11",
    python_version = "3.11.1",
)

py_repositories()

load("@python3_11//:defs.bzl", "interpreter")
load("@rules_python//python:pip.bzl", "pip_parse")

pip_parse(
    name = "gm_deps",
    requirements_lock = "//third_party:requirements_lock.txt",
    python_interpreter_target = interpreter,
)

load("@gm_deps//:requirements.bzl", "install_deps")
install_deps()

http_archive(
    name = "com_github_grpc_grpc",
    sha256 = "df9608a5bd4eb6d6b78df75908bb3390efdbbb9e07eddbee325e98cdfad6acd5",
    strip_prefix = "grpc-1.52.0",
    urls = ["https://github.com/grpc/grpc/archive/v1.52.0.tar.gz"],
)

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")
grpc_deps()

load("@com_github_grpc_grpc//bazel:grpc_extra_deps.bzl", "grpc_extra_deps")
grpc_extra_deps()
