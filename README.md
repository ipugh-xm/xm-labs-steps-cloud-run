# Google Cloud Run Steps

This step allows you to manage traffic of a Google Cloud Run service.


---------

<kbd>
  <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</kbd>

---------

# Files

* [CloudRunSteps.zip](CloudRunSteps.zip) - Workflow zip file with the step and example flow
* [cloudrun.png](/cloudrun.png) - Google Cloud Run logo

# How it works
This step runs on the xMatters agent on a Google Cloud Compute instance and uses the gcloud command line tools. If an invalid revision is requested it will fail after a two minute timeout. If this is not enough, it can be adjusted in the step code.


# Installation

## Google Cloud Run Setup
In order for xMatters to properly authenticate with Google Cloud Run, the xMatters agent needs to be running somewhere that it can run gcloud commands. We've found that a compute instance with full Cloud API access scopes (currently there are no specific settings for Cloud Run access) is suitable for this. We would recommend using a service account on this compute instance that has the minimal access to services.

Also a Cloud Run service is required for this step to be effective.

## xMatters Setup
1. Download the [CloudRunSteps.zip](CloudRunSteps.zip) file onto your local computer
2. Navigate to the Workflows tab of your xMatters instance
3. Click Import, and select the zip file you just downloaded
4. Select the agent for the **Cloud Run - Manage Traffic** step to run on.


## Usage
The **Cloud Run - Manage Traffic** step is now available in your custom steps. So navigate to the appropriate canvas so you can add the step there. If you'd like to experiment with it, the **Manage Traffic** workflow has a canvas that can be triggered via HTTP call. 

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| Service Name | Yes | 0 | 2000 | Name of service to manage traffic. | | No |
| Revision Name | No | 0 | 2000 | Revision to move traffic to. By default, will move traffic to previous revision. | | No |
| Region | Yes | 0 | 2000 | Region where your service is located. Options can be found [here](https://cloud.google.com/run/docs/locations). | | No |


### Outputs

| Name | Description |
| ---- | ----------  |
| json | Raw json output from changing traffic. |
| success | (true) or (false) depending on if traffic redirection succeeded. |


## Example
This is an image of the included example flow.

<kbd>
	<img src="/media/ExampleFlow.png">
</kbd>

