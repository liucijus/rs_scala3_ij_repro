load("@io_bazel_rules_scala//scala:scala.bzl", "scala_library")
load("@io_bazel_rules_scala//scala:providers.bzl", "declare_deps_provider")
load("@io_bazel_rules_scala//scala:scala_toolchain.bzl", "scala_toolchain")

declare_deps_provider(
    name = "scala_compile_classpath_provider",
    deps_id = "scala_compile_classpath",
    visibility = ["//visibility:public"],
    deps = [
        "@io_bazel_rules_scala_scala_library_2",
        "@maven//:org_scala_lang_modules_scala_asm",
        "@maven//:org_scala_lang_scala3_compiler_3",
        "@maven//:org_scala_lang_scala3_interfaces",
        "@maven//:org_scala_lang_scala3_library_3",
        "@maven//:org_scala_lang_tasty_core_3",
    ],
)

declare_deps_provider(
    name = "scala_library_classpath_provider",
    deps_id = "scala_library_classpath",
    visibility = ["//visibility:public"],
    deps = [
        "@io_bazel_rules_scala_scala_library_2",
        "@maven//:org_scala_lang_scala3_library_3",
    ],
)

declare_deps_provider(
    name = "scala_macro_classpath_provider",
    deps_id = "scala_macro_classpath",
    visibility = ["//visibility:public"],
    deps = [
        "@io_bazel_rules_scala_scala_library_2",
        "@maven//:org_scala_lang_scala3_library_3",
    ],
)

scala_toolchain(
    name = "scala3_toolchain_impl",
    dep_providers = [
        "@io_bazel_rules_scala//scala:scala_xml_provider",
        "@io_bazel_rules_scala//scala:parser_combinators_provider",
        ":scala_compile_classpath_provider",
        ":scala_library_classpath_provider",
        ":scala_macro_classpath_provider",
    ],
    scalacopts = [],
    visibility = ["//visibility:public"],
)

toolchain(
    name = "scala3_toolchain",
    toolchain = ":scala3_toolchain_impl",
    toolchain_type = "@io_bazel_rules_scala//scala:toolchain_type",
    visibility = ["//visibility:public"],
)

scala_library(
    name = "simple",
    srcs = ["Foo.scala"],
)
