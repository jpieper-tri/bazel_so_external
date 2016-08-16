cc_binary(
    name = "libshared_lib.so",
    srcs = ["shared_lib.cc", "shared_lib.h"],
    visibility = ["//visibility:public"],
    linkshared = 1,
)

cc_library(
    name = "shared_lib_hdrs",
    hdrs = glob(["**/*.h"]),
    visibility = ["//visibility:public"],
)

cc_library(
    name = "shared_lib",
    srcs = ["libshared_lib.so"],
    deps = [":shared_lib_hdrs"],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "builtin_app",
    srcs = ["builtin_app.cc"],
    hdrs = ["builtin_app.h"],
    deps = [":shared_lib"],
)

cc_test(
    name = "builtin_app_test",
    defines = ["BOOST_TEST_DYN_LINK"],
    linkopts = ['-lboost_unit_test_framework'],
    deps = ["builtin_app"],
    srcs = [
        "builtin_app_test.cc",
        "test_main.cc",
        ],
)
