Your [MinIO](https://docs.min.io/minio/baremetal/introduction/minio-overview.html) cluster has been successfully deployed and updated to the latest version. 

Please find access details below:

MinIO endpoint: [https://${env.domain}/]([https://${env.domain}/])
MinIO Console: [https://${env.domain}:9001](https://${env.domain}:9001)  

Both URLs are proxied via an Nginx load balancer, secured with an automatically renewing Let's Encrypt certificate.

Access Key / Username: ${globals.accessKey}  
Secret Key / Password: ${globals.secretKey}  

Please refer to [MinIO Identity and Access Management](https://docs.min.io/minio/baremetal/security/minio-identity-management/basic-authentication-with-minio-identity-provider.html) for guidance about user management.

The [MinIO Client](https://docs.min.io/minio/baremetal/reference/minio-cli/minio-mc.html) is already pre-installed as ``mcli`` on each of your MinIO servers, with a preconfigured alias of ``myminio`` - example command:

``mcli admin info myminio``

You can use any S3-compatible tool to access buckets hosted by your cluster, but the official MinIO Client (or MinIO Console) are recommended for administrative purposes.