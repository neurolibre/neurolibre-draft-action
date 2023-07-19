NeuroLibre PDF Generator
===========================

Create a draft companion PDF for NeuroLibre Reproducible Preprints (NRPs).

Usage
-----

Add a file `.github/workflows/draft-pdf.yml` to your repo.

``` yaml
on: [push]

jobs:
  paper:
    runs-on: ubuntu-latest
    name: Paper Draft
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Build draft PDF
        uses: neurolibre/neurolibre-draft-action@master
        with:
          journal: neurolibre
          # This should be the path to the paper within your repo.
          paper-path: paper.md
      - name: Upload
        uses: actions/upload-artifact@v1
        with:
          name: paper
          # This is the output path where Pandoc will write the compiled
          # PDF. Note, this should be the same directory as the input
          # paper.md
          path: paper.pdf
```

This will build the paper.pdf and make it available as an artifact
after each build.

Inputs
------

The build can be configured by setting the following inputs.

### `journal`

The journal for to which this paper will be submitted.

### `paper-path`

Filename of the paper, relative to the project's root directory.
Defaults to `paper.md`.



