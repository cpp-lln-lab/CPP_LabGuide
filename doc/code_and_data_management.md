# Code and data management

Lab phylosophy: do not lose track of code and data aka use version control (git/github, datalad, etc.) and universal data format (BIDS).

CPP member to ask for help: Marco Barilari

## Version contro tools on a "daily" basis

### Code aka git/github

1. [Install git](https://git-scm.com/downloads).
2. Create a Github account and ask to be added to the [CPP-lln-lab organization](https://github.com/cpp-lln-lab).

!!! TIP
    **Github account name**

    Better to chose a full name account name 'davidbowie' than a nickname 'ziggysturdust', collegues and and other researchers or your future supervisor that might be interested in your code will have a hard time to find you while using your cool nickname.

3. Make sure you have your SSH key for GITHUB following this [tutorial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
4. Have a look at this doc to have a first idea on how to contribute on [github](https://github.com/cpp-lln-lab/.github).
5. Have a look around cause we already have a lot of ready-to-use code [here in the CPP github organization](https://github.com/cpp-lln-lab) and [here where we store "not-so-organized" cod in the CPP brewery](https://github.com/cpp-lln-lab/CPP_brewery) ;)

### Data aka Datalad and G-node GIN

1. [Install Datalad](https://handbook.datalad.org/en/latest/intro/installation.html): in a nutshell it is "git for data", checkout more at the offical [datalad handbook](https://handbook.datalad.org/en/latest/).
2. Create an account on [G-node GIN](https://gin.g-node.org/): GIN is a host server for Neuro Imaging data, good for “unlimited” and free cloud back-up and private and public data sharing.
3. Ask to be added to the [GIN CPP organization](https://gin.g-node.org/cpp-lln-lab) and the [GIN CPP Brewery](https://gin.g-node.org/cpp_brewery) of the lab to start storing your data there.
4. Check this [datalat crush course by the CPP lab](https://github.com/cpp-lln-lab/datalad_crash_course)

## Data storage ("daily" use) and long standing back ups

Since it is important to not lose our important data, it is advised to have several back-ups stored in different places.

### Brain Imaging Data Structure - BIDS

For MRI, EEG, etc. data, the lab is (moving towards) using the BIDS data structure. For more information check the [bids specification](https://bids-specification.readthedocs.io/en/stable/).

Here below some in-house tools in Github repos that helped us to convert the data into BIDS format and maintain them:

Tools/Repos:

- [template_datalad_bids-raw](https://github.com/cpp-lln-lab/template_datalad_bids-raw)
- [CPP_dcm2Bids](https://github.com/cpp-lln-lab/CPP_dcm2Bids)
- [letswave_bids_import](https://github.com/cpp-lln-lab/letswave_bids_import)
- [eeg_bids_conversion](https://github.com/cpp-lln-lab/eeg_bids_conversion)

[WIP] Checklist to make an official “CPP BIDS raw” repo using BIDS:

- bids-validator checked
- standard CPP data organization (eg group naming, task naming, readme with link to published/preprint, etc)
- add source data eg dicoms and code to convert them
- add stimulation code used while colleting data (eg task eeg and fmri)
- add pdf of the pdf for MRI sequence

### Datalad/Gin/Github CPP dataset organization

Data:

[CPP GIN organization](https://gin.g-node.org/cpp-lln-lab) for source, raw, and preprocessed data for version control and sharing. Repos could be public or private.
[CPP brewerey](https://gin.g-node.org/cpp_brewery) for data not ready to be officially distributed (like sandbox repos or data still under processing)

Dataset summary that puts together all the bidsified raw and derivatives repos of the lab and summarizes metadata in a table from the GIN repo above: 

- [website with summary table](https://cpp-lln-lab.github.io/CPP_Datasets/index.html)
- [Githuba repo CPP_Datasets](https://github.com/cpp-lln-lab/CPP_Datasets)

Github/Datalad superdataset to grab all the repo together. These repos are submodules in the [Githuba repo CPP_Datasets](https://github.com/cpp-lln-lab/CPP_Datasets):

- [cpp-lln-lab_derivatives](https://github.com/cpp-lln-lab/cpp-lln-lab_derivatives)
- [cpp-lln-lab_source](https://github.com/cpp-lln-lab/cpp-lln-lab_source)

Guidelines to maintain the CPP dataset at [dataset_maintenance](https://github.com/cpp-lln-lab/dataset_maintenance)

#### Sharing data to collaborators external to the CPP lab via GIN

For the CPP member in charge to share the data

1. Share the link to this guidline [URL to be added one this page is rendered].
2. Once received the GIN account, add this person to the specific repo to be shared. Open the repo, Settings > Collaboration > Add the user name to the empty space and click on "Add New Collaborato". (Note to self: check if it works/is possible to add only for read mode.)
3. Inform about this so that the external collaborato can now download the data.

For the external collaborator (copied from above):

1. [Install Datalad](https://handbook.datalad.org/en/latest/intro/installation.html): in a nutshell it is "git for data", checkout more at the offical [datalad handbook](https://handbook.datalad.org/en/latest/).
2. Create an account on [G-node GIN](https://gin.g-node.org/): GIN is a host server for Neuro Imaging data, good for “unlimited” and free cloud back-up and private and public data sharing.
3. Share your gin account to the person in charge to share the data with you and ask to be added as a "collaborator" to the specific repos you want to be share with you
4. Use datalad to get the data, use this script below by changing paths and URL (use ssh URL starting with `git@gin.g-node.org:/cpp-lln-lab/`):

```bash
folder_for_installation=

# mind that this should be the ssh url since the repo is private so it should start with git@gin.g-node.org:/cpp-lln-lab/name-of-the-dataset
repo_url= 

mkdir -p $folder_for_installation

cd $folder_for_installation

# install the repo
datalad install -r $repo_url

cd $name-of-the-data-folder

# Download all the data
datalad get . -J 2

# OR download only the anatomical data (assuming there is no session folder)
datalad get */anat -J 2

# OR downlaod only the fmri data for a specific task (e.g. 'rest') and the antomical (assuming there is no session folder)
datalad get */func/*rest* get */anat -J 2
```

5. In case you want to go out of the datalad "environment" (read: avoid headaches with locked/not writeable/linked files/etc), after download copy the files out of the datalad folder and use the data as sandard files

This will copy the actual files, in case you downloade only part of the data you will see that the whole dataset has been cleaned but the not downloade files are "empty". Just manually clean them.

```bash
fodler_datalad=

folder_no_datalad=

mkdir -p $folder_no_datalad

cd $fodler_datalad

# copy the datalad fodler content one by one, we do not copy the whole fodler at once cause there are hidden git folder that we do not want
cp -L -vr sub* $folder_no_datalad
cp -L -v *.tsv $folder_no_datalad
cp -L -v *.md $folder_no_datalad
cp -L -v *.json $folder_no_datalad

chmod -R 755 $folder_no_datalad
```

### IONS cloud storage

Make sure to be connected to the UCLouvain network, if uot side the office first connect with the VPN.

Short guidelines:

- not suitable for an “online” usage (eg running analyses within the folder), it is a cloud service so reading and writing is as fast as your internet connection
- Long term storage
- Please, be organized. Imagine that another person in the future will open that folder and make sense of the content in less than 2 minutes
- Add README files to help the future user understand what’s inside that folder (e.g. dicoms from the study XXX published in XXX code for conversion/analyses here github.com/xxx, copy of this dataset is also on gin.g-node.org/xxx)
- What NOT to put there? Should not become a data dump so not just a new space where a user can free up her/his hard disk

Chek the [SSS server wiki](http://sss-intranet.icp.ucl.ac.be/wiki/index.php/Storage_access#Groups)

Here below, the cooked step by step process for MacOS users to connet to the CPP server folder:

1. Open Finder
2. Go menu
3. Element Connect to server
4. Add address smb://sss-samba.icp.ucl.ac.be/cosy-oc
5. Use your UCLouvain credentials when asked
6. Add the opened folder as a favorite (top of the right panel).

#### Sharing/receivereceive data to/from collaborators external to the CPP lab via SSS/IONS server

[WIP]
