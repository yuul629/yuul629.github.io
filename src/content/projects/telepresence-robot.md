---
title: A Design Approach for Facial Expressivity Pipeline in Telepresence Robots
description: Designed, developed, and evaluated a pipeline for facial expressivity on an immersive telepresence robot. The work was nomination for the "Creative Technogoly Graduation Award", this resulted in a third place overall.
importance: 1
category: case-studies
img: /assets/img/projects/GP/fotos/Expression_rendering.png
---

**Role:** Designer and developer
**Client:** Human Media Interaction group  
**Project-type**: Individual
**Keywords:** human-robot interaction, concept development, prototyping, user evaluation

## Project Description

_Telepresence robots allow operators to participate in social interaction from a remote location through a robotic embodiment. These interactions are often described from the operator’s
perspective, while the quality of interaction is also shaped by the interactors’ perception of the robot. In human-to-human interaction, facial expressions play a crucial role in commu-
nicating emotion and empathy._

This project explored how facial expressivity could be added to a cost-constrained telepresence robot. I designed a pipeline that captures the operator’s facial expressions using a time-of-flight (TOF) sensor, classifies the captured expression, and renders a pre-design corresposning expression on the robot. This prototype was realized using a modular approach using. The work combined human-robot interaction, concept development, prototyping, machine learning, embedded hardware, and user evaluation.

## Design Approces

The pipeline can be characterized by two phases: expression recognition and expression rendering. Based on these phases I developed the system as to connected modules. This alllowed for the modules to be developed in parrallel and individually evaluated. During the development of user centered concept 3 pilars were central.

<ul class="project-list">
    <li> A evidence based approach, this was used to identify state of the art technologies: using a TOF sensor as siggested by Zhang et al. [1] to capture expressions and using a hybrid embodyment were expressions were digitally rendered on a physical embodiment [2]. This research Shaping the direction of the project. </li>
    <li> Prototping, in various stages of the development lead me to mittigate gues work. Based one different phases of (concept) developement I applied low-fidelity prototyping methods such as sketching and paper prototyping or high fidelity prototyping methods such as CAD modeling and hardware.</li>
    <li> Continous evaluation of design decisions with the client and potential throughout the developement of the concept safe ensured that the final design positively contributed to the users exeriences. </li>
</ul>

## Engineering decisions

### Time of fight sensor

For expression recognition, I selected time of flight sensor instead of conventional RGB recognition. This reduced the amount of directly identifiable visual information being capture. Moreover, I selected a externally mounted sensor as not all VR headsets are equipped with interanally mounted camera's nor is the shape of a VR headset standardized.

### Hybrid rendering approach

For the robot face, I deliberately avoided a fully mechanical expressions as the robot had to be simple mechanically simple or highly realistic design to omit the uncanny valley. Instead, I developed a hybrid head combining a 3D-printed physical embodiment with digital facial features. The digital features were realized using pre-designed facial expressions renderd on LCD screens.

### ROS2

For the realization of the pipeline ROS2 Kilted Kajiu was selected and used in combination with Ubuntu 24.04 as this supported the modular development approach.

### Wizard of Oz recognition

For the recognition a facial expression a CNN was used in combination with different preprocessing techniques. The recognition model achieved 37% accuracy and a 31% F1-score under leave-one-participant-out validation. Although this was above the approximately 20% chance level, it was not reliable enough for real-time use with unseen users. Therefore the final interaction study, used a Wizzard of Oz approach were expression labels were manually sent through the same ROS 2 interface.

## Design decisions

### Selecting a face shape

The final face shape was developed using sketches, paper prototypes, and hardware placement tests. In the first two itterations of sketches played with different face shapes and different expression methods such as eyes and eyebrows. During coffee chats with fellow students I learned what face shapes appealled to them, based on their input I selected and developed a final design. The final plectrum-shaped head was selected because it created a recognizable facial structure without appearing overly human. This shape was then translated into a CAD model.

<div class="image-row">
  <figure>
    <img
      src="\public\assets\img\projects\GP\fotos\itt2.jpg"
      alt="Figure :First iterration of the sketches"
    />
    <figcaption>First set of sketches blurting different shapes.</figcaption>
  </figure>

  <figure>
    <img
      src="\public\assets\img\projects\GP\fotos\itt2-2.jpg"
      alt="Figure: Second itteration of the sketches"
    />
    <figcaption>Second itteration of the sketches based on the first set. </figcaption>
  </figure>
</div>

### Hardware placement

A major constraint was the stereo camera used for telepresence, as it size determined the size of the robotic head. Using paper prototyping I ideated on different positions, this resulted in the camera lenses figurating as the robot's eyes. However, the lenses were uncanny small in comparising to the size of the head which had to accomodate the camera's body. To solve this I addded extra circular plates to increase the size of the eyes.

<div class="image-row">
  <figure>
    <img
      src="\public\assets\img\projects\GP\fotos\20260409_105253.jpg"
      alt="Paper prototype for the placement of the stereocamera"
    />
    <figcaption>Paper prototype for the placement of the stereocamera were the lenses figurate as eyes.</figcaption>
  </figure>

  <figure>
    <img
      src="\public\assets\img\projects\GP\fotos\20260409_105020.jpg"
      alt="Paper prototype for the placement of the stereocamera"
    />
    <figcaption>Paper prototype for the placement of the stereocamera were the lenses figurate as the cheeks.</figcaption>
  </figure>
</div>

### Design of the expressions

For expression rendering, I focused on the features with the strongest expressive value according to literature: eyebrows and mouth. Due to the time constraint, I addapted a design from Wang et al. [3] to fit in the hybrid design. 

<figure class = small-image>
  <img
    src="\public\assets\img\projects\GP\fotos\Rendering.png"
    alt="In this figure the results from the preveided interaction quality."
  />
  <figcaption>
    In this figure the results from the preveided interaction quality are described. The results were evaluated using a Post Hoc Wilkinson rank test. 
  </figcaption>
</figure>


## Realization of the prototype

### CAD design

The selected faceshape was further developed into a CAD model using Onshape. For each component an attatchment approach was selected that allowed me to easily reach the component while still being secure.

<figure class = small-image>
    <img
        src="\public\assets\img\projects\GP\fotos\Exploded-view.png"
        alt="Exploded view of assembly showing all of the components"
    />
    <figcaption>Exploded view of assembly showing all of the components.</figcaption>
</figure>

### Fabrication

Using a 3D printer the CAD model was realized and adjusted. While printing I rotated the dome shape to 55 degrees so that the design curved was printed well. Additionally, to **omit waistfull** printing while prototyping I printed larger parts in smaller components. Which allowed me to first test the fits.

## Outcome
### Functional prototype

The design process described above led me to build a semi functional pipeline. In the video below I recorded a demo of the change in facial expressions.  

<figure className="project-video-container">
  <video
    autoPlay
    muted
    loop
    playsInline
    preload="metadata"
    className="project-video"
  >
    <source
      src="\public\assets\videos\demo-dynamic-expression.mp4"
      type="video/mp4"
    />
  </video>

  <figcaption>
    Functional prototype demonstrating the change in facial expressions.
  </figcaption>
</figure>

### Expression recognizability

The rendered expressions were evaluated with 37 participants. Joyful, fearful, and indignant expressions were clearly distinguishable from the alternative labels. The disgusted expression was frequently confused with indignant.

This showed that the simplified rendering strategy was effective, while also identifying a specific design that required further iteration.

<figure class = small-image>
  <img
    src="\public\assets\img\projects\GP\fotos\recognition-expression.png"
    alt="In this figure the results from the preveided interaction quality."
  />
  <figcaption>
    In this figure the results from the preveided interaction quality are described. The results were evaluated using a Post Hoc Wilkinson rank test. 
  </figcaption>
</figure>

### Impact on Interaction

A second study compared the perceived quality of interatior of a robot with static facial behaviour against the dynamically expressive version with 12 participants using a script, insert script. The participant evalueted the interaction using a shortend Robot Social Attribute Scale.

<figure class = small-image>
  <img
    src="\public\assets\img\projects\GP\fotos\perceived-interaction.png"
    alt="In this figure the results from the preveided interaction quality evaluation are shown."
  />
  <figcaption>
    In this figure the results from the preveided interaction quality are described. These results are a summary of a performed Man-Withney U Test.
  </figcaption>
</figure>

### Design Outcome

The strongest result of the project was the expression-rendering system. The hybrid design demonstrated that a robot does not need a realistic or mechanically complex face to communicate emotion effectively. A small number of carefully selected digital features were enough to create a measurable improvement in perceived warmth and competence.

The evaluation also exposed limitations in my design decisions.

The similarity between the negative expressions made disgust and indignation difficult to distinguish, while participant feedback suggested that some negative expressions were too exaggerated for the interaction context.

A future iteration would therefore focus on expression intensity and differentiation, rather than simply increasing visual complexity.

The recognition pipeline requires further development before autonomous use, a larger and more diverse dataset and higher-quality depth data could improve the classifyier.

## References

[1] J. Zhang, X. Xie, G. Peng, L. Liu, H. Yang, R. Guo, J. Cao, and J. Yang, “A real-time and privacy-preserving facial expression recognition system using an ai-powered
microcontroller,” Electronics, vol. 13, no. 14, p. 2791, 2024.

[2] M. Wairagkar, M. R. Lima, D. Bazo, R. Craig, H. Weissbart, A. C. Etoundi, T. Reichen-bach, P. Iyengar, S. Vaswani, C. James, et al., “Emotive response to a hybrid-face robot
and translation to consumer social robots,” IEEE Internet of Things Journal, vol. 9, no. 5, pp. 3174–3188, 2021. (accessed Mar. 13, 2026).

[3] T. Wang, L. Liu, L. Yang, and W. Yue, “Creating the optimal design approach of facial expression for the elderly intelligent service robot,” Journal of Advanced Mechanical
Design, Systems, and Manufacturing, vol. 17, no. 5, pp. JAMDSM0061–JAMDSM0061, 2023. Accessed 21 Apr. 2026.
