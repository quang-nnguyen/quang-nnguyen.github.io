---
title: "Drowsiness Detection Using Haar Feature and Decision Tree"
date: 2019-08-03
tags: ["image processing", "machine learning", "decision tree", "face detection"]
header:
    teaser: "assets/images/decision-tree.jpg"
excerpt: "A simple software detecting user's drowsiness level by tracking eye activities."
sidebar:
  - title: "Role"
    # image: http://placehold.it/350x250
    # image_alt: "logo"
    text: "Principal Investigator"
---

## Introduction
A simple software detecting user's drowsiness level by tracking eye activities.

There are 4 main stages:

- Face Detection - AdaBoost
- Eyes Localization - Random Forest
- Eye state monitoring - Various image processing techniques (global thresholding and image dilation)
- Drowsines Detection - Automatic threshold selection
The program was primarily implemented in MATLAB, some parts in C/C++ (mex file) to boost up the performance.