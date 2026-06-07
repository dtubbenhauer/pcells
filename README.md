# Low-rank cells and \(p\)-cells

This repository contains supplementary material for a project currently titled

> TBA

The repository has four complementary parts:

1. `low-rank-cells.pdf`, a compiled note collecting low-rank ordinary
   Kazhdan--Lusztig cell data;
2. `low-rank-p-cells.pdf`, a compiled note collecting low-rank \(p\)-cell data,
   including characteristic zero comparison data and guessed asymptotic
   category labels;
3. `pre-computed-data.zip`, the raw output files used for the \(p\)-cell note;
4. Magma code for computing \(p\)-cells in finite Coxeter groups using
   ASLoc/IHecke.

The goal is transparency: the notes give readable summaries, while the raw
files and code allow the computations to be checked or extended.

## Contact

If you find any errors in the paper **please email me**:

[dtubbenhauer@gmail.com](mailto:dtubbenhauer@gmail.com?subject=[GitHub]%web-reps)

Same goes for any errors related to this page.

## Main files

### `low-rank-cells.pdf`

This PDF records ordinary Kazhdan--Lusztig two-sided cells for finite Coxeter
groups in low rank, together with additional information used in the paper.

For each type considered, the tables include:

- the cell numbering;
- the size of each two-sided cell;
- Lusztig's \(a\)-value;
- the number
  \[
      p(J)=\#\{I\subseteq S\mid w_I\in J\},
  \]
  where \(w_I\) is the longest element of the standard parabolic subgroup
  \(W_I\);
- whether the cell is strongly regular;
- for non-strongly-regular cells, the matrix of intersection sizes
  \[
      |R_i\cap L_j|
  \]
  between right and left cells;
- in several cases, the corresponding asymptotic Hecke algebra or category.

A useful check on the parabolic-longest-element data is

\[
    \sum_J p(J)=2^{\operatorname{rk}(W)},
\]

since each subset \(I\subseteq S\) gives exactly one parabolic longest element
\(w_I\).

### `low-rank-p-cells.pdf`

This PDF records low-rank two-sided \(p\)-cells, computed from the
\(p\)-canonical basis.  It is meant as the \(p\)-analogue of
`low-rank-cells.pdf`.

The note includes:

- characteristic zero comparison data;
- the number of \(p\)-cells;
- \(p\)-cell size vectors;
- compressed matrices for non-strongly-regular cells;
- separate positive-characteristic data for types \(B\) and \(C\);
- exceptional low-rank data for \(G_2\), \(F_4\), and \(E_6\);
- guessed asymptotic category labels, with warnings where the interpretation is
  not clear.

The compressed matrix notation is explained in the PDF.  Roughly, it records a
large matrix of intersection sizes by grouping equal row and column profiles.

### `pre-computed-data.zip`

This archive contains the raw output files used to make `low-rank-p-cells.pdf`.
The file names follow the convention

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

These files are useful if you want to check the cell sizes, inspect the raw
`JCell` blocks, or compare the summarized matrices with the full output.

### `GraphCellsH.m`

This Magma script computes \(p\)-canonical basis data for a finite Coxeter
group and prints the two-sided \(p\)-cells as matrices of intersection sizes

```text
|R_i ∩ L_j|
```

It also prints multiplication tables in the \(p\)-canonical basis for diagonal
\(H\)-cells.

The script is intended for finite Coxeter groups.  For large types the full
cell computation can be expensive; use smaller examples or specialized scripts
when only a specific cell is needed.

## Requirements

The Magma scripts use:

1. [Magma](https://magma.maths.usyd.edu.au/magma/);
2. [ASLoc](https://github.com/joelgibson/ASLoc), with `ASLoc.spec` visible from
   the working directory;
3. [IHecke](https://github.com/joelgibson/IHecke), available through ASLoc.

A typical setup is to run the scripts from a directory where Magma can see
ASLoc, for example from inside a local ASLoc checkout.

## Examples

Create save and output directories once:

```bash
mkdir -p saves outputs
```

Run small examples:

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

Common arguments:

- `type`: Cartan type, for example `B6`, `C6`, `D6`, `G2`, `F4`, `E6`;
- `char`: characteristic, either `0` or a prime;
- `saveDir`: optional directory for resumable serialized basis data;
- `targetLength`: optional length cutoff for tests;
- `profileName`: optional Magma profiling label;
- `chatty`: optional ASLoc verbosity.

## Relation to the paper

The data are used to support statements about parabolic diagonal cells,
strongly regular cells, subregular \(p\)-cells, and related low-rank checks in
finite Weyl groups.

The suggested citation is:

```bibtex
@misc{MRT,
  author = {Miemietz, Vanessa and Roth, Marie and Tubbenhauer, Daniel},
  title = {Low-rank Kazhdan--Lusztig cell and p-cell data},
  year = {2026},
  note = {Supplementary computational data},
  url = {https://github.com/dtubbenhauer/pcells}
}
```

## Repository contents

Current intended contents:

```text
README.md
LICENSE
GraphCellsH.m
low-rank-cells.pdf
low-rank-p-cells.pdf
pre-computed-data.zip
```

Additional scripts, logs, source files, or corrected output files may be added
later.

## Erratum

Empty so far.
