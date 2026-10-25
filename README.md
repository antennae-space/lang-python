# Python for Web IDE

The Python language pack of [Web IDE](https://github.com/antennae-space/web-ide): the highlighting of Python, a language server (diagnostics, completion, navigation, rename, the structure of a file) and the test pattern `test_{name}.py`. An official plugin: the IDE installs it by default.

## What it needs

- One of, in this order: **pyright** (`npm install -g pyright`), **basedpyright** (`pipx install basedpyright`), **pylsp** (`pipx install 'python-lsp-server[all]'`: without pyflakes it reports no error), on your PATH.
- The IDE runs it **confined**: it reads your project (not write; its virtualenv included), the program and its package (pyright: the node on your PATH, `NODE`, and its package; basedpyright and pylsp: their virtualenv, or the `~/.local` of a `pip --user` install), keeps its caches in its own folder, and has no network.
- On a project over SSH, the server runs on its host, as you installed it there.

## Permissions

| | |
|---|---|
| `program:pyright-langserver`, `program:basedpyright-langserver`, `program:pylsp` | run the server, confined |
| `path:NODE` | read the node that runs pyright |
| `path:PYRIGHT`, `path:BASEDPYRIGHT`, `path:PYLSP` | read the server's package or virtualenv |

## Develop

A pack is data: `plugin.json` (checked by `node scripts/check.mjs` against the [plugin SDK](https://github.com/antennae-space/plugin-sdk)'s schema) and `grammars/python.json` (a grammar of the IDE's editor). `./scripts/pack.sh` builds the archives; a tag `v*` publishes a release.

## License

MIT.
