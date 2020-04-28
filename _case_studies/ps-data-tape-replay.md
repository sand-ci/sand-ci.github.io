---
date: "2020-04-14"
title: "Tape replay of perfSONAR Data"
layout: single
toc: true
authors: [ John Thiltges, Derek Weitzel ]

author_profile: true
---

A replay of the collected perfSONAR was initiated due to three changes in the ingestion of the data:

1. The record ID was calculated using the python `hash()` function. The record id is used to identify and remove duplicate records. With Python 3.3, the `hash()` function changed to a secured version that was not predictable between runs. Therefore, any playback from tape would not be detected as duplicate.
1. The perfSONAR metrics include traceroute, a snapshot of the network path between two nodes. To allow the path to be easily identified, queried and reported in ElasticSearch, the path is hashed to a single value as the data is stored. The Python built-in `hash()` function was initially used. As with 1. the `hash()` function changed to a secured version that was not predictable between runs. This left our path data unusable to identify duplicate paths.
1. Three new attributes were added to the traceroute ingester.

We corrected the code to generate reproducible hashes. This fixed future metrics, but not the years of existing data. To correct existing data, we elected to replay the perfSonar metrics from tape backups onto the message bus, reprocessing them with the new code.

The messages were replayed onto the message bus, consumed by ElasticSearch instances at University of Chicago and University of Nebraska. The Chicago instance was much faster, backed by flash storage, while the Nebraska instance was backed by Ceph on HDDs which ingested the data at a lower rate.

Because the replay speed exceeded the ingest rate, we had to avoid overwhelming the message bus, causing data loss. We started with a simple delay: after sending a batch of 10,000 records, wait a few seconds. This worked well, but could still send too many messages if the ElasticSearch instances were unavailable or there was a surge of messages from other sources. Next, we used the RabbitMQ API to periodically check the number of messages on the bus. If the bus was too full, we delayed or stopped sending data. With the improved rate limiting, we were able to replay a month of data---300M records---in 4.5 days, without overwhelming the bus.
