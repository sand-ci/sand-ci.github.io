---
date: "2020-03-24"
title: "Firewall Issue at University of Waterloo"
layout: single
toc: true
author: Shawn McKee
author_profile: true
---

While developing user dashboards for the [SAND project](https://sand-ci-org), we identified a significant issue with all perfSONAR testing to the University of Waterloo. You can see our [dashboard for March 10-13, 2020](https://atlas-kibana.mwt2.org/s/networking/app/kibana#/dashboard/07a03a80-beda-11e9-96c8-d543436ab024?_g=(filters:!(),refreshInterval:(pause:!t,value:0),time:(from:'2020-03-10T15:52:03.335Z',to:'2020-03-12T15:52:15.032Z'))&_a=(description:'Visualizations+and+metrics+for+measurement+of+packet+loss+from+the+OSG%2FWLCG+perfSONAR+network+monitoring+infrastructure.',filters:!(),fullScreenMode:!f,options:(darkTheme:!f,hidePanelTitles:!f,useMargins:!t),panels:!((embeddableConfig:(),gridData:(h:15,i:'7',w:48,x:0,y:9),id:'84af4350-bed9-11e9-96c8-d543436ab024',panelIndex:'7',type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:9,i:'9c7080a9-dabe-44e0-82ac-116842f92504',w:24,x:0,y:0),id:'956e5d20-5d7b-11ea-bad0-ff3d06e7229e',panelIndex:'9c7080a9-dabe-44e0-82ac-116842f92504',type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:9,i:'04c1a17f-1835-475a-b7c8-8ea5b050e037',w:24,x:24,y:0),id:'31516580-5d7b-11ea-bad0-ff3d06e7229e',panelIndex:'04c1a17f-1835-475a-b7c8-8ea5b050e037',type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:15,i:'1626e956-d4ba-4114-b772-d3ee57382bfb',w:24,x:0,y:24),id:ede40840-58b9-11ea-bad0-ff3d06e7229e,panelIndex:'1626e956-d4ba-4114-b772-d3ee57382bfb',type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:15,i:cc66d5f6-0034-4a28-9514-880f5d16ebc5,w:24,x:24,y:24),id:'01dec770-58df-11ea-bad0-ff3d06e7229e',panelIndex:cc66d5f6-0034-4a28-9514-880f5d16ebc5,type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:15,i:'545b2e51-6a50-4a68-95ab-136ac5d47055',w:24,x:0,y:39),id:d7dd3560-57e4-11ea-bad0-ff3d06e7229e,panelIndex:'545b2e51-6a50-4a68-95ab-136ac5d47055',type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:15,i:'9bafba08-4f89-4a07-a197-063b79d55900',w:24,x:24,y:39),id:ceb10bc0-57e8-11ea-bad0-ff3d06e7229e,panelIndex:'9bafba08-4f89-4a07-a197-063b79d55900',type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:15,i:'4dca9b83-e83b-4ccf-b242-e2113a141f34',w:24,x:0,y:54),id:'7ca32540-4d06-11e9-9a8d-07fa5dee6891',panelIndex:'4dca9b83-e83b-4ccf-b242-e2113a141f34',type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:15,i:e2ac0c7a-5546-495c-ae01-518178fced71,w:24,x:24,y:54),id:ccb29920-57e7-11ea-bad0-ff3d06e7229e,panelIndex:e2ac0c7a-5546-495c-ae01-518178fced71,type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:15,i:ef540c54-b0ba-4a24-82f1-d392b0f31ffc,w:24,x:0,y:69),id:e7cb34d0-57db-11ea-bad0-ff3d06e7229e,panelIndex:ef540c54-b0ba-4a24-82f1-d392b0f31ffc,type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:15,i:db48d06d-9228-4afd-bed7-503af2b5b9ce,w:24,x:24,y:69),id:'142afdb0-57cf-11ea-bad0-ff3d06e7229e',panelIndex:db48d06d-9228-4afd-bed7-503af2b5b9ce,type:visualization,version:'7.5.2'),(embeddableConfig:(),gridData:(h:18,i:'761e4f7b-e77e-4aa8-ab7d-d86bf9c478b6',w:48,x:0,y:84),id:d33b9860-5c87-11ea-bad0-ff3d06e7229e,panelIndex:'761e4f7b-e77e-4aa8-ab7d-d86bf9c478b6',type:visualization,version:'7.5.2')),query:(language:lucene,query:''),timeRestore:!f,title:'Overview+of++Packet+Loss+in+OSG%2FWLCG',viewMode:view)).

This plot that caught our attention:
![Worst Average Packet Loss](image1.png)

The top "Worst Packet Loss" as a destination was lcg-pslat.uw.computecanada.ca (see ordered legend on the right), a perfSONAR latency instance at the University of Waterloo.

We can easily use this Kibana dashboard to focus on this site as a destination. If we click on the lcg-pslat in the legend we see:

![Worst Average Packet Loss with magnifying glass highlighted](image2.png)

If we click the magnifying glass icon with the `+` in it, we apply a filter to the whole dashboard, requiring that lcg-pslat.uw.computecanada.ca be the destination for any visualizations shown. You can try it yourself by using the above link.

Once this filter is in place we can see that every latency test (packet-loss test) destined to this University of Waterloo node is seeing 100% packet loss, except for one instance ( perfsonar02-iep-grid.saske.sk) which had some packets get through. The table at the bottom of the Packet-Loss dashboard can be used to see this:

![Path Packet-loss Table](image3.png)

As shown above, another feature of the visualizations in our dashboard is an "information" icon (circle around an `i`). If you hover over it, you will see text describing the details of each visualization. The "Average Packet Loss Fraction" (last) column, shows 1 for measurements that have 100% packet loss. We can also see this by looking at the packet-loss vs time graph for the period of March 10-13, 2020:

![Packet Loss Measurement Results vs Time](image4.png)

We contacted Rolf Seuster, who is the Compute Canada perfSONAR contact (as well as the Canadian ATLAS perfSONAR contact), notifying him of the issue. By March 16, they were able to debug the cause: misconfigured firewall at the University of Waterloo. This plot shows the fix going into place (period is March 13-18, 2020):

![Packet Loss Measurement Results vs Time, after fix](image5.png)

We are continuing to evaluate the various visualizations, with a focus on highlighting significant issues in both our network monitoring infrastructure and our R&E networks themselves.
