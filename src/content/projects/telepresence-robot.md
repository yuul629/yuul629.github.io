---
title: Telepresence Robot — Design Approach for Interaction Subsystem
description: Designed, developed, and evaluated an expressive interaction pipeline for an immersive telepresence robot.
importance: 8
category: case-studies
img: /assets/img/projects/GP/fotos/Expression_rendering.png
---

> **Role:** Designer, Developer, and team leader  
> **Client:** Human Media Interaction group  
> **Keywords:** human-robot interaction, concept development, prototyping, user evaluation

_Telepresene robots allow people to interact remotely though a physical robotic embodiment equiped with a camera. This camera streams to a VR headset that the operator is wearing. This increases the quality of interaction, however much of the operator's non-verbal communication is lost._

_This project explored how facial expressivity could be added to a cost-constrained telepresence robot. I designed a modular interaction pipeline that captures the operator’s facial expressions using depth sensing, classifies them, and translates them into simplified expressions displayed on the robot itself. The work combined human-robot interaction, concept development, prototyping, machine learning, embedded hardware, and user evaluation._

**Design Approces** :
The pipeline can be characterized by two phases: expression recognition and expression rendering. Based on these phases I developed the system as to connected modules. THis alllowe for the functions to be developed in parraled and individually evaluated.

For expression recognition, I selected Time-of-Flight depth sensing instead of conventional RGB recognition. This reduced the amount of directly identifiable visual information being capture. Moreover, I selected a externally mounted sensor as not all VR headsets are equipped with interanally mounted camera's nor is the shape of a VR headset standardized.

For the robot face, I deliberately avoided a fully mechanical or highly realistic design. Instead, I developed a hybrid head combining a 3D-printed embodiment with digital facial features.

This kept the mechanism simple while retaining enough expressive freedom for social interaction.

**From Concepts to Final Form**:

The head design was developed through sketches, paper prototypes, hardware placement tests, and CAD iterations.

A major constraint was the stereo camera used for telepresence. Rather than hiding it, I integrated the camera lenses into the face as the robot's eyes.

The final plectrum-shaped head was selected because it created a recognizable facial structure without appearing overly human.

For expression rendering, I focused on the features with the strongest expressive value: eyebrows and mouth.

Three LCD displays were integrated into the head:

<ul>
    <li>left eyebrow;</li>
    <li>right eyebrow; </li>
    <li>mouth. </li>
</ul>

This allowed the robot to render distinct expressions while avoiding the complexity of mechanical facial actuation.

**System Implementation** :

The final subsystem consisted of:

Depth sensing → CNN classification → ROS 2 → Raspberry Pi → 3 LCD displays

A dedicated dataset was collected from 12 participants wearing a VR headset, resulting in 9,421 depth frames across five expression classes.

The depth data was cleaned, temporally filtered, and converted into a compact three-channel representation containing facial depth, movement, and variation over time.

A compact CNN was then trained to classify the expressions.

On the robot, a Raspberry Pi received expression labels through ROS 2 and rendered the corresponding eyebrow and mouth graphics over SPI.

Expression assets were stored locally on the Pi, meaning only the classification label had to be transmitted.

**A Critical Design Decision**

The recognition model achieved 37% accuracy and a 31% F1-score under leave-one-participant-out validation.

Although this was above the approximately 20% chance level, it was not reliable enough for real-time use with unseen users.

Instead of allowing the weak classifier to distort the evaluation of the robot face, I separated the two problems.

For the final interaction study, expression labels were manually sent through the same ROS 2 interface.

This allowed me to evaluate one question independently:

Does the expressive robot actually improve the interaction when the correct expression is rendered?

This decision made the evaluation more useful and clearly identified the FER model as the subsystem requiring further development.

**Evaluation**
Expression recognizability

The rendered expressions were evaluated with 37 participants.

Joyful, fearful, and indignant expressions were clearly distinguishable from the alternative labels.

The disgusted expression was frequently confused with indignant.

This showed that the simplified rendering strategy was effective, while also identifying a specific design that required further iteration.

**Impact on Interaction**

A second study compared a robot with static facial behaviour against the dynamically expressive version.

N = 12

Attribute Static Expressive
Warmth 2.04 4.08
Competence 1.50 3.96
Discomfort 2.00 2.00

Warmth and competence both improved significantly (p = 0.005), while discomfort did not significantly change.

Participants interacting with the expressive robot also described it as more responsive and reported feeling more heard.

The result was important because it showed that the design did more than display recognizable graphics:

the expressive behaviour changed how people perceived the robot.

**Design Outcome**

The strongest result of the project was the expression-rendering system.

The hybrid design demonstrated that a robot does not need a realistic or mechanically complex face to communicate emotion effectively. A small number of carefully selected digital features were enough to create a measurable improvement in perceived warmth and competence.

The evaluation also exposed limitations in my design decisions.

The similarity between the negative expressions made disgust and indignation difficult to distinguish, while participant feedback suggested that some negative expressions were too exaggerated for the interaction context.

A future iteration would therefore focus on expression intensity and differentiation, rather than simply increasing visual complexity.

The recognition pipeline requires further development before autonomous use, particularly through a larger and more diverse dataset and higher-quality depth data.

**Key Outcome**

The project resulted in a functional, modular expression-rendering system and a clear development path for automatic recognition.

More importantly, the evaluation demonstrated that simple, responsive facial expression can substantially change the perceived social quality of a telepresence robot.
