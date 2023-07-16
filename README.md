# Install

### install dependencies

```bash
pnpm install -g @antfu/ni nx
ni
```

### add dependencies

```bash
ni -w <dependencies>
ni -w -D <devDependencies>
```

### add local packages

```bash
ni --workspace <packages> --filter <target>
```

# Create a new package

```bash
mkdir <packageDir>
cd <packageDir>
pnpm init
```

# Build

### Build one package

```bash
nx build <package>
```

### Build all packages

```bash
nr build:all
```

### Build affected packages

```bash
nr build:affected
```

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
