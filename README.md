# phonopy-abacus
ABACUS &amp; phonopy calculation

## Prerequisite
Following packages needs to be installed first:
- [ABACUS](https://github.com/abacusmodeling/abacus-develop/releases)
- [Phonopy](https://phonopy.github.io/phonopy/index.html)

## Installation
1. Move 'abacus.py' to '~/phonopy/interface'
2. Add ABACUS-related codes in the '~/phonopy/interface/calculator.py' as 'calculator.py' we provided

## Usage
1. Prepare a 'setting.conf' with following tags:
```
DIM = 2 2 3         #  when three integers are specified, a supercell elongated along axes of unit cell is created
ATOM_NAME = C N     #  specify chemical symbols.
```
2. To obtain supercells ($2\times 2\times 3$) with displacements, run phonopy:
```
phonopy setting.conf --abacus -d
```
3. Calculate forces on atoms in the supercells with displacements. For each SCF calculation, you should specify `stru_file` with `STRU-{number}` and `out_force=1`. Be careful not to relax the structures
4. Then create FORCE_SETS file using ABACUS inteface:
```
phonopy -f ./disp-{number}/OUT*/running*.log
```
