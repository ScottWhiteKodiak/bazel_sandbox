################################################################################################
#  Be familiar with THIRD_PARTY.md for details on process necessary for third party libraries. #
################################################################################################

workspace(
    name = "bazel_sandbox",
)

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "bazel_skylib",
    branch = "main",
    remote = "git@github.com:bazelbuild/bazel-skylib.git",
)

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")
bazel_skylib_workspace()
load("@bazel_skylib//lib:versions.bzl", "versions")
versions.check(minimum_bazel_version = "5.1.1")

git_repository(
    name = "toolchains_llvm",
    commit = "19b0b2e0622d11a7c4c19e587518d5ef942e45f8",
    remote = "git@github.com:ScottWhiteKodiak/toolchains_llvm.git",
)

load("@toolchains_llvm//toolchain:rules.bzl", "llvm_toolchain")

llvm_toolchain(
    name = "llvm_toolchain",
    llvm_versions = {
        "": "15.0.6",
    },
)

register_toolchains(
    "//toolchain:clang_toolchain",
)
