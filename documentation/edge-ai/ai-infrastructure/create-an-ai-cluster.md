---
title: create-an-ai-cluster
displayName: Create an AI Cluster
published: true
order: 20
pageTitle: Create an AI Cluster | Gcore
pageDescription: Learn how to create an AI cluster using Gcore's Cloud GPU infrastructure. Follow the step-by-step guide to set up your cluster and start using it.
---
# Create an AI cluster

1\. In the <a href="https://accounts.gcore.com/reports/dashboard" target="_blank">Gcore Customer Portal</a>, open the **GPU cloud** page. You'll be taken to the page for AI cluster creation.

<img src="https://assets.gcore.pro/docs/gpu-cloud/gpu-cloud-page-lux.png" alt="Create an AI Cluster" width="80%">

2\. Select a region, which is a physical location of the data center. For example, if you choose Helsinki, your cluster will be deployed on servers in Helsinki.

3\. Choose the flavor with relevant cluster configuration and allocated resources:

 * The GPU number means the number of GPU cards allocated per server. 

 * 2x Intel Xeon 8480+ is the type of processor that powers the servers within your cluster. 

 * The amount of RAM specifies the total memory available for processing data. 

 * NVMe size indicates the total solid-state storage capacity available within each server in the cluster. 

 * 8 x 400G Infiniband refers to the number and speed of Infiniband connections within the cluster. 

4\. Select the OS <a href="https://gcore.com/docs/cloud/images/about-images" target="_blank">image</a> on which your model will be running.

<img src="https://assets.gcore.pro/docs/gpu-cloud/image-settings.png" alt="Create an AI Cluster image settings" width="80%">

5\. Set up a <a href="ps://gcore.com/docs/cloud/networking/create-and-manage-a-network" target="_blank">network interface</a>. You can choose a public or private one:
* **Public**: Attach this interface if you are planning to use the GPU Cloud with servers hosted outside of Gcore Cloud. Your cluster will be accessible from external networks.

* **Private**: If you want to use the service with Gcore servers only. Your cluster will be available only for internal networks.  
  Select one of the existing networks or create a new one to attach it to your server.

6\. (Optional) If you want to assign a reserved IP address to your server, turn on the **Use reserved IP** toggle and select one. For more details, refer to the article <a href="https://gcore.com/docs/cloud/networking/ip-address/create-and-configure-a-reserved-ip-address">Create and configure a reserved IP address</a>.   
  
7\. Turn on the **Use floating IP** toggle if you want to use a floating IP address. It’ll make your server accessible from outside networks even if they have only a private interface. Create a new IP address or choose an existing one. For more details, check out the article <a href="https://gcore.com/docs/cloud/networking/ip-address/create-and-configure-a-floating-ip-address">Create and configure a floating IP address</a>.

<img src="https://assets.gcore.pro/docs/gpu-cloud/network-settings.png" alt="Create an AI Cluster network settings" width="80%">

8\. (Optional) If you need several network interfaces, click **Add Interface** and repeat the instructions from Step 5.

9\. Select one of your SSH keys from the list, add a new key, or generate a key pair. You'll use this SSH key to connect to your cluster.

<img src="https://assets.gcore.pro/docs/gpu-cloud/create-ai-cluster-ssh-key.png" alt="Create an AI Cluster ssh key settings" width="80%">

10\. (Optional) To add metadata to your cluster, enable the **Additional options** toggle and add tags as key-value pairs.

11\. Name your cluster and click **Create Cluster**.

<img src="https://assets.gcore.pro/docs/gpu-cloud/create-ai-cluster-tags-name.png" alt="Create an AI Cluster tag and name settings" width="80%">

You’ve successfully created the cluster. Use the IP address of your AI Cluster and the SSH key from Step 10 and connect to your server.

User login: ```ubuntu```

Connection port: ```22```
