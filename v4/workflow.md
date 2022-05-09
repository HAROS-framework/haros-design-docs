# Workflow

## Model Extraction

### Packages and Files

1. User supplies paths to workspaces or packages.
2. Discover all packages and files in the given paths.
3. Filter out ignored packages, provided via settings.
4. Discover nodes within each package and their types (C++, Python).

### Executable Nodes

1. Assign source files to nodes.
2. Select and appropriate parser for each node type.
3. Traverse the code graphs and find publishers, subscribers, etc..

#### C++ Nodes

- Analysis based on [Joern](https://joern.io/).
- Joern is launched as a server, and the [Python client library](https://github.com/joernio/cpgqls-client-python) queries it.
- Joern collects [*projects*](https://docs.joern.io/organizing-projects) under a *workspace* (more or less like HAROS collects projects under a *home* directory).
- Each Joern project corresponds to one *program*, so we should create one project per Node.
- **Caveat:** Joern projects seem to be bound to one top-level directory that contains all the code.
We can create one project per node, but they probably will share the package directory.
