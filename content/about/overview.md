---
title: "Overview"
author: "The ClusterCockpit Project"
image: "images/cc-arch.png"
---
ClusterCockpit consists of:
* the web user interface and API backend [cc-backend](https://github.com/ClusterCockpit/cc-backend)
* the node agent [cc-metric-collector](https://github.com/ClusterCockpit/cc-metric-collector)
* and the in-memory metric cache [cc-metric-store](https://github.com/ClusterCockpit/cc-metric-collector)

All components can also be used individually.\n

Node metrics are collected continuously and sent to the metrics store at
fixed intervals. Job details are provided by an external adapter for the
batch job scheduler and sent to cc-backend via a REST API. For running
jobs, cc-backend queries the metrics store to collect all required time
series data. Once a job is finished, it is persisted to a JSON file-based
job archive that contains all job metadata and metrics data. Finished jobs
are loaded from the job archive. The metrics store uses cyclic buffers and
stores data only for a limited period of time.
