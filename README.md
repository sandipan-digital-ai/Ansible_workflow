 ## Github Action Wokflow
 
 The GitHub action workflow allows to create custom workflow directly in the GitHub repository. This helps in running different tasks automatically based on the events. This also helps in CI/CD capabilities directly in the repository. The workflow has been created in the GitHub repository which receives the API call from the webserver and the actions defined in the workflow gets triggered followed with running of the Ansible Playbook. The structure and the content of the workflow and the Ansible playbook has been described in this document. The Github action are created for the below two scenarios:

Github action to intiate the demo with selected containers
Github action to delete the containers

# 7.2.1.	Github Action to Create Containers for Scenarios

The workflow is configured to start when a GitHub events occurs. The workflow has been created in GitHub repository as a YML file. The github action workflow files are created under “.github/”. The files are created in “.yaml” format.

The workflow file is defined by a YAML (.yaml) file in the /.github/workflows/ path in the repository. This definition contains the various steps and parameters that make up the workflow.

#### The github action workflow  contains the following section :

I.	Github VM creation
II.	Pre-requisites for running ansible k8s module
III.	Azure cluster setup along with secret keys
IV.	Ansible installation and execution of playbook
