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
 
## Citations and References

- If you utilize the materials in this repository, please cite the following paper:

  [**Fung, K. Y., Tang, C. Y., & Cheung, C. F.** (2017). Molecular dynamics analysis of the effect of surface flaws of diamond tools on tool wear in nanometric cutting. *Computational Materials Science, 133*, 60-70.](https://doi.org/10.1016/j.commatsci.2017.03.006)

- If you work with earlier versions of LAMMPS, please reference:

  [**Plimpton, S.** (1995). Fast Parallel Algorithms for Short-Range Molecular Dynamics. *Journal of Computational Physics, 117*, 1-19.](https://doi.org/10.1006/jcph.1995.1039)

  For further details and citations for later versions of LAMMPS, please refer to the [LAMMPS citation guidelines](https://www.lammps.org/cite.html).

- If you publish results obtained using OVITO, please cite the following software in your publication:

  [**Stukowski, A.** (2010). Visualization and analysis of atomistic simulation data with OVITO - the Open Visualization Tool. *Modelling and Simulation in Materials Science and Engineering, 18*, 015012.](https://doi.org/10.1088/0965-0393/18/1/015012)

  For additional information, please refer to the [OVITO citation guidelines](https://www.ovito.org/#citeOvito).
  
- For the atomic potential utilized in the MD simulations, please reference:

  [**Erhart, P., & Albe, K.** (2005). Analytical potential for atomistic simulations of silicon, carbon, and silicon carbide. *Physical Review B, 71*(3), 035211.](https://doi.org/10.1103/physrevb.71.035211)

  [**Pastewka, L., Klemenz, A., Gumbsch, P., & Moseler, M.** (2013). Screened empirical bond-order potential for Si-C. *Physical Review B, 87*, 205410.](http://dx.doi.org/10.1103/PhysRevB.87.205410)

  [**Pastewka, L., Mrovec, M., Moseler, M., & Gumbsch, P.** (2012). Bond order potentials for fracture, wear, and plasticity. *MRS Bulletin, 37*, 493.](http://dx.doi.org/10.1557/mrs.2012.94)

