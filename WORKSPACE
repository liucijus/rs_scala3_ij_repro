workspace(name = "rs_scala3")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

local_repository(
    name = "io_bazel_rules_scala",
    path = "../rules_scala",
)

skylib_version = "1.0.3"

http_archive(
    name = "bazel_skylib",
    sha256 = "1c531376ac7e5a180e0237938a2536de0c54d93f5c278634818e0efc952dd56c",
    type = "tar.gz",
    url = "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/{}/bazel-skylib-{}.tar.gz".format(skylib_version, skylib_version),
)

load("@io_bazel_rules_scala//:scala_config.bzl", "scala_config")

scala_config(scala_version = "3.1.0")

load("@io_bazel_rules_scala//scala:scala.bzl", "scala_repositories")

scala_repositories(fetch_sources = True)

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_JVM_EXTERNAL_TAG = "4.2"

RULES_JVM_EXTERNAL_SHA = "cd1a77b7b02e8e008439ca76fd34f5b07aecb8c752961f9640dea15e9e5ba1ca"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:repositories.bzl", "rules_jvm_external_deps")

rules_jvm_external_deps()

load("@rules_jvm_external//:setup.bzl", "rules_jvm_external_setup")

rules_jvm_external_setup()

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "org.scala-lang:scala3-library_3:jar:3.1.3",
        "org.scala-lang:scala3-compiler_3:3.1.0",
        "org.scala-lang:scala3-interfaces:3.1.0",
        "org.scala-lang:tasty-core_3:3.1.0",
        "org.scala-lang.modules:scala-asm:9.1.0-scala-1",
        "org.scala-lang:scala-library:jar:2.13.8",
    ],
    repositories = [
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

register_toolchains("//:scala3_toolchain")
