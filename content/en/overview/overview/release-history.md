---
title: "Release History"
linkTitle: "Release History"
weight: 7
aliases:
- /docs/Neurodesktop/release-history
- /docs/support/release-history
description: >-
     Previous releases of Neurodesktop. 
---

Latest Version
: {{< params/neurodesktop/jupyter_neurodesk_version >}}

Please consult [this page](https://github.com/NeuroDesk/neurodesk.github.io/blob/main/.github/content-templates/release-history-template.md) for the template for new releases.

## 2025-06-10
### New Features
- upgrade to jupyterhub 5.3.0
- added nbgitpuller, tcsh
- added neurodesk copilot: https://neurodesk.org/developers/neurodesk-copilot/
- added qsirecon
### Improvements
- updated niivue (with breaking interface change!)
- updated jupyter-lmod (with breaking interface change!)
- moved cvmfs cache to home directory
- updated background to new Neurodesk logo
- updated ants to 2.6.0
### Bug Fixes
- split cvmfs in 3 different regions


## 2025-04-08
### New Features
- Added [dcm2bids](https://github.com/UNFmontreal/Dcm2Bids) support
- Integrated [QSMxT](https://qsmxt.github.io/QSMxT/) v8.0.2
### Improvements
- Replaced [BIDScoin](https://bidscoin.readthedocs.io/en/latest/) 4.6.0 with 4.6.1 to fix GUI bug
- Updated [qsiprep](https://qsiprep.readthedocs.io/) to 1.0.1
### Bug Fixes
- Improved internet test by using DNS lookup instead of ping

## 2025-03-14
### Bug Fixes
- Startup process was setting variables in different places

## 2025-03-12
### New Features
- Added neurodesk copilot dependencies
### Bug Fixes
- Apptainer didn't mount binfmt, which was resulting in simg files not working in offline mode on apple silicon

## 2025-03-07
### Bug Fixes
- CVMFS_DISABLED=false also disabled it.

## 2025-03-06
### Improvements
- Add overlay directory on startup
### Bug Fixes
- Only link from cvmfs if cvmfs is not disabled

## 2025-03-05
### New Features
- Added support for downloading containers offline, can be activated by setting CVMFS_DISABLE=true
- Add [synthstrip](https://surfer.nmr.mgh.harvard.edu/docs/synthstrip/) 7.4.1
- Add [pydeface](https://pypi.org/project/pydeface/) 2.0.2 
- Add [[fmriprep](https://fmriprep.org/en/stable/).org/en/stable/) 24.1.1 20250214

### Improvements
- update [[BIDScoin](https://bidscoin.readthedocs.io/en/latest/)](https://[BIDScoin](https://bidscoin.readthedocs.io/en/latest/).readthedocs.io/en/latest/) to 4.5.0
- update [aslprep](https://aslprep.readthedocs.io/en/latest/) to 0.7.5 
- update [QSMxT](https://qsmxt.github.io/QSMxT/) to v7.3.1 
- update [QSMxT](https://qsmxt.github.io/QSMxT/) to v7.3.2
- changed from apptainer -w flag to overlay directory because it works with SIMG files
- disable automatic GPU flag --nv because it is causing problems on newer host OSs like Ubuntu 24.04
- automate zenodo doi creation and update to applist.json
- tweaks in chown of files in homedirectory (#268 #269)

## 2025-02-04
### New Features
- Add latency check for cvmfs direct vs CDN
- Add [fsl](https://fsl.fmrib.ox.ac.uk/fsl/docs/) 6.0.7.16 
- Add [dicomtools](https://wfwiggins.github.io/dicomtools/) container 
### Improvements
- update [freesurfer](https://surfer.nmr.mgh.harvard.edu/) 8.0.0 and nighres 

## 2025-01-29
### New Features
- Add [freesurfer](https://surfer.nmr.mgh.harvard.edu/) 8.0.0
### Bug Fixes
- In JVM - parameters only worked for arm64, not x86

## 2025-01-24
### New Features
- add [Matlab](https://www.mathworks.com/products/matlab.html) 2023b 
- add [Matlab](https://www.mathworks.com/products/matlab.html) 2022b 
- new Quay.io jupyter baseimage
### Improvements
- update version in neurodesk.yml 
- Change TinyRange share path to /data instead of /share
- updated [deepRetinotopy](https://github.com/Puckett-Lab/deepRetinotopy) version by
- update [Matlab](https://www.mathworks.com/products/matlab.html) 2024b
### Bug Fixes
- Added workaround for JVM bug on Apple M4
- added docker fix for MacOS to desktop

## 2024-12-06
- updated [QSMxT](https://qsmxt.github.io/QSMxT/): v7.2.2 
- add [heudiconv](https://heudiconv.readthedocs.io/en/latest/) 1.3.1 
- add [mriqc](https://mriqc.readthedocs.io/en/latest/) 24.0.2 20241108 
- add [samsrfx](https://github.com/samsrf/samsrf) v10.003 
- add palmettobug 0.0.1 20241119
- add neurodock/pydesigner 
- Update [dcm2niix](https://github.com/rordenlab/dcm2niix) version to 20241125 
- changed CVMFS servers
- added -w workaround for docker on apple silicon into dockerfile
- add static strace to /opt for container debugging
- enabled VNC again and fix RDP auto resizing

## 2024-10-22
- use cloudfront distribution only
- workaround for kernel bug on arm64
- add ipywidgets ipyvolume jupyterlab_widgets
- add [fsl](https://fsl.fmrib.ox.ac.uk/fsl/docs/) 6.0.7.14
- add [QSMxT](https://qsmxt.github.io/QSMxT/) v7.2.1 

## 2024-10-16
- add jupyter-resource-usage plugin
- disable VNC
- remove updating of example directory on startup
- update jupyter-server-proxy
- add more CVMFS servers
- Added relion 4.0.1.sm61 20240528
- update [aslprep](https://aslprep.readthedocs.io/en/latest/) to 0.7.0
- update deepretinotpy to 1.0.5
- add quickshear
- add nighres 1.5.1
- update [BIDScoin](https://bidscoin.readthedocs.io/en/latest/) 4.3.3 and 4.4.0
- Added bart 0.9.00
- updated [QSMxT](https://qsmxt.github.io/QSMxT/) to 7.1.0
- Added mrtrix3src (latest version)
- update VesselBoost to ver 1.0.0 by @KMarshallX in #301
- add qmrlab 
- added niimath
- updated [fsl](https://fsl.fmrib.ox.ac.uk/fsl/docs/) to 6.0.7.8
- update [aslprep](https://aslprep.readthedocs.io/en/latest/) to 0.7.2
- update ants to 2.5.3
- updated spinalcordtoolbox to 6.4 
- Update afni to 24.2.07 
- add [dcm2niix](https://github.com/rordenlab/dcm2niix) 
- add micapipe 0.2.3 
- added brainnetviewer 
- Added brainlifecli 
- update [fmriprep](https://fmriprep.org/en/stable/) to 24.1.0 
- Update dsistudio 2024.06.12 
- add vmtk 1.5.0

## 2024-05-25
- add new CVMFS CDN servers
- add jupyter_scheduler and ipycanvas
- update guacamole version to 1.5.5 and tomcat to 9.0.87
- add rise extension for presentations
- https://github.com/NeuroDesk/neurocommand/releases/tag/2024-05-25
- fixed brkraw by @stebo85 in #268
- [QSMxT](https://qsmxt.github.io/QSMxT/): v6.4.1 by @astewartau in #270
- update mrtrix3 by @stebo85 in #271
- [QSMxT](https://qsmxt.github.io/QSMxT/): v6.4.2 by @astewartau in #272
- [QSMxT](https://qsmxt.github.io/QSMxT/): v6.4.3 by @astewartau in #274
- update [BIDScoin](https://bidscoin.readthedocs.io/en/latest/) to 4.3.2 by @stebo85 in #275
- update [fmriprep](https://fmriprep.org/en/stable/) by @stebo85 in #277
- add julia 1.9.4 by @stebo85 in #280
- update dsi_studio by @stebo85 in #283
- add glmsingle by @stebo85 in #284
- ants 2.5.1 20240429 by @stebo85 in #285
- [QSMxT](https://qsmxt.github.io/QSMxT/): v6.4.4 by @astewartau in #287

## 2024-03-27
- Switched from singularity to apptainer
- added (brkraw) and fixed multiple tools (mrtrix3, julia)

## 2024-01-12
- fixed [fsl](https://fsl.fmrib.ox.ac.uk/fsl/docs/) GUI error, when starting [fsl](https://fsl.fmrib.ox.ac.uk/fsl/docs/) in VNC mode (the USER was not exported)
- removed c.ServerApp.root_dir setting because it was causing an error when clicking on the Home button. Now it's not possible to navigate outside of the homedirectory anymore in the side panel.

## 2023-11-28
- fixed a bug where the /proc/cpuinfo file under ARM did not contain a MHz entry, which stopped [Matlab](https://www.mathworks.com/products/matlab.html) from starting up
- fixed a bug where the SINGULARITY_BINDPATH was not send in a jupyter notebook file

## 2023-10-29
- bugfix: conda and mamba environments are now initialized correctly when neurodesktop starts up (not just in jupyter)

## 2023-09-20
- the neurodesktop image is now multi-arch and supports x86 and ARM64
- fixed recursive link creation in /data
- switched to new cvmfs server geolocation DNS steering policy system: cvmfs[1,2,3].neurodesk.org resolve to 3 servers per region which are compared for speed by the client on startup
- fixed recursive execution of bash shell inside a singularity container
- fixed empty username
- switched release tag naming scheme to YYYY-MM-DD instead of YYYYMMDD for better readability

## 20230628
- directories can now be deleted in jupyter interface even if they contain files
- moved startup configurations out of .bashrc
- removed redundant chown of homedirectory (e.g. affecting windows startup time)
- added git extension to juputerlab
- more robust handling of CVMFS edge cases

## 20230531
- included neurodesktop version in hostname
- removed apt lists
- triggered automount externally

## 20230525
- used jupyter based image
- fixed environment variables for nipype
- fixed RDP upload permission errors
- added symlink on home if /data is mounted

## 20221216
- added VNC connection back into docker container because RDP currently causes issues for european keyboards
- added [freesurfer](https://surfer.nmr.mgh.harvard.edu/) into AFNI container to get @SUMA_Make_Spec_FS to work (issue: https://github.com/orgs/NeuroDesk/discussions/210#discussioncomment-4337927)
- added deepretinotopy tool in version 1.0.0 20221201 (contributed by Xincheng & Fernanda)

## 20221129
- updated [QSMxT](https://qsmxt.github.io/QSMxT/) to 1.1.13 (contributed by Ashley)
- added nipype 1.8.3 (contributed by Steffen)
- added mneextended 1.1.0 (contributed by David)
- added new tool category "workflows"
- added new CVMFS mirror server in Phoenix
- added mimetypes so that nii/minc files now open in the respective applications
- [Matlab](https://www.mathworks.com/products/matlab.html) licenses can now be saved from the activation GUI
- update rstudio to 2022.07.2 (and R version to 4.1.2 with new additional packages, like brms) 

## 20220813
- updated [QSMxT](https://qsmxt.github.io/QSMxT/) to 1.1.12 (contributed by Ashley)
- updated 3D Slicer to 5.0.3 and included MONAI Label (contributed by Xincheng)
- added [Matlab](https://www.mathworks.com/products/matlab.html) 2022a (contributed by Oren)
- updated AFNI to 22.1.14 (contributed by Steffen)
- updated Spinal Cord Toolbox to 5.7 (contributed by Steffen)
- updated Oshyx to 0.4 (contributed by Jeryn)
- updated [freesurfer](https://surfer.nmr.mgh.harvard.edu/) to 7.3.2 (contributed by Steffen)
- added CVMFS mirror server in Perth and cleaned up server list to account for DNS geo location steering (contributed by Steffen)

## 20220701
- added laynii 2.2.1 - layer fMRI toolbox (contributed by Renzo Huber)
- added fieldtrip 20220617 - eeg processing (contributed by David White)

## 20220329
- added [BIDScoin](https://bidscoin.readthedocs.io/en/latest/) 3.7.0 (converting data to bids) contributed by Oren
- added sigviewer 0.6.4 (viewing electrophysiological data) contributed by Tom
- added niftyreg 1.4.0 (image registration tool) contributed by Steffen
- added mne 1.0.0 (EEG processing pipeline) contributed by David

## 20220302
- update of ROMEO (phase unwrapping) to latest version 3.2.8
- update of [QSMxT](https://qsmxt.github.io/QSMxT/) (automated end-to-end QSM processing) to latest version 1.1.10
- added mritools 3.3.0 (includes clearswi 1.0.1, mcpc3ds 0.1.0, romeo 3.2.8 as compiled binaries)

## 20220222
- update for PhysIO toolbox (physiological noise correction for fMRI) to r2021a including the latest SPM r8224
- update of lcmodel to include basis sets for 1.5-9.4T
- added a memory display plugin to illustrate how much memory is available to the container and how much is consumed
- added a version checker to help with identifying if a new version is available
- added file upload via guacamole (+ update of guacamole to 1.4) - users can now drag and drop their files onto guacamole and they get copied to the desktop

## 20220128
- update of Spinalcordtoolbox to 5.5
- update of CAT12 to r1933

## 20220121
- MNE Python 0.23.4 container including VScode and extensions
- VScode container including Python/Julia Extensions and singularity to test "Inception Mode" (Running singularity containers within singularity containers)
- update of [fsl](https://fsl.fmrib.ox.ac.uk/fsl/docs/) to 6.0.5.1
- added CAT12 (a software that allows estimation of tissue volumes (and additional surface parameters such as cortical thickness, gyrification or fractal dimension) for different volume and surface-based atlas maps)

## 20220111
- a deep learning based vessel segmentation algorithm "vesselapp" was added in version 0.3.1
- palm - Permutation Analysis of Linear Models - was added in version alpha119
- niistat running in octave was added with version 1.0.20191216
- MRIcroGL was updated to a version with included python support, so the scripting is now working
- rabies - Rodent Automated Bold Improvement of EPI Sequences was added with version 0.3.5
- oshyx was updated to 0.3

## 20211220
- neurodesktop can now be accessed via native RDP client as well (e.g. for multi-monitor support): https://neurodesk.org/docs/getting-started/neurodesktop/windows/#using-an-rdp-client
- there is a new Help button in the menu :)
- updates of ants 2.3.4 (now includes Scripts as well, including antsCookTemplatePriors.sh) + newly added version 2.3.5
- new version of [QSMxT](https://qsmxt.github.io/QSMxT/) 1.1.9 20211219
- new version of Spinal Cord Toolbox 5.4
- new tools: MRIcroGL and surfice - fantastic viewers for neuroimaging data


## 20211207
- Physio toolbox compiled and added to SPM + update of SPM
- added brainstorm 
- new neurodesktop container management scripts for Linux, Mac and Windows: https://github.com/NeuroDesk/neurodesktop 
- added fieldtrip 
- Datalad is now in the main image, so datalad run should work
- added Oshy-X segmentation tool
- updated [freesurfer](https://surfer.nmr.mgh.harvard.edu/) 7.2.0

## 20211028
- added EEGLAB

## 20211018
- added Rstudio, R and multiple R packages (plotly, car, tidyverse, ...)
- added ClearSWI and ROMEO for MRI phase processing (including new Tutorials: https://neurodesk.org/tutorials-examples/tutorials/phase_processing/)
- added more categories in applications menu (Body, Electrophysiology, Hippocampus, Phase Processing, Rodent Imaging, Shape Analysis, Spine, Statistics)
- bugfix: improved startup time of the desktop container (miniconda in homedirectory was causing chmod slowdown)
- bugfix: ssh, vnc and rdp servers are now restarted in case the container was stopped and started again (e.g. on Standby)


## 20210929
- fixed naming of aidmri to aidamri and added new category "Rodent Imaging"
- updated all tool icons and updated neurodesk icon including background image
- VScode now stores settings in persistent storage /neurodesktop-storage and with this keeps extensions and settings across different neurodesktop versions
- docker layers are now cached, so updating the desktop to the next version is very fast and consumes less disk space locally
- default theme of terminal changed from Solarized to Tango as the old theme was hiding information in tools like htop (same font colour on same background...)


## 20210923
- removed faulty [mriqc](https://mriqc.readthedocs.io/en/latest/) 0.15.2 container
- neurodesk.github.io is now starting page in firefox browser

## 20210918
- added [mriqc](https://mriqc.readthedocs.io/en/latest/) 0.16.1 and mrtrix 3.0.3

## 20210917
- included more tools for connecting to cloud storage services (rclone, owncloud, nextcloud, davfs2, globus). For more info: [Storage](/docs/getting-started/neurodesktop/storage)
- styling of desktop interface, including background wallpaper and colour scheme in terminal window
- new categories in menu system (visualization) and added more categories to tools

## 20210916
- This is the first version of the newly renamed and rebuild neurodesktop (previously vnm and neuromachine)
- containers are mounted by default from CVMFS, but this can be deactivated by adding `-e CVMFS_DISABLE=true` to the docker call

