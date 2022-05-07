# If you are looking for final projects please [see here](https://openastronomy.org/gsoc/)

These projects are work-in-progress ideas what have not yet made the jump to final projects.
The list of projects below will be changing as they are being taken by someone or made obsolete by the project as it moves on.

## Project Template

**Abstract**

**Requirements**

**Expected Outcomes**

**Idea from:**

**Possible mentors/help by**

***
***
***

## HELIO - capabilities improvement

### Description

SunPy has already the capability to access to the Heliophysics Events Catalogue provided by the HELiophysics Integrated Observatory.  This catalogue provides access to different lists of events observed anywhere in the heliosphere.  However, HELIO offers a lot more web services of interest for the solar community.  Some of the services can provide information of when and where a planet or instrument where located, properties on features detected on the sun, or properties of some heliospheric observations; moreover it also allow the discovery of new data by a propagation model which simulates three different scenarios - Coronal Mass Ejections, High speed solar wind and Solar Energetic Particles events.

This project would consist in the creation of an interface to access to HELIO services in a similar way that other services like HEK or VSO are accessible at the moment. HELIO uses VOTables as the standard to transfer the data, astropy provides support for reading such file format, therefore some understanding of astropy may be needed.

* Requirements: All the services from HELIO are through webservices (SOAP, REST), thus some understanding on that would be beneficial. VOTable parser provided from astropy will be used, so familiarization with such interface will be helpful.

* Difficulty: Medium

* Mentors: David Perez-Suarez, (Marco Soldati, Kevin Benson - HELIO)

## Feature Tracking / Detection

Framework and algorithms for detecting features in the solar atmosphere / magnetic fields on the solar surface.

Detection algorithms:

* Thresholding
* Clumping
* Downhill
* Curve

Tracking and property extraction using labelling and similar.

## GUI to use LCT tools

### Abstract

Abstract
The Local Correlation Tracking (LCT, November & Simon, 1988) technique is a robust method used to study the dynamics of structures in a time series of images. By tracking pixel displacements, using a correlation window, LCT can determine proper motions and generate flow maps of horizontal velocities. This procedure is used to study the dynamics of plasma in the solar photosphere at different spatial scales, e.g the analysis of granular and super-granular convective cells, meridional flows, etc.

### Description

A widget implemented in Python was developed. It generates a user-friendly graphical user interface (GUI) to control various parameters for the process of calculating flow maps of proper motions for a series of filtergrams (data cube). Our purpose is to implement this tool in Sunpy and to improve it with some more options, i.e. masks, statistics, histograms, contours and multi-plots. Although an initial version is already developed, our proposal is to focus on the efficient integration of the code in the  SunPy libraries. The code (without widget files yet) is <https://github.com/Hypnus1803/flow_maps>

### Requirements

Python and basic knowledge of GUI design (qt4,pyqt4)

### Expected Outcomes

* To integrate efficiently the code in SunPy libraries.

### Idea from

Jose Iván Campos Rozo (National Astronomical Observatory, National University of Colombia)

### Mentor:s

* Jose Iván Campos Rozo (National Astronomical Observatory, National University of Colombia)
* Santiago Vargas Domínguez(National Astronomical Observatory, National University of Colombia)
* David Pérez Suárez.
