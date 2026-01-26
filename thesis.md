---
layout: default
title: Master's Thesis
---

# Master's Thesis

**Degree:** M.Sc. in Robotics  
**Completion:** August 2024  

---

## Title
*Development of Automated System for Diagnosing Chronic Venous Insufficiency using Artificial Intelligence-Based Robot*

---

## Abstract
Chronic venous insufficiency (CVI) is a condition in which blood stagnates in the lower extremities due to venous valve dysfunction, resulting in venous hypertension. Lower extremity edema is a common symptom of CVI. The primary diagnostic method for CVI is duplex ultrasound scanning, in which a clinician scans the lower extremities of a patient using an ultrasound probe and observes the images. During this procedure, the patient performs the Valsalva maneuver to intentionally induce blood reflux. CVI is diagnosed when blood reflux lasts more than 0.5 seconds in the superficial veins and more than 1.0 seconds in the deep veins.

However, the Valsalva maneuver cannot ensure consistent examination results, and the duration of blood reflux does not reflect the severity of CVI. These factors make it difficult to select appropriate treatment methods and monitor their effectiveness. Additionally, ultrasound examination results are significantly influenced by the skill and fatigue level of clinicians.

To address these limitations, this dissertation proposes an automated system for diagnosing CVI using an artificial intelligence-based robot. We developed a robotic ultrasound examination system to eliminate variability caused by the condition of clinicians. This system uses a depth camera to recognize contact points on the calves and acquires high-quality ultrasound images through precise force control.

In addition, an AI-based CVI diagnostic algorithm was developed. To avoid the use of qualitative diagnostic criteria, we introduced a new diagnostic index called the 'balance ratio.' The balance ratio is derived from the characteristics of calf vessels, representing the diameter ratio of deep veins and arteries. An artificial neural network is designed and trained to find the deep vein-artery pairs in ultrasound images. CVI is diagnosed by extracting the balance ratios from the detected blood vessel pairs.

---

## Keywords
Chronic Venous Insufficiency · Diagnostic Robotics · Artificial Intelligence · Mathematical Modelling · Automation System

---

## Methods & Tools
- ROS / ROS2
- Simulation (Gazebo)
- Control algorithms
- Perception
- Sensor fusion

---

## Results
- Experimental setup
- Evaluation results
- Key findings

---

## Resources
<a href="https://www.riss.kr/search/detail/DetailView.do?p_mat_type=be54d9b8bc7cdb09&control_no=80a57115cf332585ffe0bdc3ef48d419&outLink=K"
   target="_blank">
  🔗 View thesis on official university site
</a>
- [Source code](https://github.com/SUN1031/thesis-repo)
- Demo video (if available)
