---
layout: post
title: Pneumonia Diagnosis
---
This project focuses in the diagnosis of pneumonia based on X-ray images.

**Business Case:**

Pneumonia is the world’s leading cause of death for children under 5 years of age  and it is one of the top ten most expensive conditions to treat inpatient in the US . Advances in pneumonia diagnosis could help reduce the pneumonia death toll and hopefully help avoid costly complications.

X-rays are the most common imagining tool, but there is a shortage of experts to interpret X-ray images in certain locations of the world.   The automation of interpretation of images may help fill this gap where a specialist is not available.

**Diagnosis Process:**

Normally, doctors have two sets of information when diagnosing pneumonia. The symptoms the patient is experiencing and the X-ray images. This project focused in the diagnosis of pneumonia based on the X-ray images only.

**The Data:**

The relevant information when examining chest images for pneumonia is the presence or not of opacities in the lungs. The presence of opacities is associated with fluids in the lungs and it indicated that there may be an infectious process in the lungs, pneumonia.

The dataset used for this project includes more than 25,000 images. The dataset was unbalanced and included 22% x-rays of patients with pneumonia. 

**The model:**

I looked into different approached for the development of the model specifically neural networks transfer learning and an object detection system (yolo). The results achieved from the transfer learning approach were significantly better that for the object detection approach.

The transfer learning approach focused on the use of the VGG16 and ResNet50 architectures trained with the imagined database. I removed the last layer for theses architectures, kept the weights for the remaining layers and tried different configurations for the final layer. The configuration that achieved the best result was using a single sigmoid activated layer trained with the images in the dataset.

The results were evaluated by comparing the ROC AUC. The dataset is unbalanced and this metric is more appropriate in this case than accuracy. The model with the highest area under the ROC curve was the VGG16 model, and its ROCAUC was 0.82.

**Evaluating results:**

The metrics show that the model has predictive power, but how does it compare with a real-life application.

I took into consideration the average F1 score for radiologist as per the research published by the Stanford ML group , which tasked radiologist with the diagnosis of pneumonia by interpreting the chest X-ray images only.  The radiologist average F1 score for this study was 0.387. The dataset used for this study is different to the dataset I used. Still, this value is a good baseline to consider. The F1 score for the model is 0.573. This shows an improvement over the radiologist performance given a similar task.

**Conclusions:**

A model based on transfer learning was developed to diagnose pneumonia using X-ray images only.

The performance of the model shows an improvement over the performance of radiologists given a similar task.

**Future work:**

It would be ideal to develop a model with the same information that a doctor normally has, symptoms and X-ray images. The current research body shows that it is possible that a model could perform as well and potentially better than doctors given the same information. This hopefully could expedite diagnosis and treatment for some patients.


References:

  http://www.who.int/en/news-room/fact-sheets/detail/pneumonia
  
  https://www.hcup-us.ahrq.gov/reports/statbriefs/sb204-Most-Expensive-Hospital-Conditions.jsp
  
  Everton, Kathryn L., et al. "White paper report of the 2011 RAD-AID conference on international radiology for developing countries: integrating multidisciplinary strategies for imaging services in the developing world." Journal of the American College of Radiology 9.7 (2012): 488-494.
  
  https://www.kaggle.com/c/rsna-pneumonia-detection-challenge
  
  Rajpurkar, Pranav, et al. "Chexnet: Radiologist-level pneumonia detection on chest x-rays with deep learning." arXiv preprint arXiv:1711.05225 (2017).

