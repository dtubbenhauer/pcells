# TBA

This repository contains supplementary material for the project currently titled

> TBA

The repository currently has two complementary parts:

1. a compiled note, `low-rank-cells.pdf`, collecting low-rank ordinary
   Kazhdan--Lusztig cell data;
2. Magma code for computing \(p\)-cells in finite Coxeter groups using
   ASLoc/IHecke.

## Contact

If you find an error in the data or code, please email:

[daniel.tubbenhauer@sydney.edu.au](mailto:daniel.tubbenhauer@sydney.edu.au)

Same goes for errors related to this repository.

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

The purpose of this file is to make the low-rank cell computations transparent
and easy to cite. In particular, it records which strongly regular cells contain
longest elements of standard parabolic subgroups.

A useful check on the parabolic-longest-element data is

\[
    \sum_J p(J)=2^{\operatorname{rk}(W)},
\]

since each subset \(I\subseteq S\) gives exactly one parabolic longest element
\(w_I\).

### `GraphCellsH.m`

This Magma script computes \(p\)-canonical basis data for a finite Coxeter
group and prints the two-sided \(p\)-cells as matrices of intersection sizes

```text
|R_i ∩ L_j|
```

It also prints multiplication tables in the \(p\)-canonical basis for diagonal
\(H\)-cells.

The script is intended for finite Coxeter groups. For large types the full cell
computation can be expensive; use smaller examples or specialized scripts when
only a specific cell is needed.

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

Common arguments:

- `type`: Cartan type, for example `G2`, `F4`, `E6`;
- `char`: characteristic, either `0` or a prime;
- `saveDir`: optional directory for resumable serialized basis data;
- `targetLength`: optional length cutoff for tests;
- `profileName`: optional Magma profiling label;
- `chatty`: optional ASLoc verbosity.

## Relation to the paper

The data are used to support statements about parabolic diagonal cells,
strongly regular cells, subregular \(p\)-cells, and related low-rank checks in
finite Weyl groups.

In the paper, the relevant citation can be something like:

```bibtex
@misc{MRT-cells,
  author = {Miemietz, Vanessa and Roth, Marie and Tubbenhauer, Daniel},
  title = {TBA},
  year = {2026},
  note = {Supplementary low-rank Kazhdan--Lusztig and \(p\)-cell data},
  url = {TBA}
}
```

The repository title and URL should be updated once the final title and GitHub
address are fixed.

## Repository contents

Current intended contents:

```text
README.md
low-rank-cells.pdf
GraphCellsH.m
```

Additional scripts, logs, or source files may be added later.

## Erratum

Empty so far.
