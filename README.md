# pulsar-IDE-python package


Python language support for [Pulsar-edit](https://pulsar-edit.dev) (and [Atom](https://github.com/atom/atom)), powered by the [Python LSP server](https://github.com/python-lsp/python-lsp-server).

The Atom IDE-Python package has had a convoluted history, unfortunately the fall of Atom and rise of Pulsar-edit has resulted in a lot of packages no longer being maintained. The original version of the gives a "cannot be activated" error on the final release versions of Atom and all versions of Pulsar.

In this fork, the code supporting the debugger feature have been removed (I don't think the debugger was functioning anyway). It now installs and functions properly in the latest versions of Pulsar.

![ide-python](https://user-images.githubusercontent.com/13285808/30352538-b9687a76-9820-11e7-8876-c22751645d36.png)

## Requirements

The [`pulsar-ide-python`](https://atom.io/packages/ide-python) package requires either [Pulsar-edit](https://pulsar-edit.dev) or [Atom `1.60+`](https://github.com/atom/atom), a [Python language server](https://github.com/python-lsp/python-lsp-server), and the [`atom-ide-base`](https://github.com/atom-community/atom-ide-base) package to expose the functionality within Pulsar/Atom.


### Important

Please note that `atom-ide-ui` is now deprecated, therefore, you must use the `atom-ide-base` packages supplied from `atom-ide-community` as mentioned above.

It is also advised to use the `pylsp` language server for Python, instead of the similarly names `pyls` language server, which is now deprecated.

## Feature Providers

- [Jedi](https://github.com/davidhalter/jedi) for Completions, Definitions, Hover, References, Signature Help, and Symbols
- [Rope](https://github.com/python-rope/rope) for Completions and renaming
- [Pyflakes](https://github.com/PyCQA/pyflakes) linter to detect various errors
- [McCabe](https://github.com/PyCQA/mccabe) linter for complexity checking
- [pycodestyle](https://github.com/PyCQA/pycodestyle) linter for style checking
- [Pylint](https://www.pylint.org/) linter to detect various errors
- [Flake8](http://flake8.pycqa.org/en/latest/) linter to detect various errors
- [pydocstyle](https://github.com/PyCQA/pydocstyle) linter for docstring style checking
- [autopep8](https://github.com/hhatto/autopep8) for code formatting (preferred over YAPF)
- [YAPF](https://github.com/google/yapf) for code formatting

## Installation

### Language Server

Install the language server (0.29.0 or newer) with:

```bash
python -m pip install 'python-lsp-server[all]'
```

This command will install the language server and all supported feature providers, which can be enabled or disabled in the settings. Checkout the [official installation instructions](https://github.com/python-lsp/python-lsp-server#installation) on how to install only the providers you need.

You can verify that everything is correctly installed by running `python -m pylsp --help` from the command line.
It should return

```bash
usage: pylsp [-h] [--tcp] [--ws] [--host HOST] [--port PORT] [--check-parent-process] [--log-config LOG_CONFIG | --log-file LOG_FILE] [-v] [-V]

Python Language Server
...
```

If you have installed `pylsp` using a non default installation of Python, you can add modify the _Python Executable_ config in the `ide-python` settings.

### Pulsar Package

Install `ide-python` and [`atom-ide-base`](https://web.pulsar-edit.dev/packages/pulsar-ide-python) from _Install_ in Pulsar's settings or run:

```bash
ppm install atom-ide-base
ppm install pulsar-ide-python
```

## Configuration

Configuration is loaded from zero or more configuration sources.

- `pycodestyle`: discovered in `~/.config/pycodestyle`, `setup.cfg`, `tox.ini` and `pycodestyle.cfg`
- `flake8`: discovered in `~/.config/flake8`, `setup.cfg`, `tox.ini` and `flake8.cfg`

Overall configuration is computed first from user configuration (in home directory), overridden by configuration in the `ide-python` settings, and then overridden by configuration discovered in the current project.

## Contributing

Always feel free to help out! Whether it's [filing bugs and feature requests](https://github.com/mjrodgers/ide-python/issues/new) or working on some of the [open issues](https://github.com/mjrodgers/ide-python/issues).

## License

MIT License. See [the license](LICENSE.md) for more details.
