---
title: "Service Analysis and Network Diagnosis"
layout: splash
# author_profile: true
header:
  overlay_color: "#565554"
  overlay_filter: "0.5"
  #overlay_image: /assets/images/unsplash-image-1.jpg
  actions:
    - label: "View Network Dashboard"
      url: "https://psmad.opensciencegrid.org/maddash-webui/index.cgi"
    - label: "Historical Network Performance"
      url: "https://atlas-kibana.mwt2.org/s/networking/app/kibana#/dashboard/perfSONAR"
    - label: "View Perfsonar Collector Performance"
      url: "https://gracc.opensciencegrid.org/dashboard/db/perfsonar-collector?orgId=1"
    - label: "View Github"
      url: "https://github.com/sand-ci"
    - label: "perfSONAR Toolkit Information"
      url: "https://toolkitinfo.opensciencegrid.org/toolkitinfo/"
  caption: ""
excerpt: 'Combine, visualize, and analyze disparate network monitoring and service logging data'
intro: 
  - excerpt: 'Service Analysis and Network Diagnosis'
feature_row:
  - image_path: /images/sample_packet_loss.png
    alt: "Sample packet loss graph"
    title: "Packet Loss Tracking"
    excerpt: "Sample packet loss graph from the SAND archive"
  - image_path: /images/sample_throughput.png
    alt: "Sample TCP throughput graph"
    title: "Throughput Tracking"
    excerpt: "SAND's archives record historical single-stream TCP throughout across many links"
---

## About SAND

The SAND project coordinates network monitoring and diagnostics from over a hundred application-level
measurement points and aggregates them into a measurement archive.  This curated measurement archive
provides access to historical and quasi-real-time network performance data, allowing for higher-level
diagnastics and analyses.

SAND supports and collaborates with long-running activities such as the
[OSG-Networking area](https://opensciencegrid.org/networking/) and the
[WLCG Throughput working group](https://twiki.cern.ch/twiki/bin/view/LCG/NetworkTransferMetrics).  The
data collected by each of these projects goes into the SAND Network Monitoring Archive (SAND-NMA).

{% include feature_row %}

## Abstract

Increasingly, science has become a "team sport" with projects less likely to be conducted by a single
investigator or university group but with multi-institution collaborations spanning many universities
and national laboratories. As these collaborations have become data-intensive, highly-performant
network links connecting their distributed science platforms have become increasingly important. While
true across all science, some collaborations, like those at the Large Hadron Collider (LHC) at CERN,
transfer millions of gigabytes across global networks today and anticipate orders of magnitude increases
within the next decade. Without performant networks and efficient data transfer and access services,
the time to science will be greatly compromised. In this context, high-speed, long-distance networks
see their performance degrade surprisingly quickly in the face of modest error rates. Accordingly,
network engineers and researchers use sophisticated tools to monitor the network and transfer services.
Without a means to aggregate and correlate network tests, performance measurements, and application
response, they at best can only reveal a small piece of the overall problem. This project focuses on
techniques that better combine, visualize, and analyze disparate network monitoring and service logging
data, providing a comprehensive picture critical to the engineers and scientists relying on the network.
This will allow problems to be located and fixed more quickly, reducing the time to science.

## Weekly Meeting

| **When**   | Monday, 3:00–4:00 p.m. Central Time                         |
| **Online** | [https://unl.zoom.us/j/344520180](https://unl.zoom.us/j/344520180)                             |
| **Phone**  | +1 646 876 9923,or +1 669 900 6833, Meeting ID: 344 520 180 |

