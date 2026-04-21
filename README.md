# GNPS2 to SNAP-MS Bridge
Welcome to the GNPS2 to SNAP-MS Bridge repository! This tool acts as a bridge between GNPS2 output and SNAP-MS. It modifies a GNPS2 .graphml file by mapping its attributes to the GNPS1 format required by SNAP-MS.

## 🌐 Live Application
You can try the application directly online without any local installation:
[GNPS2 to SNAP-MS Bridge on shinyapps.io](https://5bptzm-alan-hernandez.shinyapps.io/GNPS2_to_SNAP-MS/)

## 🧬 What it Does
SNAP-MS expects specific node and edge attributes that are formatted differently in GNPS2. This R Shiny application automates the conversion process. Specifically, the script (app.R) performs the following data mappings and network corrections:

* Identifiers: Maps the GNPS2 id attribute to the cluster index.
* Mass & Retention Time: Converts mz to both parent mass and precursor mass. It also converts rt to RTMean and RTConsensus.
* Library Annotations: Maps library_compound_name to Compound_Name (assigning "N/A" if missing), library_SMILES to Smiles, and library_InChI to INCHI.
* Cosmetic Attributes: Injects required metadata for SNAP-MS compatibility, including setting sum(precursor intensity) to 100.0 and NODE_TYPE to "Feature Node".
* Edge Data: Updates edge attributes by mapping score to cosine_score and EdgeScore, and maps deltamz to mass_difference.
* Network Topology: Recalculates network components (clusters) and appropriately flags singletons (nodes with a degree of 0) with a component index of -1.

## 💻 Running Locally
If you prefer to run this application on your local machine, you will need R installed along with the following packages:
* shiny
* *igraph

Simply clone this repository and run the app. The server logic is configured to handle large .graphml files up to 500 MB. Once processing is complete, the app provides a convenient download button for the fixed GraphML file.

## 🧑‍🔬 About & Contact
This project was developed by Alan Hernandez. The application is proudly associated with the Microbial Natural Products Research Lab. 125, School of Chemistry, UNAM.

If you encounter any issues or want to report a bug, please reach out via email: f9.alan@gmail.com.

## 📄 License
This project is licensed under the MIT License - Copyright (c) 2026 Alan Hernandez.
