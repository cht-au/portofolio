---
title: "Underwater Fish Tracker"
date: 2025-07-01
draft: false
tags: ["MATLAB", "Image Processing", "Computer Vision", "Research"]
categories: ["Projects", "Research"]
github_link: "https://github.com/cht-au/Ishii-Lab-Image-Processing"
image: "/assets/images/fish_tracking.png"
summary: "A MATLAB-based motion tracking pipeline using edge detection, contrast enhancement, and blob analysis to track fish behaviors through underwater obstructions."
---

🔗 [View GitHub Page](https://github.com/cht-au/Ishii-Lab-Image-Processing)

## 📌 The Challenge
Given an underwater video of feeding fish, our research goal was to capture and analyze the hunger levels of the fish. Tracking objects in underwater environments presents unique computer vision challenges:

1. **Low Light:** Less light hits the camera sensor deep in the water.
2. **Medium Distortion:** Light undergoes distortion as it travels through a water medium before reaching the lens.
3. **Physical Obstructions:** In our specific footage, a physical net obscured the fish, interfering with standard tracking algorithms.

---

## 🛠️ The Image Processing Pipeline
To tackle these challenges, we broke the problem down into three sequential phases:

### 1. Image Enhancement
We experimented with several methods of enhancing the underwater footage across different color spaces and settings. While we ultimately settled on converting the images to high-contrast black and white for consistency, there are likely still many alternative ways to optimize the raw image data.
![Image enhancement](images/ishii_1.png)



### 2. Removing the Net
We managed to isolate and remove the obscuring net by leveraging MATLAB’s **edge detection** and **image dilation** techniques, effectively filtering out the grid lines of the net from the background.
![Net removal](images/ishii_2.png)




### 3. Data Extraction & Tracking
Following net removal and enhancement, we used MATLAB’s built-in computer vision functions to isolate the fish and generate their bounding boxes. From there, we implemented a naive position tracking algorithm to track individual fish across frames, allowing us to calculate and measure their velocities.
![Net removal](images/ishii_3.png)
![Net removal](images/ishii_4.png)

---

## 🚀 Results & Future Challenges

We successfully created a complete pipeline capable of taking raw underwater video with net obstructions and tracking the fish with **~80% accuracy**. 

While we extracted meaningful motion data from the footage, we encountered a major domain-specific challenge: the video only provides usable activity data during actual feeding windows, remaining empty the rest of the time. The ongoing challenge is finding ways to extract meaningful data to determine fish hunger solely from these brief feeding intervals.