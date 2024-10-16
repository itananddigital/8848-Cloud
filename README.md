# 8848-Cloud

8848 Cloud is a cloud-based platform similar to Frappe Cloud that allows users to host, manage, and scale their applications effortlessly. 

## Features

- **Effortless Deployment**: Deploy your applications quickly without worrying about infrastructure complexities.
- **Scalability**: Seamlessly scale your apps as your business grows, ensuring optimal performance at every stage.
- **Integrated Management**: Manage all your projects from a single dashboard, with real-time monitoring and control.
- **Secure Hosting**: Ensure that your applications are hosted securely, with advanced protection and regular updates.
- **Cost-Effective**: Enjoy cloud hosting with competitive pricing, tailored for businesses of all sizes.

## Getting Started

To get started with 8848 Cloud, follow these steps:

1. **Sign Up**: Create an account on our platform.
2. **Deploy**: Use the platform to deploy your applications in just a few clicks.
3. **Manage**: Access the dashboard to monitor and manage your apps, ensuring they run smoothly.

For more detailed Commands documentation, visit our [Wiki](https://github.com/itananddigital/8848-Cloud/blob/main/Commands.md).


## Procedure to Setup

### Prerequisites for Frappe Cloud Setup:

1. **Domain**  
   - Dedicated Domain and Subdomain
   - Setup Domain in Route 53 and update the Nameserver records in the main domain

2. **IAM User**  
   IAM user with the following permissions:
   - `AmazonEC2FullAccess`
   - `AmazonRoute53DomainsFullAccess`
   - `AmazonS3FullAccess`
   - `AmazonVPCFullAccess`
   - `AmazonSSMReadOnlyAccess`

### Architecture Overview:

     Cluster 1              +                              Cluster 2

Press Site {       }                         All the Servers (proxy, app, db, monitor, registry)


- **Cluster 1**  
  A new server is created where we install our main site for Frappe Press (e.g., cloud.8848digital.com).  
  Install Frappe and Press App on this site, and follow the setup process provided.

- **Cluster 2**  
  The following software packages should be installed on your computer:
  - Docker (Latest): Don’t forget to give Docker sudo access.
  - Certbot (Latest): Install the `dns-route53` plugin for Certbot:  
    `pip3 install certbot-dns-route53`

  Cluster 2 setup includes:
  - **App Server** (f)
  - **Database Server** (m)
  - **Proxy Server** (n)
  - **Log Server** (ElasticSearch) (e)
  - **Monitor Server** (Prometheus) (p)
  - **Registry** (r)

### Cluster 1 Setup Steps:

1. Create an EC2 Server and host your site.
2. Install Frappe and Press App on it.
3. Prepare AWS User Details and Permissions.
4. Prepare Domain Details and Route 53 Setup.
5. Install required dependencies and complete the setup.
6. Setup Cluster 2 using the Press site.

### Cluster 2 Setup Steps:

1. Press "Settings" and fill in all the details:  
   `{ .certbot, .webroot, .docker-builds }`
2. Setup Root Domain records by creating a root domain.
3. Generate TLS certificates.
4. Complete the Press Settings.
5. Set up virtual machines and server records for:
   - Proxy Server (n)
   - App Server (f)
   - Database Server (m)
   - Registry
   - Grafana and Prometheus (p)
   - ElasticSearch (e)

### Server Setup:

1. **Proxy Server**
2. **App Server**
3. **Database Server**
4. **Registry**
5. **Grafana and Prometheus**
6. **ElasticSearch**

### Create Release Group:

- **Apps:**
  - Frappe
  - Press
  - ERPNext
- **Dependencies:**
  - Docker
  - Certbot
  - Route-53 pip package

### Deploy Steps:

1. Create Deploy Candidate.
2. Build Bench and Deploy to Server.
3. Create your first site.

### Final Steps After Creating Your Press Site:

1. SSH into your server.
2. Ensure Docker is installed with all the required permissions.
3. Create a public key using:  
   `ssh-keygen -t rsa`  
   This will generate an `id_rsa` key.
4. Copy the public key and add it to the site under the SSH key list. This will assist in creating clusters, virtual machines, etc.
5. Install Certbot and the required plugin:  
   `pip3 install certbot-dns-route53`

### How to Create a Cluster:

1. After logging into your server, the first thing you need to do is create a public key using the command:  
   `ssh-keygen -t rsa`.

### How to Set Up a Root Domain:

1. Navigate to the Root Domain List via the AwesomeBar and create a new document.
2. Fill in the details as below:
   - **Name**: `<your-domain-name>`, e.g., cloud.8848digitalerp.com
   - **Default Cluster**: Default
   - **AWS Access Key ID**: Get from AWS Console
   - **AWS Secret Access Key**: Get from AWS Console

### How to Host Frappe Cloud (Frappe Press):

This will involve both **Cluster 1** and **Cluster 2**.

**Prerequisites:**

1. Choose a region and create an EC2 instance (e.g., `t2.large`) and attach an Elastic IP.
2. Install Frappe and Press V15.
3. Install necessary dependencies:
   - Docker with user permissions.
   - Certbot with Route 53: `sudo pip3 install certbot-dns-route53`.
4. Create a public key using `ssh-keygen -t rsa`.
5. Create directories inside `/home/ubuntu/`:
   - `.certbot`
   - `.certbot/webroot`
6. Create two more directories under the Frappe bench: `.clones`, `.docker-builds`.


## License

<br>


Open-Source Freelance Platform is Licensed under the <a href="./LICENSE">MIT License</a>. Please go through the License atleast once before contributing.

## Contact

For any queries or support, please feel free to reach out:

- **Email**: support@8848cloud.com
- **GitHub**: [https://github.com/itananddigital/8848-cloud](https://github.com/itananddigital/8848-cloud)

