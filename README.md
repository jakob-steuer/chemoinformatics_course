# chemoinformatics_2025

Exercises for the course "Chemoinformatics" (WS 2025) at the FHNW.

## How to Run the Notebooks

You can run each set of exercises in your browser using Google Colab.

(Note: a Google account is required)

Click the links below to open a notebook directly from this GitHub repository into Colab.

[**Exercise 1: Chemical Space**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_1_chemical_space.ipynb)

[**Exercise 2: Molecular Graphs**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_2_molecular_graphs.ipynb)

[**Exercise 3: SMILES**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_3_smiles.ipynb)

[**Exercise 4: Chemical Databases**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_4_chemical_databases.ipynb)

[**Exercise 5: Molecular Dynamics Simulation Analysis**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_5_MD_simulation_analysis.ipynb)

[**Exercise 6: Pharmacophores**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_6_pharmacophores.ipynb)

[**Exercise 7: QSAR**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_7_qsar.ipynb)

[**Exercise 8: Appendix — NLP Based Information Extraction**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_8_appendix_nlp.ipynb)

[**Exercise 9: Docking**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_9_docking_analysis.ipynb)

[**Exercise 9b: Cofolding (optional)**](https://colab.research.google.com/github/jakob-steuer/chemoinformatics_course/blob/main/chemoinformatics_9b_cofolding.ipynb)

Exercise 9 reads the results of your own SwissDock jobs. If they are not back in time it falls
back automatically to the worked EGFR set in [`docking_example/`](docking_example/), so the
notebook runs either way.

Exercise 9b predicts the same complex from sequence alone, with no structure and no search box,
and packages the result for exercise 9 to read. It needs a **T4 GPU** runtime
(Runtime → Change runtime type) and takes about ten minutes. It is entirely optional — exercise 9
uses a prepared cofolding example if you skip it.

The prediction is a tight fit in a T4's memory, so the notebook's `LOW_MEMORY` setting is on by
default. If it still reports that it ran out of memory, a T4 is not enough for that run — use a
larger GPU runtime if you have one, or just skip ahead, since exercise 9 has the result prepared.
