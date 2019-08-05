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
    url: https://atlas-kibana.mwt2.org/s/networking/app/kibana#/dashboard/perfSONAR
  - image_path: /images/sample_throughput.png
    alt: "Sample TCP throughput graph"
    title: "Throughput Tracking"
    excerpt: "SAND's archives record historical single-stream TCP throughout across many links"
  - image_path: /images/sample_data_collection.png
    alt: "Sample Data Collection Rates"
    title: "Running Data Collection Queries"
    excerpt: "SAND continuously queries participating perfSONAR endpoints to pull their data into the archive"
    url: https://gracc.opensciencegrid.org/dashboard/db/perfsonar-collector?orgId=1
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

SAND maintains a map of CC\* sites running perfSONAR; to allow your site to show up, [follow these directions](join-community).

{% include feature_row %}

## SAND Network Monitoring Archive

The SAND-NMA aims to aggregate as much network monitoring tests results as feasible, providing a
knowledgebase for debugging networks and performing data analytics.  This archive consists of
a data collector (polling measurement endpoints), a message bus (which endpoints can also push
data into directly), an archive, and a visualization platform, as pictured here:

<div class="notice">
  <h4>SAND-NMA Architecture</h4>
  <img class="card-img-bottom" src="/images/SAND-Architecture1.png" alt="SAND-NMA Architecture"/>
</div>

Currently, we are recording network measurements from perfSONAR and
[HTCondor file transfer](https://opensciencegrid.org/docs/other/schedd-filebeats/); we plan to
extend this to XRootD services during 2020.

A few metrics about our service:

* SAND users: SAND is utilized by US ATLAS and US CMS to help debug their network performance.
* Number of unique data sources: 274
* Number of HTCondor submit hosts reporting network measurements: 23
* Number of distinct measurements in the ElasticSearch database: over 2.3 billion

## Contact us

SAND has a weekly meeting for collaborators and project members:

| **When**   | Monday, 3:00–4:00 p.m. Central Time                         |
| **Online** | [https://unl.zoom.us/j/344520180](https://unl.zoom.us/j/344520180)                             |
| **Phone**  | +1 646 876 9923,or +1 669 900 6833, Meeting ID: 344 520 180 |

Additionally, we can be reached via our [public Google Group](https://groups.google.com/a/sand-ci.org/forum/#!forum/discuss).

