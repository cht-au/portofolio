---
title: "Bluetooth Low Energy Scanner"
date: 2025-05-01
draft: false
tags: ["Android Studio", "Kotlin", "BLE", "Mobile App"]
categories: ["Projects"]
github_link: "https://github.com/cht-au/ble-background-scan"
summary: "Android app that scans nearby BLE devices, displays RSSI strength, supports background scanning, and notifies users when beacons are in range."
---

[![GitHub](https://img.shields.io/badge/GitHub-Repository-blue?logo=github)](https://github.com/cht-au/ble-background-scan)

## Overview
This project investigates the capabilities of Bluetooth Low Energy (BLE) scanning on Android devices. The app explores how reliably and consistently Android devices can detect and log nearby Bluetooth signals. The bigger goal of the project is to see how Bluetooth can be leveraged to support research on human interaction and proximinity tracking.

## Challenges and Actions
To efficiently track interaction, the app required a mechanism to scan for BLE devices continuously, even  when the phone is locked or the app is running in the background. 

I first delved into Android Studio Developer  documentation to understand BLE scanning, scanning filters, and permission handling. Next, I developed a persistent background service, collected data from BLE packets, and displayed data to the user.  




## Results

The project demonstrates that Android devices can serve as reliable proximity trackers. The final app includes:

* **Continuous Background Scanning**
* **Realtime Received Signal Strength Indicator (RSSI) Graphing**
* **Promiximity Notification** when a user comes close to target beacons

The most interesting thing I learned is that the app will work even if it is off after all permission all granted. Any attempt to shut down the app on the phone will cause the app to restart itself. The only real way to stop the app is to uninstall it.
