# Latex Action 

This action compiles latex/xelatex files using [Tectonic](https://tectonic-typesetting.github.io/en-US/), which automatically downloads necessary dependencies, and compiles to pdf.

## Inputs

### `tex-path`

**Required** Path of tex, xtx file to compile.

### `push`

**Optional** Compiled PDF is pushed, if `push` is passed as 'yes'.

### `push_path`

**Optional** Path to push compiled PDF to, if defined.

### `push_branch`

**Optional** Branch to push compiled PDF to, if defined. *(Default: Branch in which action is triggered)*

### `logging`

**Optional** Whether to output API response when status code is not 2XX. True if `logging` is passed as 'yes'. Default is 'no'.

## Outputs
Pushes a Compiled PDF file parallel to the tex, xtx file, if push is passed as 'yes' and push_path is undefined. Otherwise a Compiled PDF file will be pushed to the location defined in push_path, if push is passed as 'yes'. Logging is false by default.

## Example usage

### Pushes Compiled PDF
```
on: [push]

jobs:
  latex-job:
    runs-on: ubuntu-latest
    name: A job to Compile Latex file
    steps:
    - uses: actions/checkout@v1
    - name: Compilation
      uses: vinay0410/tectonic-action@master
      env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        tex_path: 'dir/file.tex'
        push: 'yes'
        push_path: 'output_dir'
        push_branch: 'gh-pages'
        logging: 'yes'
```

### Doesn't Push Compiled PDF
```
on: [push]

jobs:
  latex-job:
    runs-on: ubuntu-latest
    name: A job to Compile Latex file
    steps:
    - uses: actions/checkout@v1
    - name: Compilation
      uses: vinay0410/tectonic-action@master
      env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        tex_path: 'dir/file.tex'
```
