---
title: "Distributed Neural Network"
date: 2026-05-20
draft: false
tags: ["Distributed Systems", "Machine Learning", "gRPC", "System Architecture"]
categories: ["Projects"]
github_link: "https://github.com/cht-au/FlightBowl"
featured_image: "/images/dnn.webp"
summary: "A distributed neural network training system utilizing an elastic, fault-tolerant Parameter Server architecture over gRPC."
---

[![GitHub](https://img.shields.io/badge/GitHub-Repository-green?logo=github)](https://github.com/cht-au/FlightBowl)

## 📌 The Problem
Machine Learning models are often highly compute-heavy, requiring massive amounts of calculations and large datasets. While solutions exist to distribute this machine learning workload, they typically demand a rigid, fixed number of worker nodes and require them to remain online throughout the entire training process. 

---

## 🛠️ Our Architecture
To solve this, we created a distributed ML training system using a **Parameter Server architecture** designed to be both **elastic** and **fault-tolerant**. The central server and worker nodes communicate via Google’s Remote Procedure Call (**gRPC**).  

### Key System Design Features:
* **Central Parameter Server:** Manages global model weights and synchronizes gradients.
* **Elastic Worker Nodes:** Nodes can dynamically join and leave the training cluster at any time. 
* **Fault Tolerance:** The architecture can handles instances worker or server crashes and restarts itself.
* **Parallel Training:** Improve training times through data partitioning across available nodes.

![Architecture Overview](/images/proj_dnn_overview.png)


---

## 📊 Results & Key Trade-offs

While we successfully achieved our core architectural goals, we uncovered significant trade-offs regarding efficiency and time in exchange for elasticity:

* We found that scaling the number of worker nodes increases system efficiency only up to a certain point. Beyond that threshold, communication and synchronization overhead begins to grow exponentially. We partially solved this problem by dynamically scaling the shard assignment sizes relative to the active number of workers to reduce communication costs.
* **Future Improvements:** The current iteration of the system experiences notable downtime for worker nodes while waiting for synchronization, which is a key area we aim to improve upon.

