# HAROS Home Directory

This is the directory that holds HAROS databases, global configurations, logs, internal files, etc..
There can be multiple of these directories, to allow for different profiles, etc., but only one is used/active at any given time.

## Resolution Order

1. Directory given via the `--home` option (present in v3).
2. Current directory, if it contains some marker file (TBD, possibly `haros.config`).
3. Directory pointed to by the environment variable `HAROS_HOME` (new).
4. Default directory, `~/.haros`, to allow easy one-button-magic.

## Directory Contents

```
+ logs
+ extras (pyflwor, etc.)
+ data
    + <project_name>
        - project.json
        + packages
            + <package name>
                - package.json
                - files.json    (smaller than all in one collection)
                - nodes.json    (same as above)
        - packages.json         (collection view?)
        - files.json            (index to .json file in pkg dir? index by relative pkg/file path?)
        - nodes.json            (index file?)
        + analysis
            + <timestamp>
            - reports.json
+ output?
- haros.config
```

## Configuration File

Contains global settings that can be overriden for specific projects (*à la* git).

```yaml
data:
    driver: tinyDB | "custom_driver_pkg.main_module:DriverClass"
    version: <haros metamodel/storage version>
logs:
    level: info | warn | error
    max_files: 10
    max_size_kb: 10000
```
