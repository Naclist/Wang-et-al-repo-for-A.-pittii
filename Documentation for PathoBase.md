# PathoBase
PathoBase is an open bioinformatics platform for storing, analyzing, and processing microbial pathogen genomes. The database provides comprehensive genomic analysis capabilities, including distributed core genome Multi-Locus Sequence Typing (dcgMLST) [^ref1], automated genome annotation, and advanced plasmid prediction algorithms.

## Quick Start
PathoBase was developed based on the open-source framework of [EnteroBase](https://enterobase.warwick.ac.uk/)[^ref2], and is currently maintained by Professor Zhemin Zhou's research group at Soochow University. As a web-based centralized database, PathoBase is optimized for use with [Google Chrome](https://www.google.com/chrome/) and maintains similar interface logic to EnteroBase, making it immediately familiar to users of that platform.
The PathoBase homepage displays the available bacterial databases—currently featuring *Acinetobacter pittii*, *Acinetobacter baumannii*, and *Staphylococcus aureus*—along with real-time statistics on genome counts for each pathogen. Users can access species-specific genomic information by selecting any of these databases. While limited browsing is available to guest users, full functionality—including genome assembly downloads and GrapeTree visualizations—requires registration and authentication.

### Account Registration

For potential use of Reviewers, we offered a DEMO administrator account:

Account: `zhemin`
Password: `Soochow`

To register for PathoBase:

1.	Click the Register button in the upper-right corner of the homepage
2.	Complete all required fields in the registration form, including username, password, email address, and institutional affiliation
3.	Submit the form by clicking Register
4.	Check your email for a verification message containing an activation link
5.	Follow the verification link to activate your account and gain access to PathoBase

![image](https://github.com/user-attachments/assets/d28e4bf3-50a0-4b5b-a637-40bce7ecba2f)
 
### Logging In
Users with existing accounts can authenticate by:

1.	Clicking the Log In button
2.	Entering their username and password credentials
3.	Selecting the "Remember me" option (optional) for persistent sessions

First-time users will receive a brief tutorial introducing key features, though experienced users may choose to explore the database structure, analysis workflows, and the dcgMLST + HierCC (Hierarchical Clustering of cgMLST) [^ref3] algorithm independently.

![image](https://github.com/user-attachments/assets/5cf606d9-a1bf-4bbf-9e25-f4817397156d)


## Tutorial: Analyzing Bacterial Strains
PathoBase excels in genomic data storage and strain classification through its dcgMLST + HierCC implementation, which efficiently identifies epidemiological relationships between bacterial isolates. The following tutorial demonstrates core functionalities using real data examples. 

Case Study: *Acinetobacter pittii* Analysis
### Genome Upload Process
After authentication and selection of your target pathogen database, follow these steps to upload genomic data:

1.	Select Upload Reads from the left navigation panel

![image](https://github.com/user-attachments/assets/f649be26-d52d-464c-9b60-8ff0b8678316)

2.	Complete the metadata entry form with essential epidemiological information
   * Isolation date, geographic origin, and clinical context are particularly valuable for epidemiological tracking
   * Comprehensive metadata enhances the utility of your contribution for other researchers

![image](https://github.com/user-attachments/assets/265ebb70-bac6-49dc-a78c-e5920f03e202)

![image](https://github.com/user-attachments/assets/a674a61e-0895-4289-8f22-29695db26560)

![image](https://github.com/user-attachments/assets/7b1509b9-bfdf-4ea4-84df-3f20e79227c0)

By default, PathoBase accepts only raw sequencing reads rather than pre-assembled genomes to ensure analytical consistency and minimize methodological variability. However, users with verified credentials (**"Trusted Users"**) may upload pre-assembled genomes in exceptional circumstances.

After completing the metadata form:
1.	Navigate to the Upload Data tab
2.	Select the directory containing your sequencing files
3.	Initiate the upload process by clicking Upload
4.	Monitor processing status through the Job List section
5.	Access detailed progress information by selecting the associated task ID

![image](https://github.com/user-attachments/assets/ce0a5e2b-decd-4c7b-bf55-01e4860043d8)

Once analysis is complete, your genome will be integrated into the PathoBase repository and annotated with appropriate metadata and typing information. To view all genomes within a species database, navigate to the database page and select Search Strains > All Strains from the navigation menu.

![image](https://github.com/user-attachments/assets/87f6cc00-0638-4937-b880-d2d73b050a99)

![image](https://github.com/user-attachments/assets/7048af4c-4764-4f6b-af99-e66ca9e4c59d)

### Comparative Genomic Analysis
The A. pittii repository contains 726 reference genomes collected over 33 years from 30 countries, representing 148 distinct HC1100 types (high-resolution hierarchical clusters) from our comprehensive cgMLST study (see Supplementary Data 1 for details).

![image](https://github.com/user-attachments/assets/8bc72dce-cc50-4c01-996e-4b0d55a734b7)

To identify related strains:
1.	Return to Search Strains and apply filters matching your genome's metadata
2.	Note the population assignments generated by the cgMLST + HierCC analysis
3.	For A. pittii, two hierarchical clustering thresholds are defined: HC450 and HC1100
4.	HC1100 provides higher resolution and is recommended for initial analysis

![image](https://github.com/user-attachments/assets/9954be40-cf5b-4321-8067-e93bdf076a41)

![image](https://github.com/user-attachments/assets/0bc3941c-6b17-4bc6-bb2c-c988bec6b600)

Each genome receives a unique integer HC1100 identifier. To retrieve evolutionarily related genomes:
1.	Reapply the Search Strains filter
2.	Select the Experimental Data tab
3.	Filter by your strain's HC1100 value to identify closely related isolates

This approach rapidly identifies genetically similar strains that may share epidemiological connections, enabling efficient outbreak investigation and evolutionary analysis.

### Visualization
You can use multiple algorithms provided by PathoBase to rapidly construct **cgMLST-based phylogenetic trees** for strains with assigned HC identifiers, which can then be visualized via **GrapeTree**. The figure below shows the initial interface for building a cgMLST tree using all currently displayed strain genomes:

![image](https://github.com/user-attachments/assets/146ccd87-55a0-4910-89ad-7bd5506f249b)

![image](https://github.com/user-attachments/assets/832649b8-5b55-44de-9e3d-e3e271b4630a)

For the genomes in this tutorial, we recommend generating a **minimum spanning tree** using **RapidNJ**. Click **Submit** to queue the tree-building task for background analysis. If successful, a pop-up window will appear in your browser. After a brief wait, you will see the GrapeTree visualization results as shown in the figure below:  

![image](https://github.com/user-attachments/assets/3805f282-4260-4189-a994-c331ba07952c)

At this stage, you cannot directly group genome nodes based on **Experimental Data** (e.g., HC1100 assignments). To import HC1100 data:  
1. Click **Import fields** in the visualization interface.  
2. Select **Experiment** from the dropdown menu.  
3. Choose **HC1100** (or other fields of interest) to load hierarchical cluster assignments from the database.

![image](https://github.com/user-attachments/assets/b67ae74c-ac99-443b-8c11-e160493bab72)

![image](https://github.com/user-attachments/assets/8502eafc-e94b-4ab3-b54a-99d51a8c1e70)

![image](https://github.com/user-attachments/assets/557bd68d-fbf5-4c16-b652-13e2d79479db)



## References
[^ref1]: https://doi.org/10.1038/s41467-023-43528-0
[^ref2]: https://doi.org/10.1093/nar/gkae902
[^ref3]: https://doi.org/10.1093/bioinformatics/btab234
