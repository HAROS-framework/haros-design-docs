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

### Distribution: `haros-metamodel`

Library with the HAROS metamodel.

### Distribution: `haroscpp`

Library and tool to parse and interpret `roscpp` files (extract Nodes and primitives).

### Distribution: `harospy`

Library and tool to parse and interpret `rospy` files (extract Nodes and primitives).

### Distribution: `haroslaunch`

Library and tool to parse and interpret `roslaunch` files (extract runtime Nodes, etc.).

### Distribution: `harosmake`

Tool to discover and build ROS workspaces.
Finds packages, lists files and executables, and calls the other tools to extract models.

### Distribution: `haroscheck`

Plugin-based analysis tools. Receives a model and runs plugins on it.

### Distribution: `harosviz`

Model and report visualizer.

### Distribution: `haros`

Depends on all the above (sort of a metapackage with cli and storage).

## Possibly Relevant Links

Plugin-driven architectures using namespace packages:

- https://pawamoy.github.io/posts/plugins-as-python-native-namespace-packages/
- https://straightplugin.readthedocs.io/en/latest/getting-started.html
- https://github.com/napari/napari/issues/139
