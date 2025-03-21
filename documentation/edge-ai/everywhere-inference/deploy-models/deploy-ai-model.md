---
title: deploy-ai-model
displayName: Deploy AI models in the Customer Portal
published: false
order: 10
toc:
    --1--Step 1. Select a model: "step-1-select-a-model"
    --1--Step 2. Select a flavor: "step-2-select-a-flavor"
    --1--Step 3. Set up routing placement: "step-3-set-up-routing-placement"
    --1--Step 4. Configure autoscaling: "step-4-configure-autoscaling"
    --1--Step 5 (Optional). Add environment variables: "step-5-optional-add-environment-variables"
    --1--Step 6 (Optional). Configure authentication via API keys: "step-6-optional-configure-authentication-via-api-keys"
    --1--Step 7. Specify pod lifetime: "step-7-specify-pod-lifetime"
    --1--Step 8. Enter deployment details: "step-8-enter-deployment-details"
    --1--Step 9. Finalize deployment: "step-9-finalize-deployment"
pageTitle: Deploy an AI model | Gcore
pageDescription: 'Learn how to deploy an AI model on Gcore Everywhere Inference: Upload your custom model or deploy from our model catalog.'
---
# Deploy AI models in the Customer Portal

With Gcore Everywhere Inference, you can use foundational open-source models from our AI model catalog or deploy a custom model by uploading a Docker container image.

## Step 1. Select a model

This step will slightly differ based on whether you choose to deploy a custom model or use a model from our catalog.

<tabset-element>

### Deploy model from the catalog

1\. In the Gcore Customer Portal, navigate to **Cloud** > **Everywhere Inference**.

2\. Open the **Overview** page.

3\. Click **Browse model catalog** to view the available AI models.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/overview-deploy-from-catalog.png" alt="Overview tab with model catalog and custom model sections" width="80%">

4\. Hover your cursor over the model you are interested in and click on the preferred model.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/model-catalog.png" alt="Model catalog tab" width="80%">

5\. Ensure that the correct model is selected. If not—select another one from the dropdown menu.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/select-model.png" alt="A dropdown with model versions" width="80%">

### Deploy a custom model

1\. In the Gcore Customer Portal, navigate to **Cloud** > **Everywhere Inference**.

2\. Open the **Overview** page.

3\. Click **Deploy custom model**.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/overview-deploy-custom-model.png" alt="Overview tab with model catalog and custom model sections" width="80%">

4\. In the **Registry** dropdown, select the storage location of your AI model.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/registry-dropdown.png" alt="Deploy a model dialog with highlighted registry section" width="80%">

If you need to add a new model registry, click **Add registry** and then configure it as follows:

* **Image registry name:** Registry name that will be displayed in the Registry dropdown.

* **Image registry URL:** Link to the location where your AI model is stored.

* **Image registry username:** Username you use to access the storage location of your AI model.

* **Image registry password:** Password you use to access the storage location of your AI model.

To save the new registry, click **Add**.

<alert-element type="info" title="Info">

The image with your AI model must be built for the x86-64(AMD64) architecture.

</alert-element>

5\. Enter the name of the image with your model. For example: `ghcr.io/namespace/image_name:tag` or `docker.io/username/model:tag`.

6\. Specify a port to which the containerized model will listen. The external port for accessing your deployment is always 443 (HTTPS).

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/image-name-port.png" alt="Image name and port sections" width="80%">

</tabset-element>

## Step 2. Select a flavor

This configuration determines the allocated number of resources (GPU/vCPU/RAM) for running your model. Ensure that you select sufficient resources. Otherwise, the model deployment might fail.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/select-flavor.png" alt="Flavor dropdown in the Pod configuration section" width="80%">

We recommended the following flavor parameters for models:

<table>
<thead>
  <tr>
    <th>Recommended flavor</th>
    <th>Billion parameters</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>1 × L40s 48 GB</td>
    <td>4.1–21</td>
  </tr>
    <tr>
    <td>2 × L40s 48 GB</td>
    <td>21.1–41</td>
  </tr>
      <tr>
    <td>4 × L40s 48 GB</td>
    <td>21.1–41</td>
  </tr>
</tbody>
</table>

## Step 3. Set up routing placement

Select the inference regions where the model will run from the list of available worldwide edge PoPs. The list of available PoPs depends on which pod configuration you selected in Step 2.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/routing-placement.png" alt="Regions dropdown in the Routing placement section" width="80%">

## Step 4. Configure autoscaling

You can set up autoscaling for all pods (**All selected regions**) or only for pods located in particular regions (**Custom**).

Specify the range of nodes you want to maintain:

* **Minimum pods**: The minimum number of pods that must be deployed during low-load periods.

* **Maximum pods**: The maximum number of pods that can be added during peak-load periods.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/autoscaling.png" alt="Autoscaling section" width="80%">

To ensure more efficient use of computational resources and consistent model performance, define scaling thresholds for GPU and CPU utilization.

Click **Advanced settings** to view and modify current thresholds:

* The minimum setting is 1% of the resource capacity.

* The maximum setting is 100% of the resource capacity.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/autoscaling-parameters.png" alt="Autoscaling parameters" width="80%">

By default, the autoscaling parameters are set to 80% but you can enter any percentage within the specified range.

## Step 5 (Optional). Add environment variables

If you want to add additional information to your model deployment, create variables for your container in the format of key-value pairs. These variables will only be used in the environment of the created container.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/env-variables.png" alt="Environment variables section" width="80%">

## Step 6 (Optional). Configure authentication via API keys

You can configure API authentication for your deployment by enabling API key authentication. To do this, turn on the **Enable API Key Authentication** toggle.

## Step 7. Specify pod lifetime

Specify the number of seconds after which a pod will be deleted when there are no requests to your pod. For example, if you enter 600, the pod will be deleted in 600 seconds, which is equal to ten minutes.

<alert-element type="info" title="Info">

If you specify 0, the container will take approximately one minute to scale down.

</alert-element>

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/pod-lifetime.png" alt="Pod lifetime section" width="80%">

## Step 8. Enter deployment details

Enter the deployment name and additional information if needed. This information will be displayed on the **Deployments** page under **Settings**.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/deployment-details.png" alt="Deployment details section" width="80%">

## Step 9. Finalize deployment

Scroll to the top of the page and click **Deploy** in the top-right corner of the screen.

<img src="https://assets.gcore.pro/docs/cloud/everywhere-inference/deploy-ai-model/click-deploy.png" alt="Your plan section with an active Deploy button" width="80%">
