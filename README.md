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
nr build
```

# Reference

[Tutorial: Getting Started with Package-Based Repos](https://www.youtube.com/watch?v=hzTMKuE3CDw)

[Setup a monorepo with PNPM workspaces and add Nx for speed](https://www.youtube.com/watch?v=ngdoUQBvAjo)

# nx.json

```json
  "targetDefaults": {
    "build": {
      "dependsOn": [
        // when build a package, build all packages that it's depended on
        "^build"
      ]
    }
  }
```
