# Low-rank cells and p-cells

This repository contains code and additional calculations for the paper

> *The subregular and submaximal p-cells*

by Vanessa Miemietz, Marie Roth and Daniel Tubbenhauer.

The paper is available on the [arXiv](https://arxiv.org/abs/2608.19798).

The paper determines the subregular and submaximal p-cells in finite Weyl groups. In classical type we give explicit descriptions of the relevant p-canonical basis elements and the resulting p-cells; in exceptional type some of the low-rank calculations are done by computer. This repository contains the corresponding ordinary cell data, p-cell data, raw output and Magma code.

## Contact

If you find any errors in the paper **please email me**:

[dtubbenhauer@gmail.com](mailto:dtubbenhauer@gmail.com?subject=[GitHub]%20pcells)

Same goes for any errors related to this page.

## Main files

### `low-rank-cells.pdf`

This PDF records ordinary Kazhdan--Lusztig two-sided cells for finite Coxeter groups in low rank, together with some extra information used in the paper.

For each type considered, the tables include:

- the cell numbering;
- the size of each two-sided cell;
- Lusztig's a-value;
- the number of parabolic longest elements in each cell;
- whether the cell is strongly regular;
- for cells which are not strongly regular, the matrix of intersection sizes between right and left cells;
- in several cases, the corresponding asymptotic Hecke algebra or category.

As a quick check on the parabolic data, the numbers of parabolic longest elements over all two-sided cells add up to 2^rank(W).

### `low-rank-p-cells.pdf`

This PDF records low-rank two-sided p-cells computed from the p-canonical basis. It is the p-analogue of `low-rank-cells.pdf`.

The note includes:

- characteristic zero comparison data;
- the number and sizes of the p-cells;
- intersection matrices for cells which are not strongly regular;
- positive-characteristic data for types B and C;
- low-rank exceptional data for G2, F4 and E6;
- asymptotic category labels in the cases where we have identified them.

For large intersection matrices we use a compressed notation, explained in the PDF.

### `pre-computed-data.zip`

This archive contains the raw output files used to make `low-rank-p-cells.pdf`. The file names follow the convention

```text
<type>-<rank>-<characteristic>.txt
```

for example:

```text
b-6-2.txt
c-6-2.txt
d-6-2.txt
e-6-3.txt
f-4-2.txt
g-2-3.txt
```

The raw files contain the full cell output behind the tables in the PDF.

### `GraphCellsH.m`

This Magma script computes the p-canonical basis for a finite Coxeter group and then its left, right and two-sided p-cells. For each two-sided p-cell it prints the right-cell/left-cell intersection matrix. It also prints multiplication tables in the p-canonical basis for the diagonal H-cells.

The script computes the p-canonical basis elements themselves as well. We do not list these in `low-rank-p-cells.pdf`, since there are far too many of them.

For large types the full computation can take a while. The optional save directory allows an interrupted p-canonical basis calculation to be resumed.

## Requirements

The Magma script uses:

1. [Magma](https://magma.maths.usyd.edu.au/magma/);
2. [ASLoc](https://github.com/joelgibson/ASLoc), with `ASLoc.spec` visible from the working directory;
3. [IHecke](https://github.com/joelgibson/IHecke), available through ASLoc.

A convenient setup is to run the script from a directory where Magma can see ASLoc.

## Examples

Create save and output directories once:

```bash
mkdir -p saves outputs
```

Small examples:

```bash
magma -b type:=G2 char:=2 saveDir:=saves GraphCellsH.m > outputs/g-2-2.txt
magma -b type:=G2 char:=3 saveDir:=saves GraphCellsH.m > outputs/g-2-3.txt
magma -b type:=F4 char:=2 saveDir:=saves GraphCellsH.m > outputs/f-4-2.txt
magma -b type:=F4 char:=3 saveDir:=saves GraphCellsH.m > outputs/f-4-3.txt
```

Some larger examples used in the data files are:

```bash
magma -b type:=B6 char:=2 saveDir:=saves GraphCellsH.m > outputs/b-6-2.txt
magma -b type:=C6 char:=2 saveDir:=saves GraphCellsH.m > outputs/c-6-2.txt
magma -b type:=D6 char:=2 saveDir:=saves GraphCellsH.m > outputs/d-6-2.txt
magma -b type:=E6 char:=3 saveDir:=saves GraphCellsH.m > outputs/e-6-3.txt
```

The main arguments are:

- `type`: Cartan type, for example `B6`, `C6`, `D6`, `G2`, `F4`, `E6`;
- `char`: characteristic, either `0` or a prime;
- `saveDir`: optional directory for resumable p-canonical basis data;
- `targetLength`: optional length cutoff for tests;
- `profileName`: optional Magma profiling label;
- `chatty`: optional ASLoc verbosity.

## Relation to the paper

The ordinary and p-cell tables collect the low-rank calculations used for comparisons and checks in the paper. The Magma code is also used for the exceptional-type computations where the p-cell structure is determined computationally.

If you only want the results, start with `low-rank-cells.pdf` and `low-rank-p-cells.pdf`. If you want to reproduce the calculations, use `GraphCellsH.m` together with the raw files in `pre-computed-data.zip`.

The suggested citation is:

```bibtex
@misc{MRTpcells,
  author = {Miemietz, Vanessa and Roth, Marie and Tubbenhauer, Daniel},
  title = {Code, data and more for ``The subregular and submaximal p-cells''},
  year = {2026},
  url = {https://github.com/dtubbenhauer/pcells}
}
```

## Repository contents

```text
README.md
LICENSE
GraphCellsH.m
low-rank-cells.pdf
low-rank-p-cells.pdf
pre-computed-data.zip
```

## Erratum

Empty so far.
