---
title: '20 months of working my first job'
date: 2025-12-31    
permalink: /posts/2025/12/20-months-work-first-job/
collections: posts
tags:
  - connectomics
  - ultramicrotomy
  - robotics 
  - autonomy
---

*wip; first draft; don't read just yet*

# what makes building a high accuracy and high precision machines hard? 

#### the above question is primarily contingent on the scale

**40 nm to 10 microns**<br> 
**0.00000004 m to 0.00001 m**

#### physical limits
- mechanical
- optical
- electrical
- thermodynamics
- fluid dynamics

- you have a tissue sample that is embedded in resin
	- this resin mixture determines 
		- *manual process*
		- cutting performance / quality 
		- thermal coefficient 
		- trimming
		- chipping
		- physical attributes 
			- density
			- viscosity 
			- hysteresis 
	- trimming and facing
		- *manual process*
		- to get the required shape, you remove material 
		- this is not trivial, requires certain level of skill and finesse 
		- common issues
			- chipping
			- uneven faces
	- cutting 
		- *semi-automatic*
		- continuously cutting at about 40 nm using ultramicrotome
		- common issues
			- *might take a while to note them all*
  - collection
		- *automatic*
		- loop-assisted pickup and dropoff of the section 
		- 3 linear axis robot