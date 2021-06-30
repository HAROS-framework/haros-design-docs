# Implementation Architecture

## Python Packages

```
+ haros (package, core)
    + cli (input)
    + filesystem (ws)
        - ros.py
        - ros2.py
        - common.py
    + storage (input/output, package, core)
        + tinydb (package, core)
    + data (package, core)
        - ros.py        (core)
        - ros2.py       (core)
        - structs.py    (core)
        - logic.py      (core)
    + parsers (model)
        + cmake
        + roscpp
        + rospy
        + rclcpp
        + rclpy
        + launchxml
        + pkgxml
    + analysis
        - plugin_interface.py
+ haros_plugins (namespace)
    - metamodel.py (read-only objects wrapping true model)
```

## Possibly Relevant Links

Plugin-driven architectures using namespace packages:

- https://pawamoy.github.io/posts/plugins-as-python-native-namespace-packages/
- https://straightplugin.readthedocs.io/en/latest/getting-started.html
- https://github.com/napari/napari/issues/139
