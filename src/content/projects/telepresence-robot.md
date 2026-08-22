---
title: Telepresence Robot — Design Approach for Interaction Subsystem
description: Designed, developed, and evaluated an expressive interaction pipeline for an immersive telepresence robot.
importance: 8
category: case-studies
img: /assets/img/projects/GP/fotos/Expression_rendering.png
---

**Role:** Designer, Developer, and team leader

**Client:** Human Media Interaction group

**Keywords:** human-robot interaction, concept development, prototyping, user evaluation

Telepresene robots allow people to interact remotely though a physical robotic embodiment equiped with a camera. This camera streams to a VR headset that the operator is wearing. This increases the quality of interaction, however much of the operator's non-verbal communication is lost.

This project explored how facial expressivity could be added to a cost-constrained telepresence robot. I designed a modular interaction pipeline that captures the operator’s facial expressions using depth sensing, classifies them, and translates them into simplified expressions displayed on the robot itself. The work combined human-robot interaction, concept development, prototyping, machine learning, embedded hardware, and user evaluation. 

**Design Approces**
TThe pipeline can be characterized by two phases: expression recognition and expression rendering. Based on these phases I developed the system as to connected modules. THis alllowe for the functions to be developed in parraled and individually evaluated. 

For expression recognition, I selected Time-of-Flight depth sensing instead of conventional RGB recognition. This reduced the amount of directly identifiable visual information being capture. Moreover, I selected a externally mounted sensor as not all VR headsets are equipped with interanally mounted camera's nor is the shape of a VR headset standardized. 

For the robot face, I deliberately avoided a fully mechanical or highly realistic design. Instead, I developed a hybrid head combining a 3D-printed embodiment with digital facial features.

This kept the mechanism simple while retaining enough expressive freedom for social interaction.
