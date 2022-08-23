# Create a deployment pipeline
You can create a pipeline from the deployment pipelines tab, or from a workspace.

## Create a pipeline from the deployment pipelines tab

To create a pipeline from the deployment pipelines tab, do the following:

1. In Power BI service, from the navigation pane, select **Deployment pipelines** and then select **Create pipeline**.

2. In the *Create a deployment pipeline* dialog box, enter a name and description for the pipeline, and select **Create.**


## Create a pipeline from a workspace
You can create a pipeline from an existing workspace, providing you're the admin of a workspace.

1. From the workspace, select **Create a pipeline.**
2. In the Create a deployment pipeline dialog box, enter a name and description for the pipeline, and select Create.

## Assign a workspace
To assign a workspace to a pipeline stage, follow these steps:
1. Open the pipeline.
2. In the stage you want to assign a workspace to, expand the dropdown titled Choose a workspace to assign to this pipeline.
3. From the dropdown menu, select the workspace you want to assign to this stage.
4. Select Assign a workspace.

## Deploy to an empty stage
Any Pro user that's a member or admin in the source workspace, can deploy content to an empty stage (a stage that doesn't contain content). The workspace must reside on a capacity for the deployment to be completed.

### Deploying all content
Select the stage to deploy from and then select the deployment button. The deployment process creates a duplicate workspace in the target stage. This workspace includes all the content existing in the current stage.

## Selective deployment
To deploy only specific items, select the Show more link, and then select the items you wish to deploy. When clicking the deploy button, only the selected items are deployed to the next stage.


# Deploying Reports with Pipelines

In this lab you will use your own initiative to connect to the demo capacity, create three pipelines. Promote some demo content through the pipelines to mimic a release

This link will help you https://docs.microsoft.com/en-us/power-bi/create-reports/deployment-pipelines-get-started

## Create deployment rules
You can create the deployment rules by following these steps
1. In the pipeline stage you want to create a deployment rule for, select Deployment settings.
2. You can set rules to dataflows, datasets, datamarts and paginated reports. In the Deployment settings pane, select the type of rule you want to set.
3. Select the dataflow, dataset or paginated report you want to create a rule for.
4. Select the type of rule you want to create, expand the list, and then select Add rule. 

## Deploy content from one stage to another

Once you have content in a pipeline stage, you can deploy it to the next stage. Deploying content to another stage is usually done after you've performed some actions in the pipeline. 


To deploy content to the next stage in the deployment pipeline, select the deploy button at the bottom of the stage.

## Comparing stages

To allow a quick visual insight into the differences between two sequential stages, a comparison icon indicator appears between them. The comparison indicator has two states:

- Green indicator – The metadata for each content item in both stages, is the same.
- Orange indicator - Appears if one of these conditions is met:
  - Some of the content items in each stage, were changed or updated (have different metadata).
  - There is a difference in the number of items between the stages.
