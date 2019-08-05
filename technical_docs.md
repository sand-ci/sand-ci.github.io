---
title: "SAND Technical Documents"
collection: technical_docs
permalink: /technical-docs/
layout: collection
sort_order: reverse
sort_by: date
---

## Documentation

This page holds the detailed technical documentation for the SAND project; below, you will find
various archictural information, operational links, and FAQs.

## Software Products

* [ps-collector](https://github.com/sand-ci/ps-collector): Given a perfSONAR configuration mesh, the `ps-collector` queries perfSONAR instances and uploads their most recent test results to a RabbitMQ message bus.
* [ps-ingest](https://github.com/sand-ci/ps-ingest): Daemons that read data from the RabbitMQ message bus and uploads it into an ElasticSearch instance.
* [SAND Display](https://github.com/sand-ci/sand-display): The software the powers the Google maps-based visualization of the data in the SAND-NMA.

## Technical Documents

