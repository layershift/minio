# MinIO Cluster

The **MinIO Cluster** solution by Layershift automates creation of a scalable and cost-efficient object storage cluster, which is fully compatible with Amazon S3 (_Simple Storage Service_). The package utilises [MinIO](https://www.minio.io/) microstorage architecture to interconnect a number of separate Docker containers distributed across separate physical hardware to create a reliable cluster, load balanced behind an Nginx proxy node.

MinIO divides objects into chunks and evenly distributes them among containers in an Erasure Set, protecting against silent data corruption (bitrot). By [adjusting the Storage Class](https://docs.min.io/minio/baremetal/concepts/erasure-coding.html#storage-classes), you can balance the level of redundancy against storage efficiency.

It can be accessed via S3 compatible APIs and the [MinFS fuse driver](https://github.com/minio/minfs).

![MinIO S3 Cluster](images/minio-s3-cluster.png)

## MinIO Cluster Installation

[![Deploy](images/getithosted.png)](https://app.j.layershift.co.uk/?manifest=https://raw.githubusercontent.com/layershift/minio/master/manifest.jps)

Or, log into your Layershift Jelastic account and [import](https://docs.jelastic.com/environment-import) the [manifest.jps](manifest.jps).

## Capacity / Number of cluster nodes

Note that number of nodes cannot be modified later, so to avoid having to create a new cluster and migrate to it, it's better to plan ahead based on your capacity requirements.

Raw capacity of your MinIO cluster depends on the maximum storage capacity allowed per node (generally 200GB) times the number of nodes you select for your MinIO cluster. However the usable capacity and efficiency of the cluster does depend on other factors as well. Please see the below table for the usable capacity, efficiency and failure tolerance depending on the number of nodes you select.

| Number of cluster nodes | Usable Capacity | Raw Capacity | Storage Efficiency | Server Failure Tolerance                 |
|:-----------------------:|:---------------:|:------------:|:------------------:|------------------------------------------|
|                       4 | 400GB           | 800GB        | 50%                | 1 server in total                        |
|                       6 | 600GB           | 1.2TB        | 50%                | 2 servers in total                       |
|                       8 | 800GB           | 1.6TB        | 50%                | 3 servers in total                       |
|                      10 | 1TB             | 2TB          | 50%                | 2 servers in total                       |
|                      12 | 1.2TB           | 2.4TB        | 50%                | 5 servers in total                       |
|                      14 | 1.4TB           | 2.8TB        | 50%                | 6 servers in total                       |
|                      16 | 2.4TB           | 3.2TB        | 75%                | 4 servers in total (4 out of 16 servers) |
|                      18 | 2TB             | 3.6TB        | 55%                | 8 servers in total (4 out of 9 servers)  |
|                      20 | 2.4TB           | 4TB          | 60%                | 8 servers in total (4 out of 10 servers) |
|                      22 | 2.8TB           | 4.4TB        | 63%                | 8 servers in total (4 out of 11 servers) |
|                      24 | 3.2TB           | 4.8TB        | 66%                | 8 servers in total (4 out of 12 servers) |
|                      26 | 360TB           | 5.2TB        | 69%                | 8 servers in total (4 out of 13 servers) |
|                      28 | 4TB             | 5.6TB        | 71%                | 8 servers in total (4 out of 14 servers) |
|                      30 | 4.4TB           | 6TB          | 73%                | 8 servers in total (4 out of 15 servers) |
|                      32 | 4.8TB           | 6.4TB        | 75%                | 8 servers in total (4 out of 16 servers) |


## Maintenance

MinIO and MinIO Client can be updated from the Jelastic dashboard.

![MinIO Server Addons button](images/minio-addons.png)

![MinIO Cluster Management panel](images/minio-cluster-management.png)

**IMPORTANT**
* Please consult the [MinIO Release Notes](https://github.com/minio/minio/releases) to be aware of any breaking changes
* The update affects all MinIO servers at the same time, so please plan for a period of downtime.
