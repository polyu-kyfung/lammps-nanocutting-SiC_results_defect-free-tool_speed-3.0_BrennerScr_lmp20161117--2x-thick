An MD study of the wear of defective tools in the nanometric cutting process with workpiece thickness = 20 units
================================================================================

## Introduction

An MD simulation analysis was conducted to compare the cutting response and the tool wear between flawed and flawless tool surfaces based on a three-layer nanometric cutting model.

---

## Methodology
 
### Materials
 - single diamond tool,	with dimensions 11[100] 11[010] 22[001] in x, y, and z directions, edge radius = 4 x diamond unit cell
 - 3C-SiC workpiece,	with dimensions 65[010] 20[010] 18[001] in x, y, and z directions
 
### Cutting Conditions
 - Depth of cut = 5 x 3C-SiC unit cell length
 - Cutting direction = [010]<-1 0 0> for ≈200 Å
 - Initial temperature = 300 K
 
### Simultion Settings
 1. Equilibration
 - NVT ensemble, timestep = 0.001 ps 	(1 fs) for 24000 steps
 2. Cutting
 - NVT+NVE ensembles, timestep = 0.0005 ps (0.5 fs) for 133000 steps
 
---

## Execution

### Input Template:
 - in.cutsic_eq.lmp
 
 **Potential**
 - EA Scr	=== pair_style	atomistica BrennerScr
 
 **Variables**
 - v		cutting velocity (unit = Å/ps)
 - grooveDepth	Depth of V-shaped groove defect on the diamond flank face (Range: [0-9], unit = length of a diamond unit cell)
 - grooveTan	Angle of V-shaped groove defect on the diamond flank face in tangent (e.g. input 1 for 45 degrees, 0.5 for 26.56(5) degrees)
 
 
### example:
  @Precision > mpirun -np 32 ../../lmp_mpi_20161117_atomistica046 < in.cutsic_eq.lmp -v v 3.0 -v grooveDepth 0 -v grooveTan 1.0
 
## Recommended Books and References
1. [Fung, K. Y., Tang, C. Y., and Cheung, C. F. (2017). Molecular dynamics analysis of the effect of surface flaws of diamond tools on tool wear in nanometric cutting. Computational Materials Science, 133, 60–70.](http://www.sciencedirect.com/science/article/pii/S0927025617301180)
 
