# A geometric shape regularity effect in the human brain: fMRI dataset

Authors:

* Mathias Sablé-Meyer
* Lucas Benjamin
* Cassandra Potier Watkins
* Chenxi He
* Maxence Pajot
* Théo Morfoisse
* Fosca Al Roumi
* Stanislas Dehaene

## Abstract

The perception and production of regular geometric shapes is a characteristic trait of human cultures since prehistory, whose neural mechanisms are unknown. Behavioral studies suggest that humans are attuned to discrete regularities such as symmetries and parallelism, and rely on their combinations to encode regular geometric shapes in a compressed form. To identify the relevant brain systems and their dynamics, we collected functional MRI and magnetoencephalography data in both adults and six-year-olds during the perception of simple shapes such as hexagons, triangles and quadrilaterals. The results revealed that geometric shapes, relative to other visual categories, induce a hypoactivation of ventral visual areas and an overactivation of the intraparietal and inferior temporal regions also involved in mathematical processing, whose activation is modulated by geometric regularity. While convolutional neural networks captured the early visual activity evoked by geometric shapes, they failed to account for subsequent dorsal parietal and prefrontal signals, which could only be captured by discrete geometric features or by more advanced transformer models of vision. We propose that the perception of abstract geometric regularities engages an additional symbolic mode of visual perception.

## Notes about this dataset

We separately share the MEG dataset at [UPDATE](UPDATE). Below are some notes about the
fMRI dataset of N=20 adult participants (`sub-2xx`, numbers between 204 and
223), and N=22 children (`sub-3xx`, numbers between 301 and 325).

* The code for the analyses associated to
  [https://doi.org/10.1101/2024.03.13.584141](https://doi.org/10.1101/2024.03.13.584141)
  are provided at
  [https://github.com/mathias-sm/AGeometricShapeRegularityEffectHumanBrain](https://github.com/mathias-sm/AGeometricShapeRegularityEffectHumanBrain)

  However, the analyses work from already preprocessed data. Since there is no
  custom code per se for the preprocessing, I have not included it in the
  repository. To preprocess the data as was done in the published article, here
  is the command and software information:
    * fMRIPrep version: `20.0.5`
    * fMRIPrep command: `/usr/local/miniconda/bin/fmriprep /data /out participant --participant-label <label> --output-spaces MNI152NLin6Asym:res-2 MNI152NLin2009cAsym:res-2`
* Defacing has been performed with `bidsonym` running the `pydeface` masking,
  and `nobrainer` brain registraction pipeline.

  The published analyses have been performed on the non-defaced data. I have
  checked for data quality on all participants after defacing. In specific
  cases, I may be able to request the permission to share the original,
  non-defaced dataset.
* `sub-325` was acquired by a different experimenter and defaced *before* being
  shared with the rest of the research team, hence why the slightly different
  defacing mask. That participant was also preprocessed separately, and using a
  more recent fMRIPrep version: `20.2.6`.
* The data associated with the children has a few missing files. Notably:
    1. `sub-313` and `sub-316` are missing one run of the localizer each
    2. `sub-316` has no data at all for the geometry
    3. `sub-308` has eno useable data for the intruder task

  Since all of these still have some data to contribute to either task, all
  available files were kept on this dataset. The analysis code reflects these
  inconsistencies where required with specific exceptions.
