---
date: "2020-07-24"
title: "Identifying and Investigating Significant Packet Loss from Univ. of Wisconsin"
layout: single
toc: true
author: Shawn McKee
author_profile: true
---

Once we had draft versions of our new dashboards we wanted to explore the top issues being identified. In our experience, packet-loss is usually a primary indicator of poor network performance because of its impact on TCP, especially for long, fat network pipes. On our [packet-loss dashboard](https://atlas-kibana.mwt2.org/s/networking/app/kibana#/dashboard/07a03a80-beda-11e9-96c8-d543436ab024?_g=(filters%3A!()%2CrefreshInterval%3A(pause%3A!t%2Cvalue%3A0)%2Ctime%3A(from%3Anow-1d%2Cto%3Anow))) we have a "Worst Average Packet Loss (Src Host) Dashboard" showing the 10 worst "sources" for packet-loss in our data. The top-most problematic host was perfsonar01.hep.wisc.edu, the latency measurement host for the USCMS Tier-2 center at the University of Wisconsin.  

![Graph of top hosts for TCP packet loss, showing high sustained packet loss for the latency measurement host at Wisconsin](image1.png)

Our assumption was the transfers from Wisconsin to other sites should be suffering and we wanted to use the data we had to confirm this.

By selecting the `perfsonar01.hep.wisc.edu` item in the legend on the above visualization, we are able to set up a filter requiring the source to be perfsonar01. Doing this updates all the other visualizations on the dashboard with that requirement, allowing us to see results specific to when the Wisconsin host is the source of latency tests.

One interesting item was the "Path Packet-loss Table" at the bottom of the dashboard

![Path Packet-loss table showing high loss from Wisconsin to IPv6 destinations](image2.png)

This shows the top loss measurements and we noticed that all the top loss measurements were IPv6 results. We then added a filter to require IPv4 and we get a new packet-loss line graph:

![Path Packet-loss table showing very little IPv4 loss from Wisconsin](image3.png)

This shows at least a factor of 30 less packet-loss for perfsonar01 than our original graph.

At this point we have identified significant outbound packet-loss in the perfSONAR IPv6 latency testing from Wisconsin. Our assumption was that this should be having a significant impact on Wisconsin’s ability to move data to other sites via IPv6. To investigate, we looked for the throughput measurements results from Wisconsin but transfer rates to IPv6 sites, even in Europe, had reasonable values and were not  severely affected.

Whatever the problem was it seems to have cleared up by May 1, 2020 as shown in the plot below. This plot filtered on the Wisconsin perfSONAR latency node as the source using IPv6.

![Packet-loss chart showing a sudden improvement on May 1, 2020](image4.png)

Checking the destinations:

![Packet-loss chart showing improvement on May 1, 2020 for metrics from Wisconsin to all other destinations](image5.png)

We see it was affecting ALL destinations, and whatever change by May 1, addressed the problem.

Our conclusion is that this problem was most likely local to the perfSONAR latency node, perhaps the first device or port it connected to. We are working with the Wisconsin team to understand what might have been changed/updated/replaced around April 30, 2020.
