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
    - label: "SAND Network Display"
      url: "https://display.sand-ci.org"
  caption: ""
excerpt: 'Combine, visualize, and analyze disparate network monitoring and service logging data'
intro: 
  - excerpt: 'Service Analysis and Network Diagnosis'
feature_row:
  - image_path: /images/sample_packet_loss.png
    alt: "Sample packet loss graph"
    title: "Packet Loss Tracking"
    excerpt: "Sample packet loss graph from the SAND archive"
    url:  https://atlas-kibana.mwt2.org/s/networking/app/kibana#/dashboard/07a03a80-beda-11e9-96c8-d543436ab024?_g=(filters%3A!()%2CrefreshInterval%3A(pause%3A!t%2Cvalue%3A0)%2Ctime%3A(from%3Anow-3d%2Cto%3Anow))
    btn_label: "View Dashboard"
    btn_class: "btn--primary"
  - image_path: /images/sample_throughput.png
    alt: "Sample TCP throughput graph"
    title: "Throughput Tracking"
    excerpt: "SAND's archives record historical single-stream TCP across many links"
    url:  https://atlas-kibana.mwt2.org/s/networking/app/kibana#/dashboard/ab7c4950-5cfa-11ea-bad0-ff3d06e7229e?_g=(filters%3A!()%2CrefreshInterval%3A(pause%3A!t%2Cvalue%3A0)%2Ctime%3A(from%3Anow-3d%2Cto%3Anow))
    btn_label: "View Dashboard"
    btn_class: "btn--primary"
  - image_path: /images/sample_traceroute_dashboard.png
    alt: "Traceroute Dashboard"
    title: "Traceroute Tracking"
    excerpt: "SAND's archives record historical traceroutes throughout many links"
    url: https://atlas-kibana.mwt2.org/s/networking/app/kibana#/dashboard/58121420-5e17-11ea-bad0-ff3d06e7229e?_g=(filters%3A!()%2CrefreshInterval%3A(pause%3A!t%2Cvalue%3A0)%2Ctime%3A(from%3Anow-3d%2Cto%3Anow))
    btn_label: "View Dashboard"
    btn_class: "btn--primary"
  - image_path: /images/sample_traceroute_explorer.png
    alt: "MEPHi TRACER (traceroute explorer)"
    title: "MEPHi TRACER"
    excerpt: "Interactive Traceroute explorer"
    url: https://perfsonar.uc.ssl-hep.org/
    btn_label: "Open App"
    btn_class: "btn--primary"
  - image_path: /images/ps-dash-sample.png
    alt: "PS-Dash App"
    title: "PS-Dash App"
    excerpt: "OSG-LHC/WLCG network metrics summary, ordered by most problematic sites first"
    url: https://ps-dash.uc.ssl-hep.org/
    btn_label: "Open App"
    btn_class: "btn--primary"
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

* SAND users: Engaged BNL (ATLAS), AGLT2 (ATLAS), MWT2 (ATLAS), UCSD (CMS), Nebraska (CMS), Wisconsin (CMS), MIT (CMS), and Purdue (CMS), all within the last year, to identify and resolve network issues
* Number of data sources: 236 distinct perfSONAR endpoints
* Number of HTCondor submit hosts reporting network measurements: 23
* Number of distinct measurements in the ElasticSearch database: over 10 billion, from February 28, 2018 to present

## Contact us

SAND has a weekly meeting for collaborators and project members:

| **When**   | Monday, 3:00–4:00 p.m. Central Time                         |
| **Online** | [https://unl.zoom.us/j/344520180](https://unl.zoom.us/j/344520180)                             |
| **Phone**  | +1 646 876 9923,or +1 669 900 6833, Meeting ID: 344 520 180 |

Additionally, we can be reached via our [public Google Group](https://groups.google.com/a/sand-ci.org/forum/#!forum/discuss).

