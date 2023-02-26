# Overview

## Table of Contents
* [KAPE](#kape) 
* [This Project](#this-project)
* [Group Memebers](#group-members)

## KAPE

### General Information

KAPE (Kroll Artifact Parser and Extractor) is an open source tool created by Eric Zimmerman. The tool is designed to automate forensic evidence extraction and analysis. On its own, the tool does not do anything besides extract files/folders and tie together multiple different tools for analysis. An analogy that is often given with KAPE is that KAPE is a car: you provide the gas and directions, the car just helps you get there faster. KAPE is primarily used with Windows machines.

### Targets

Targets are how KAPE knows which data to extract. In essence, a target tells KAPE exactly where to find forensic artifacts. If a file name or path deviates any amount from what the KAPE target expects, KAPE will fail to find the artifact and will not retrieve the expected evidence. Properly configured targets are essential to effective KAPE evidence collection.

### Modules

Whereas KAPE targets extract evidence from a forensic image, KAPE modules perform analysis on the extracted evidence. KAPE does not do any analysis itself. All that a KAPE module does is take a separate tool (KAPE modules must point to this tool) and run it against specific forms of evidence. When used properly, KAPE can run extraction using various targets and then automatically analyze the obtained evidence by pointing modules to existing tools. This makes forensic work significantly faster, especially when performing a triage analysis. 

### KAPE References

* [KAPE Download Page](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape)
* [SANS KAPE Page](https://www.sans.org/tools/kape/)
* [KAPE GitHub](https://github.com/EricZimmerman/KapeFiles)

## This Project

### Temp Files

When malware runs on a machine, it will often take advantage of directories that are easy to access and enable some level of hiding. Temp folders are the perfect location for this. Temp folders are often easy to write to, and they are also generally full of a random assortment of files. Because of this, pulling files from temp folders on a live system may often obtain crucial evidence. This could be used, for example, when attempting to determine how many computers have been infected with a particular variety of malware. If that malware is known to write to the temp folder, pulling temp folders from many different computers and searching for indicators of compromise may help to quickly determine the scope of the infection.

### KAPE Target

KAPE provides a perfect solution to use for this purpose. KAPE can be deployed across multiple live systems, and it can pull every file inside of specific folders. Currently, however, KAPE does not have a target that is dedicated to pulling these temp folders. This project seeks to correct that by creating a KAPE target that is able to pull these folders with all of their content. The target specifically focuses on the following three folders:

* `C:\Windows\Temp`: this folder is the Windows default temporary folder. Many applications store information here, especially when they run with higher privileges.
* `C:\Users\<user profile>\AppData\Local\Temp`: this folder is the default temporary folder for each user profile. Many applications store information here when run from a user context.
* `C:\Temp`: while nonstandard, this is a very common location for system administrators or software to create a 'temporary' folder. Unlike the other two folders, Windows does not standardize this folder. It is often a standard folder, but it is still common.

## Group Members

The following are part of the group that is responsible for this project:
* Daniel Smith
* Garrett Morgan
* Jordan Johnson
* Conner Tracy
* Robert Smith
* Daniel Taylor