# Copyright (c) 2022 Mark Friedenbach
#
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

# absl source code repository
git_repository(
    name = "com_google_absl",
    remote = "https://github.com/abseil/abseil-cpp.git",
    commit = "215105818dfde3174fe799600bb0f3cae233d0bf",
    shallow_since = "1635953174 -0400",
)

# boringssl source code repository
git_repository(
    name = "boringssl",
    remote = "https://github.com/google/boringssl.git",
    commit = "2a0e6de411bb141e2fe169cee445741137478ef3",
    shallow_since = "1641854268 +0000",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_foreign_cc",
    strip_prefix = "rules_foreign_cc-0.7.1",
    url = "https://github.com/bazelbuild/rules_foreign_cc/archive/refs/tags/0.7.1.zip",
    sha256 = "7350440503d8e3eafe293229ce5f135e8f65a59940e9a34614714f6063df72c3",
)

# This sets up some common toolchains for building targets; includes
# repositories needed by rules_foreign_cc, and creates some utilities
# for the host operating system.  For more details, please see:
# https://github.com/bazelbuild/rules_foreign_cc/tree/main/docs#rules_foreign_cc_dependencies
load("@rules_foreign_cc//foreign_cc:repositories.bzl", "rules_foreign_cc_dependencies")
rules_foreign_cc_dependencies()

# Group the sources of the library so that CMake rule have access to it
_ALL_CONTENT = """\
filegroup(
    name = "all_srcs",
    srcs = glob(["**"]),
    visibility = ["//visibility:public"],
)
"""

# cpp-httplib source code repository
http_archive(
    name = "cpp_http",
    build_file_content = _ALL_CONTENT,
    strip_prefix = "cpp-httplib-0.10.1",
    url = "https://github.com/yhirose/cpp-httplib/archive/refs/tags/v0.10.1.zip",
    sha256 = "4576b7f1775cc25ab5f76a9be8798910f756792e45b372127b0f5c018e86145e",
)

# univalue source code repository
http_archive(
    name = "univalue",
    build_file_content = _ALL_CONTENT,
    strip_prefix = "univalue-1.1.1",
    url = "https://github.com/jgarzik/univalue/archive/refs/tags/v1.1.1.zip",
    sha256 = "50a4e306c782c77b84dee5c53049c0a072e1973d6bb76141cf41cec6ae57649f",
)

# cross-compiler for arm/arm64
http_archive(
    name = "murtis_bazel_compilers",
    urls = [
      "https://github.com/curtismuntz/bazel_compilers/archive/e7c3ee9820bfde7f7284bbc3a9540293741719cd.tar.gz",
    ],
    strip_prefix = "bazel_compilers-e7c3ee9820bfde7f7284bbc3a9540293741719cd",
)

load("@murtis_bazel_compilers//compilers:dependencies.bzl", "cross_compiler_dependencies")

cross_compiler_dependencies()

# End of File
