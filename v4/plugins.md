# HAROS Plugins

## Registration and Discovery

The ideal option would be to use namespace packages, but it seems that the current implementation of this feature is harder to manage than the alternatives.
Alternative options include:

1. [Naming convention](https://packaging.python.org/guides/creating-and-discovering-plugins/#using-naming-convention) (current approach) using the `haros_plugin_*` prefix.
2. `setuptools` [entry point](https://setuptools.readthedocs.io/en/latest/userguide/entry_point.html#advertising-behavior) for `haros.plugins`.

Plugins were previously used only for analysis, following a hook style (like [Pytest](https://docs.pytest.org/en/latest/how-to/writing_plugins.html#writing-your-own-plugin)).
It is likely that hooks will be the go-to option here, but the hook interface might be extended to other functionalities.
