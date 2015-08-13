---
layout: post
draft: true
title: Diabetic retinopathy detection contest: what we did wrong
---

After watching the [awesome video course by Hugo Larochelle](https://www.youtube.com/playlist?list=PL6Xpj9I5qXYEcOhn7TqghAJ6NAPrNmUBH) on neural nets (more on this in the [previous post]({% post_url 2015-07-30-getting-started-with-neural-networks %})) we decided to test our knowledge on some computer vision contest. We looked at [Kaggle](https://www.kaggle.com/competitions) and the only active competition related to computer vision (except for the [digit recognizer contest](https://www.kaggle.com/c/digit-recognizer), for which lots of perfect out-of-the-box solutions exist) was the [Diabetic retinopathy detection contest](https://www.kaggle.com/c/diabetic-retinopathy-detection). This was probably quite hard to become our very first project, but nevertheless we decided to try. The team included [Karen](https://www.linkedin.com/in/mahnerak), [Tigran](https://www.linkedin.com/in/galstyantik), [Hrayr](https://github.com/Harhro94), [Narek](https://www.linkedin.com/pub/narek-hovsepyan/86/b35/380) and [me](https://github.com/Hrant-Khachatrian). Long story short, we finished at the [82nd place](https://www.kaggle.com/c/diabetic-retinopathy-detection/leaderboard), and in this post I will describe in details what we did and what mistakes we made. We hope this will be interesting for those who just start to play with neural networks. Also we hope to get feedback from experts and other participants.


## The contest
[Diabetic retinopathy](https://en.wikipedia.org/wiki/Diabetic_retinopathy) is a disease when the retina of the eye is damaged due to diabetes. It is one of the leading causes of blindness in the world. The contest's aim was to see if computer programs can diagnose the disease automatically from the image of the retina. [It seems](https://www.kaggle.com/c/diabetic-retinopathy-detection/forums/t/15605/human-performance-on-the-competition-data-set) the winners slightly surpassed the performance of general ophthalmologists. 

Each eye of the patient can be in one of the 5 levels, from 0 to 4, where 0 corresponds to the healthy state and 4 is the most severe state. Different eyes of the same person can be at different levels (also some contestants could leverage the fact they are not completely independent). Contestants were given 35126 JPEG images of retinas for training (32.5GB), 53576 images for testing (49.6GB) and a CSV file where level of the disease is written for the train images.