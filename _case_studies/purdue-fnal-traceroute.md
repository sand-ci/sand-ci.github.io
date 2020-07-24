---
date: "2020-07-24"
title: "Topology Exploration: Purdue"
layout: single
toc: true
author: Shawn McKee
author_profile: true
---

We have been using our dashboards, as well as the MEPHI 3D traceroute visualization tool, to explore our network topology information. As we explored, we have uncovered some interesting network topologies, both in IPv4 and IPv6.

In this example, we will show the interesting topology discovered between Purdue and a number of sites and then drill down on the path from Purdue to FNAL. Geographically, Purdue is not that far from FNAL but the routing we find is very interesting and will need further examination by the Purdue networking team.

{% comment %} 
In the video below we demonstrate how to start investigating the networking topology we are gathering via our regular perfSONAR traceroute measurements.
{% endcomment %}

You can start with our [Traceroute dashboard](https://atlas-kibana.mwt2.org/s/networking/app/kibana#/dashboard/58121420-5e17-11ea-bad0-ff3d06e7229e) which provides statistics and visualizations of the traceroute metrics we are gathering.

![Traceroute dashboard](image1.png)

Near the top is a Navigation box that will let you get to other resources. We can select the [SAND Toolkit Info](https://toolkitinfo.opensciencegrid.org/) link, taking us to our "information router" for SAND/OSG/WLCG information:

![SAND Toolkit Info](image2.png)

The "Analytics and Dashboards" menu can take us to [TRACER](https://perfsonar.uc.ssl-hep.org/), the MEPHI 3D traceroute visualization tool.

{% comment %} 
The video below shows how you can use this tool to visualize the perfSONAR traceroute data we are gathering.
<INSERT VIDEO>
{% endcomment %}

![Purdue traceroute](image3.png)

As you can see, the traceroute information between Purdue and many other sites--in both IPv4 and IPv6--shows a large number of paths. While this is not necessarily a problem, it deserves some examination to ensure Purdue's routing is really optimal.  The large number of paths to research partners may not be taking advantage of other R&E network paths that might be more stable or shorter.

Shown above are the IPv4 and IPv6 routes from Purdue (pink circles) to FNAL (blue circles).   You can see two distinct sets of paths.  Those on the right are IPv6 while the large number of paths on the left are IPv4.  The large number of IPv4 paths deserves investigation.