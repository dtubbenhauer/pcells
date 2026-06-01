# TBA

This repository contains supplementary material for the project currently titled

> TBA

At the moment, the main file is a compiled note collecting low-rank
Kazhdan--Lusztig cell data for finite Coxeter groups.

## Contact

If you find an error in the data, please email:

[daniel.tubbenhauer@sydney.edu.au](mailto:daniel.tubbenhauer@sydney.edu.au)

Same goes for errors related to this repository.

## Main file

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

The purpose of the file is to make the low-rank cell computations transparent
and easy to cite. In particular, it records which strongly regular cells contain
longest elements of standard parabolic subgroups.

## Relation to the paper

The data are used to support statements about parabolic diagonal cells and
strongly regular cells in finite Weyl groups.

In the paper, the relevant citation can be something like:

```bibtex
@misc{MRT-cells,
  author = {Miemietz, Vanessa and Roth, Marie and Tubbenhauer, Daniel},
  title = {TBA},
  year = {2026},
  note = {Supplementary low-rank Kazhdan--Lusztig cell data},
  url = {TBA}
}
```

The repository title and URL should be updated once the final title and GitHub
address are fixed.

## Reproducibility

The computations use standard finite Coxeter group and Hecke algebra tools.
Some of the underlying checks were performed using GAP3/CHEVIE and Magma-based
code for cells and \(p\)-cells.

For the specific purpose of the PDF, the important reproducibility check is:

\[
    \sum_J p(J)=2^{\operatorname{rk}(W)},
\]

since each subset \(I\subseteq S\) gives exactly one parabolic longest element
\(w_I\).

## Files

Current repository contents:

```text
low-rank-cells.pdf
README.md
```

More scripts or source files may be added later.

## Erratum

Empty so far.
