load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_library", "go_test")

go_library(
    name = "go_default_library",
    srcs = [
        "doc.go",
        "main.go",
        "server.go",
    ],
    importpath = "k8s.io/test-infra/experiment/cherrypicker",
    visibility = ["//visibility:private"],
    deps = [
        "//prow/git:go_default_library",
        "//prow/github:go_default_library",
        "//prow/hook:go_default_library",
        "//prow/plugins:go_default_library",
        "//vendor/github.com/satori/go.uuid:go_default_library",
        "//vendor/github.com/sirupsen/logrus:go_default_library",
    ],
)

go_binary(
    name = "cherrypicker",
    importpath = "k8s.io/test-infra/experiment/cherrypicker",
    library = ":go_default_library",
    visibility = ["//visibility:public"],
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [":package-srcs"],
    tags = ["automanaged"],
    visibility = ["//visibility:public"],
)

go_test(
    name = "go_default_test",
    srcs = ["server_test.go"],
    importpath = "k8s.io/test-infra/experiment/cherrypicker",
    library = ":go_default_library",
    deps = [
        "//prow/git/localgit:go_default_library",
        "//prow/github:go_default_library",
        "//vendor/github.com/sirupsen/logrus:go_default_library",
    ],
)
