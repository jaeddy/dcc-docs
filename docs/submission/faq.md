# Data Submission FAQ

### How do I upload my files to the submission system?

Before using the web-based submission system, you must upload your submission files to the SFTP server. Logging into the web submission system can be accomplished using your existing project SFTP account and password. For more details, visit the [File Submission][1] page.


### Where can I find that latest DCC data file specification?

You can find the latest DCC data file specification and Release notes [here][2].


### How do I put my submission files together?

Submission files must follow the rules in the DCC Data File specification. More details about submission file format can be found [here][3]


### How do I submit information about a simple somatic mutation?

Examples of the format required for mutations can be found [here][4]. Note, this is not a new format and has always been enforced by ICGC.


### Where do I find the Release Notes showing changes between the last DCC data file
specification and the current DCC data file specification?

The latest dictionary Release Notes can be found [here][5]


### What assembly version do you use?

ICGC DCC uses hg19 (GrCh37).


### How do I get the JSON format of the DCC data file specification?

You can access the JSON format of the DCC data specification via REST webservice:

curl -v -XGET  -H "Accept: application/json"

Optional: Format JSON to more readable format:

python -mjson [name of JSON dictionary file downloaded in previous step] > dictionary.mjson

To access the JSON format of the controlled vocabulary tables via REST webservice:

curl -v -XGET  -H "Accept: application/json"


### What do -777 and -888 mean? How do I use them?

-777 and -888 are reserve codes accepted by ICGC for data elements where the data is verified to be unknown, or the information is not applicable. Details and examples can be found [here][6]


### I got an error message during validation that I don't understand! How do I get more details?

Once validation is complete, you will be able to view a report generated by the submission system which gives details about errors. In addition, please refer to the "Additional Notes" section of the data file specification tables for each data type, which explain cross-field restrictions. If you encounter an error message you do not understand, please contact [dcc-support@icgc.org][7].


### I can't log into the submission system. I think I forgot my username/password. How do I retrieve it?

The submission system will lock a user out if a password is entered incorrectly three times. Should you find yourself locked out, or if you have forgotten your password, please contact [dcc-support@icgc.org][7] and we will reset it.


### How do I obtain the accession number required for the "raw_data_accession" field?

When you submit your raw sequencing data to EGA's EBI repository, EGA will supply you with an accession number. You will need to use this accession number to populate the _raw_data_accession_ field in the submission files.

### Why do I have to submit my raw data to EBI's EGA repository before submitting data to ICGC DCC?

ICGC member projects are required by ICGC policies to submit their raw sequencing reads, and other primary data, to controlled access public repositories. The official ICGC DCC-supported repository for [ICGC sequencing reads][8] is the European Bioinformatics Institute's (EBI) [European Genome-phenome Archive (EGA)][9].


### What does open and controlled access mean?

Open access refers to all data that is publicly available in the portal without restrictions. Controlled access refers to protected data, such as germline SNPs, that requires user certification for access. For more information on how to access controlled tier data in the ICGC Data Portal and data deposited to the EGA, please contact [DACO][10].


### What language are the cross-field validation scripts written in?

The cross-field validation scripts are implemented in [MVEL][11]


### Can I submit just clinical data without experimental data to ICGC?

Please be advised that donors, specimen, and analyzed_samples with no associated experimental results will be ignored and not reported DCC Data Portal release.


### What are "percentage_of_cellularity" and "level_of_cellularity" fields in the Specimen and Analyzed Sample Data File data file specifications? Do I need to fill both in?

Cellularity is defined as the proportion of tumour nuclei to total number of nuclei in a given specimen or analyzed sample. The cellularity at the specimen level (ie. pathologist reported) could be different from the cellularity reported at the sample level (ie. using sequencing methods such as cell sorting). The two fields "percentage_of_cellularity" and "level_of_cellularity" record the same piece of information, but give the submitter the option to submit the information as either an integer value (percentage_of_cellularity) or a range of percentages (level_of_cellularity). An example would be in the case where a pathologist can only specify the cellularity of a specimen to be within a certain range (40-50% for example), then the "level_of_cellularity" data element could be populated with "3" (which defines 41-60% in the controlled vocabulary table), and "percentage_of_cellularity" could be populated with "-888" (not applicable).

[1]: guide/overview/file-submission.md
[2]: /dictionary/release-20.md
[3]: guide/overview/submission-file-format.md
[4]: guide/icgc-simple-somatic-mutation-format.md
[5]: /dictionary/releases.md
[6]: guide/dcc-data-element-specifications.md#missing-or-unknown-values
[7]: mailto:dcc-support@icgc.org
[8]: http://www.ebi.ac.uk/ega/dacs/EGAC00001000010
[9]: http://www.ebi.ac.uk/ega
[10]: http://www.icgc.org/daco
[11]: http://mvel.codehaus.org/Language+Guide+for+2.0