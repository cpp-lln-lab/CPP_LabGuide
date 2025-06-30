# Code and data arrangement

## Version control

In the lab we (try) to stick to version control for code with git/github and data with datalad and gin. Somewhere else is already mentioned but repetita iuvant so 

1. Install git on your computer 
2. Create a GITHUB account and ask to be added to the (lab organization)[https://github.com/cpp-lln-lab]
3. Make sure you have your SSH key for GITHUB following this tutorial 
4. Have a look at this doc to have a first idea on how to contribute on github
5. Have a look around cause we already have a lot of ready to use code ;)
6. Make sure you are set up with the following tools having a look at this doc’s first section
    1. Datalad (in a nutshell git for data but checkout more here https://handbook.datalad.org/en/latest/)
    2. Gin (host server for data, good for “unlimited” and free cloud back and private and public data sharing)
7. Ask to be added to the Gin organization of the lab to start storing your data there

## Data management
for MRI data the lab is moving towards using the BIDS data structure

* bids starter kit
* bids specification

### Official GIN/DATALAD CPP dataset organization 


[WIP] Checklist to make an official “raw” repo (bids, bids-validator checked, standard CPP data organization (eg group naming, task naming, readme with link to published/preprint, etc)) 

[WIP - Just dropping useful links here for now]

Data:

[GIN organization](https://gin.g-node.org/cpp-lln-lab) for source, raw, and preprocessed data for conversion control and sharing

Dataset summary that puts together all the bidsified raw and derivatives repos of the lab and summarizes metadata in a table from the GIN repo above: 

- [website with summary table](https://cpp-lln-lab.github.io/CPP_Datasets/index.html)
- [Githuba repo CPP_Datasets](https://github.com/cpp-lln-lab/CPP_Datasets)

Datalad superdataset to grab all the repo together (these are submodules in the [Githuba repo CPP_Datasets](https://github.com/cpp-lln-lab/CPP_Datasets):

- https://github.com/cpp-lln-lab/cpp-lln-lab_derivatives 
- https://github.com/cpp-lln-lab/cpp-lln-lab_source

Guidelines to maintain the CPP dataset https://github.com/cpp-lln-lab/dataset_maintenance


Tools:

- https://github.com/cpp-lln-lab/template_datalad_bids-raw
- https://github.com/cpp-lln-lab/CPP_dcm2Bids
- https://github.com/cpp-lln-lab/letswave_bids_import
- https://github.com/cpp-lln-lab/eeg_bids_conversion



## Other back ups


### IONS cloud storage

For more information, see the [SSS / IONS official intranet page](http://sss-intranet.icp.ucl.ac.be/wiki/index.php/Storage_access#Groups)

Cooked step by step for MacOS users:

(If not connected in UCLouvain, first connect with VPN)
1. Open Finder
2. Go menu
3. Element Connect to server
4. Add address smb://sss-samba.icp.ucl.ac.be/cosy-oc 
5. Use your UCLouvain credentials when asked
6. Add the opened folder as a favorite (top of the right panel)


Short guidelines (how to use this space):

- not suitable for an “online” usage (eg running analyses within the folder), it is a cloud service so reading and writing is as fast as your internet connection
- Long term storage
- Please, be organized. Imagine that another person in the future will open that folder and make sense of the content in less than 2 minutes
- Add README files to help the future user understand what’s inside that folder (e.g. dicoms from the study XXX published in XXX code for conversion/analyses here github.com/xxx, copy of this dataset is also on gin.g-node.org/xxx)
- What NOT to put there? Should not become a data dump so not just a new space where a user can free up her/his hard disk

It is possible to ask/send data with not UCLouvain collaborators by setting up an SFTP access, see [here](https://sss-intranet.icp.ucl.ac.be/wiki/index.php/File_transfer#Transferring_large_files_between_SSS_and_the_outside)


## Get organised

### Code style guides


matlab
https://www.mathworks.com/matlabcentral/fileexchange/46056-matlab-style-guidelines-2-0

### Useful links

A quick thread on how to organize your scripts:
https://twitter.com/wmvanvliet/status/1240907591791886337
