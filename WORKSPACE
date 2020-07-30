load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "0f2de53628e848c1691e5729b515022f5a77369c76a09fbe55611e12731c90e3",
    urls = [
        "https://github.com/bazelbuild/rules_nodejs/releases/download/2.0.1/rules_nodejs-2.0.1.tar.gz",
    ],
)

load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories", "yarn_install")

node_repositories()

yarn_install(
    name = "lib_a_npm",
    package_json = "//lib_a:package.json",
    yarn_lock = "//lib_a:yarn.lock",
)

yarn_install(
    name = "app_npm",
    package_json = "//app:package.json",
    yarn_lock = "//app:yarn.lock",
)
