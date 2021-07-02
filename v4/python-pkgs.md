# Implementation Architecture

## Python Packages (Multi-distribution Approach)

The multi-distribution approach is appealing from a developer's point of view.
Everything can be implemented, fixed and iterated independently.
However, there are some caveats.
From a user's point of view, installing new features or updating HAROS to get the latest fixes is not so straightforward, e.g.,

```
$ pip install -U haroscpp
```

Instead of

```
$ pip install -U haros
```

This could be circumvented by pushing a new version of `haros` every time one of the dependencies is fixed.
But, in practice, all that gives us is one additional way to mess things up (e.g., forgetting to update `haros`), and achieves exactly the same thing as packing everything under a single distribution.
The root cause of this is *coupling* - every component is tightly coupled to the metamodel, and any changes to that must propagate all the way up.

This is not to say that this approach does not work.
It does, but the development process requires careful version and dependency management.
Perhaps some of it could be automated with scripts.

### Distribution: `haros-metamodel`

Library with the HAROS metamodel.

```
+ haros (namespace)
    + metamodel
        - ros.py
        - ros2.py
        - structs.py
        - logic.py
```

### Distribution: `haroscpp`

Library and tool to parse and interpret `roscpp` and `rclcpp` files (extract Nodes and primitives).

```
+ haros (namespace)
    + parsers (namespace)
        - roscpp.py
        - rclcpp.py
+ haroscpp
    - ...
```

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
