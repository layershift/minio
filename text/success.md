Your [MinIO](https://docs.min.io/minio/baremetal/introduction/minio-overview.html) servers are currently at the latest version, and can be further updated in future [via the option in the Jelastic dashboard](https://github.com/layershift/minio#maintenance) or the [corresponding Minio Client command](https://docs.min.io/minio/baremetal/reference/minio-cli/minio-mc-admin/mc-admin-update.html).

Access your cluster using the details below:

MinIO endpoint: [https://${env.domain}]([https://${env.domain})
MinIO Console: [https://${env.domain}:9001](https://${env.domain}:9001)  

Both URLs are proxied via an Nginx load balancer, secured with an automatically renewing Let's Encrypt certificate.

Access Key / Username: ${settings.accessKey}  
Secret Key / Password: ${settings.secretKey}  

Please refer to [MinIO Identity and Access Management](https://docs.min.io/minio/baremetal/security/minio-identity-management/basic-authentication-with-minio-identity-provider.html) for guidance about user management.

The [MinIO Client](https://docs.min.io/minio/baremetal/reference/minio-cli/minio-mc.html) is already pre-installed as ``mcli`` on each of your MinIO servers, with a preconfigured alias of ``myminio`` - example command:

``mcli admin info myminio``

You can use any S3-compatible tool to access buckets hosted by your cluster, but the official MinIO Client (or MinIO Console) are recommended for administrative purposes.

Total available storage capacity depends on:
* Number of nodes in the cluster
* Disk quota per node
* [Storage class configuration](https://docs.min.io/minio/baremetal/concepts/erasure-coding.html#storage-classes)

Storage capacity cannot be readily increased for the existing cluster. Please create a new cluster with more nodes and migrate/replicate your objects if additional storage is required.

**IMPORTANT**: Review the [release notes](https://github.com/minio/minio/releases) before performing updates!