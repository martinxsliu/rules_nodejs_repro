# Issue

Running `bazel build //app:with_lib` fails with the following error message:

```
➜  rules_nodejs_repro git:(master) bazel build //app:with_lib
ERROR: /Users/martin/repos/rules_nodejs_repro/lib_a/BUILD.bazel:3:11: Provider es6_module_mappings provided twice
ERROR: Analysis of target '//app:with_lib' failed; build aborted: com.google.devtools.build.lib.skyframe.ConfiguredValueCreationException: Provider es6_module_mappings provided twice
INFO: Elapsed time: 0.118s
INFO: 0 processes.
FAILED: Build did NOT complete successfully (0 packages loaded, 2 targets configured)
```

The issue is triggered when a `ts_library` target from one repository (`@app_npm`)
has dependencies on `ts_library` targets from another repository.

Note that `//lib_a:ts_library` and `//app:main` both build successfully as they only
depend on their own repositories.
