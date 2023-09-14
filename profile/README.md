# Australian Scalable Drone Cloud

https://asdc.io

A summary of descriptions and purposes of repositories in this organisation

Owen Kaluza, Monash University - written/current as of 14/3/2023

## Core repos

### [DronesVL](https://github.com/AuScalableDroneCloud/DronesVL)
Admin scripts to bootstrap, shutdown and update the deployment clusters: load configuration and secrets, bootstrap FluxCD for deployment from live repo below.
Key branches: 
- *master* - production state
- *development* - dev version. To deploy to the production site, you must set the ASDC_ENV variable to PRODUCTION, eg: `export ASDC_ENV=PRODUCTION` before running any scripts.

### [asdc-infra](https://github.com/AuScalableDroneCloud/asdc-infra) (private)
This is the live repo for FluxCD deployment, changes here are propgated to the live deployments.  
Key branches: 
- *production* : the production site deployment (https://asdc.cloud.edu.au)
- *development* : the development site deployment (https://dev.asdc.cloud.edu.au)

### [nvidia-driver-build-fedora](https://github.com/AuScalableDroneCloud/nvidia-driver-build-fedora)
This is the NVidia driver image build customised for our Nectar OpenStack Fedora CoreOS version, if the FedoraCoreOS version is updated along with a new Kubernetes release on OpenStack Magnum, this image will need to be rebuilt with the updated kernel versions, can also be rebuilt when NVidia driver updates are provided.

## WebODM - Main web site

### [WebODM](https://github.com/AuScalableDroneCloud/WebODM)
An extensively customised fork of the Open Source project WebODM from OpenDroneMap, https://github.com/OpenDroneMap/ this runs as the base software for operating the platform.  
This needs to be kept up to date with the upstream repo.  
All changes are rebuild into the development image and deployed continuously. Only versioned releases are deployed to the production site.

### [asdc-init](https://github.com/AuScalableDroneCloud/asdc-init)
This repository contains configuration and utilities to deploy WebODM, including the asdc_plugin below and other plugins and scripts.
Key branches: 
- *main* : production deployment, on production the submodule plugins/asdc controls the deployed version of the asdc_plugin repo below. 
- *development* : development deployment, on dev the latest github repo version of the asdc_plugin is always deployed so no need to keep the submodule version up to date

### [asdc_plugin](https://github.com/AuScalableDroneCloud/asdc_plugin)
This is a WebODM plugin for ASDC specific features, developed to try and keep most customisations specific to our deployment of WebODM separate from the rest of the WebODM project code, although there are still significant changes that had to be made in the fork as well. Provides the ASDC Tools and Pipelines menu items and additional per-project and task buttons for ASDC functionality.

### [ClusterODM](https://github.com/AuScalableDroneCloud/ClusterODM)
Small modifications to the OpenDroneMap/ClusterODM project, needs to be keept up to date with upstream image

### [NodeODM](https://github.com/AuScalableDroneCloud/NodeODM)
Small modifications to the OpenDroneMap/NodeODM project, needs to be keept up to date with upstream image

## Pipelines / Jupyterhub

### [asdc_python](https://github.com/AuScalableDroneCloud/asdc_python)
This is the ASDC python API to access the WebODM and our custom API features from python, in particular from the ASDC JupyterHub environment.
It also contains Jupyterhub server features to automate authentication tokens and sharing data between the WebODM site and Jupyterhub.

### [pipelines](https://github.com/AuScalableDroneCloud/pipelines)
This repo holds the core docker images for the Jupyterhub environments, there are currently 3 images:
- **base** CPU only image
- **gpu** GPU image, includes GPU support and CUDA libraries etc
- **ml** ML+GPU image, GPU image with additional ML libraries
Deployment is as WebODM, all updates pushed to dev site, versioned releases deployed to production

### [pipelines-jupyter](https://github.com/AuScalableDroneCloud/pipelines-jupyter)
This holds the base pipeline definitions (pipelines.yaml) and subdirectories for pipeline notebooks and code for the core ASDC Jupyterhub pipelines. New pipelines can be created by editing pipeines.yaml and adding the subdirectory to this repo or an external repo.

### [pipeline-fracture](https://github.com/AuScalableDroneCloud/pipeline-fracture)
This is the Structural Geology use case Fracture Detection pipeline and dependencies, example of a pipeline existing in its own repo.

## Applications

### [cesium-asdc](https://github.com/AuScalableDroneCloud/cesium-asdc)
Cesium deployment for https://cesium.asdc.cloud.edu.au/cesium/Apps/ASDC/  
Deployment of all updates pushed to dev site, versioned releases deployed to production

### [cesium-api](https://github.com/AuScalableDroneCloud/cesium-api)
Cesium API and ept server deployment
Deployment of all updates pushed to dev site, versioned releases deployed to production

### [terria-asdc](https://github.com/AuScalableDroneCloud/terria-asdc)
Terria app deployment for https://terria.asdc.cloud.edu.au  
Deployment of all updates pushed to dev site, versioned releases deployed to production

## Misc

### [Tracker](https://github.com/AuScalableDroneCloud/Tracker/issues)
Used to track issues for parts of the system that do not have their own issue tracker, including forked repos such as our WebODM fork https://github.com/AuScalableDroneCloud/Tracker/issues

### [Documentation](https://github.com/AuScalableDroneCloud/documentation)
Intended for platform documentation, based around the wiki site at https://github.com/AuScalableDroneCloud/documentation/wiki

## Other repos

Any repositories not listed above are mostly forks of other open-source tools we have used and made a modification to or archived, there are also a few currently unused components or legacy tools
