# pipelineStatus

## Pipeline Requirements

The PipelineStatus pipeline requires the following parameters to be defined:
### Parameters:


| Name  | type | Default | Values | Opional/Required | Comments |
| :------------- | :-------------: | :------------- | :-------------: | :-------------: | :------------- |
| pipelineId | String | | | Required | This enables passing of Pipeline ID as a variable |
| resultFilter | String | succeeded | | Required | |
| buildNumber | String | | | Optional | |
| outputVariablePrefix | String |  | | Required | |
| pipelineDisplayName | String | | | Required | This enables to use different display name for the pipeline |
| executeCondition | Boolean | true | | Required | |
| publishStepName | String | | | Required | This enables to use step name for the publishPipelineStatus.yml template |
| publishStepDisplayName | String | | | Required | This enables to use different display name for the publishPipelineStatus.yml template |

  These parameters provide multiple use case options for the PipelineStatus framework templates pipeline, executeCondition flag is used for the utilization of different templates as per the requirements.


## Use Cases


### 1. Publishing "pipelinestatus" as output (Output variable "BuilSummary" to be used in another dependent template)

You can use the "output variable" of this template as per the requirement. for example: 

```yaml

    # azure-pipeline.yaml
    resources:
    repositories:
    - repository: Template
        type: github
        name:  your_username/Repo_name
        ref: <respective branch name>
        endpoint: 'githubServiceConnectioNname'


    steps:
    - template: templates/publishPipelineStatus.yml@Template
        parameters:
        BuildSummary: $buildSummary
        pipelineId: $(pipeline.publishAndDeployClaimsPipelineId)
        publishStepName: SetPublishAndDeployPartyPipelineStatus
        publishStepDisplayName: 'Set Publish And Deploy Party Pipeline Status'


```

The parameters are provided to configure the pipelineStatus pipeline according to the desired build configuration and stages.

Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.


