---
date: "2019-02-12"
title: "Backup and Recovery"
layout: single
toc: true
author: Derek Weitzel
sidebar:
  nav: "docs"
---

## Backup

## Recovery

This procedure has been tested from the GRACC frontend node (gracc.opensciencegrid.org).  Though, this procedure could be performed anywhere with the correct software and configuration installed.  There is nothing special about the gracc.opensciencegrid.org IP or hostname for this procedure.

### Software
- GRACC replayer from the [gracc archive](https://github.com/opensciencegrid/gracc-archive) package.
- `globus-url-copy` and/or `uberftp`.  It may be useful to use uberftp to `ls` the directory to pick correct file.  Though, the naming convention of the backup files may make the `ls` unnecessary.

### Configuration
- Certificate that FNAL tape trusts with access to the gracc backup directory `gsiftp://fndca1.fnal.gov/pnfs/fs/usr/fermigrid/gratia/gracc-ps-raw/`
- User credentials to the OSG message bus

### Steps
1. `ls` the backup directory:

        $ sudo -u gracc X509_USER_CERT=/etc/grid-security/backup-cert/gracc.opensciencegrid.org-cert.pem X509_USER_KEY=/etc/grid-security/backup-cert/gracc.opensciencegrid.org-key.pem uberftp -ls gsiftp://fndca1.fnal.gov/pnfs/fs/usr/fermigrid/gratia/gracc-ps-raw/
    
    Notice that the naming convention of the file is `<hostname>-<year>-<month>-<day>.tar.gz`.

2. Copy the file(s) somewhere using `globus-url-copy`:

        $ sudo -u gracc X509_USER_CERT=/etc/grid-security/backup-cert/gracc.opensciencegrid.org-cert.pem X509_USER_KEY=/etc/grid-security/backup-cert/gracc.opensciencegrid.org-key.pem globus-url-copy gsiftp://fndca1.fnal.gov/pnfs/fs/usr/fermigrid/gratia/gracc-ps-raw/gracc-hcc-gracc-fe1.unl.edu-2019-02-08.tar.gz file:///tmp/

3. Install gracc-archive in order to use the unarchiver:

        $ pip install git+https://github.com/opensciencegrid/gracc-archive

4. Run the unarchiver.  You will need the connection username, password parameters.

        $ graccunarchiver -p "amqps://username:password@clever-turkey.rmq.cloudamqp.com/osg-nma” osg.ps.raw /tmp/gracc-hcc-gracc-fe1.unl.edu-2019-02-08.tar.gz 

    Unfortunately, no feedback is given on the command line.


