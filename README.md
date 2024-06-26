# Commands

## Getting started

```bash
pnpm install -g @antfu/ni nx
ni
```

## Package management

```bash
# Create a package
mkdir <pkgDir>
cd <pkgDir>
pnpm init
```

| Management        | Root            | Local package                     |
| ----------------- | --------------- | --------------------------------- |
| Add from registry | `ni -w <deps>`  | `ni <deps> -F <pkg>`              |
| Add from local    |                 | `ni --workspace <deps> -F <pkg>`  |
| Update            | `nu`            | `nu -F <pkg>`                     |
| Update All        | `nu -r`         | `nu -F <pkg> -r`                  |
| Remove            | `nun -w <deps>` | `nun --workspace <deps> -F <pkg>` |

## Build

| Build    | command             |
| -------- | ------------------- |
| one      | `nx build <pkg>`    |
| all      | `nr build:all`      |
| affected | `nr build:affected` |

## Test

## Publish

# Reference

[Tutorial: Getting Started with Package-Based Repos](https://www.youtube.com/watch?v=hzTMKuE3CDw)

[Setup a monorepo with PNPM workspaces and add Nx for speed](https://www.youtube.com/watch?v=ngdoUQBvAjo)

# nx.json

```json
{
  "namedInputs": {
    // exclude markdown files from caching
    "noMarkdown": ["!{projectRoot}/**/*.md"]
  },
  "targetDefaults": {
    "build": {
      // exclude markdown files from caching for the package and its dependencies
      "inputs": ["noMarkdown", "^noMarkdown"],
      // when build a package, build all packages that it's depended on
      "dependsOn": ["^build"]
    }
  }
}
```
