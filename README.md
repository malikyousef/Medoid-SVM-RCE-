# Medoid-SVM-RCE

Medoid-SVM-RCE is a feature selection algorithm that builds upon the Recursive Cluster Elimination (RCE) framework. It follows the same algorithmic structure as SVM-RCE-CW, differing only in the cluster representation step. Instead of representing each cluster by its synthetic centroid (mean vector), Medoid-SVM-RCE selects the medoid (the observed gene that best represents the cluster) as the cluster representative. A single Linear SVM is trained simultaneously on the selected medoids, and the absolute values of the estimated SVM coefficients serve as cluster importance scores. This provides an efficient joint scoring strategy while preserving direct correspondence between cluster representatives and observed genes.

# Data Preparation

Gene expression datasets for different types of human complex diseases are required to be downloaded from Gene Expression Omnibus (https://www.ncbi.nlm.nih.gov/geo/) or the GDC Data Portal (https://portal.gdc.cancer.gov/).

Input data must be provided in KNIME .table format with the following structure:

* Rows: Samples / patients

* Columns: Genes / features

* Class label column: Named "class", containing binary labels (pos / neg)

* The link for downloading KNIME: https://www.knime.com/downloads

* For more information about the KNIME platform, please visit https://www.knime.com/software-overview

# The Environment Settings of Medoid-SVM-RCE

After installing KNIME Analytics Platform (version 4.7.6), the Medoid-SVM-RCE workflow is downloaded and imported into KNIME. The workflow contains R scripts and Python scripts therefore the following steps should be followed to prevent errors.

The following KNIME extensions are required:

* KNIME Python Integration
* KNIME Weka Data Mining Integration (3.7)

The following Python libraries are required (Python 3.11.5 via Anaconda):

* scikit-learn 1.3.0
* pandas 2.0.3

Before initiation of the workflow process in KNIME, R / RStudio is required to be run with the following commands:

* library(Rserve)
* Rserve(args = "--vanilla")

Execution of R / RStudio and the workflow simultaneously enables the Medoid-SVM-RCE analysis without retrieving any error.
