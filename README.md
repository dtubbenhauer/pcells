# pcells

Magma scripts for computing p-cells in finite Coxeter groups using ASLoc/IHecke.

## Main script

`GraphCellsH.m` computes the p-canonical basis for a finite Coxeter group and prints the two-sided p-cells as matrices of intersection sizes

```text
|R_i ∩ L_j|
```

It also prints multiplication tables in the p-canonical basis for the diagonal H-cells.

## Requirements

- Magma
- ASLoc, with `ASLoc.spec` visible from the working directory
- IHecke available through ASLoc

## Examples

Create a save directory once:

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

Arguments:

- `type`: Cartan type, for example `G2`, `F4`, `E6`
- `char`: characteristic, either `0` or a prime
- `saveDir`: optional directory for resumable serialized basis data
- `targetLength`: optional length cutoff for tests
- `profileName`: optional Magma profiling label
- `chatty`: optional ASLoc verbosity

## Notes

The script is designed for finite Coxeter groups. For large types the full cell computation can be expensive; use specialized subregular scripts when only the ordinary subregular cell is needed.
