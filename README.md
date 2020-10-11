# Github Issues to Azure Devops Work Items migration script

A simple script to migrate GitHub Issues to Azure Devops Work Items via the Devops Web API.

To be run from the command line using your PHP binary.

## What GitHub Issue data is migrated

* Work Item Type (User Story default and Bug if label Bug is present)
* Title
* Description
* Comments
* State
* Tags
* Milestones (as Tag)
* AssignedTo
* CreatedBy
* CreatedAt

In addition a reference to the old GitHub issue will be placed inside the Azure Devops Work Item description.

Also, you are optionally able to specify a list of GitHub user to Azure Devops email mappings.

Make sure that the target Azure Devops Team and and Area Path exist for the matching to work properly. 

## Mandatory arguments

* --import input file, relative to this file. See below for the required format of this file
* --pat GitHub PAT with at least "repo" access
* --version DevOps API version, e.g. "6.0-preview.3"
* --organization DevOps organization, e.g. "my-org"
* --project DevOps project, e.g. "Your Project"
* --team DevOps project team, e.g. "My-Team"
* --verbose Whether to display debug logs

## Optional settings

* list of user mappings in case you want don't want to use the user specified in the original GitHub issue
  See getUser()

## Additional notes

The input file specified must be compliant to the format generated by the githubCsvTools
@see https://github.com/gavinr/github-csv-tools
