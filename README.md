# 7.2.	Github Action Wokflow

The GitHub action workflow allows to create custom workflow directly in the GitHub repository. This helps in running different tasks automatically based on the events. This also helps in CI/CD capabilities directly in the repository.
The workflow has been created in the GitHub repository which receives the API call from the webserver and the actions defined in the workflow gets triggered followed with running of the Ansible Playbook. The structure and the content of the workflow and the Ansible playbook has been described in this document. The Github action are created for the below two scenarios:
1.	Github action to intiate the demo with selected containers
2.	Github action to delete the containers 


## 7.2.1.	Github Action to Create Containers for Scenarios

The workflow is configured to start when a GitHub events occurs. The workflow has been created in GitHub repository as a YML file. The github action workflow files are created under “.github/”. The files are created in “.yaml” format. 

The workflow file is defined by a YAML (.yaml) file in the /.github/workflows/ path in the repository. This definition contains the various steps and parameters that make up the workflow.

####The github action workflow  contains the following section :

I. Github VM creation
II. Pre-requisites for running ansible k8s module
III. Azure cluster setup along with secret keys
IV. Ansible installation and execution of playbook

##### Step1: Github VM creation

The event payload from the Java REST API is named ‘demo_k8s_tools’. The ‘On' keyword means, a certain event to trigger the workflow , to start, “repository_dispatch” is the workflow that is getting triggered in this case.'
The github action is run on a ubuntu VM. The “run” command is used to retrieve the value passed from the UI, which prints the user input from the tools selected from the UI as toollist and the demo number as namespace.

##### Step2: Pre-requisites for Ansible K8s module

Here, under the “Uses” keyword, we are importing a module called “actions/checkout@v1”, which installs the prerequisite package to run the ansible k8s module. The packages are 
• openshift >=0.6
• PyYAML >= 3.11

##### Refer to the link for the latest information :

##### https://docs.ansible.com/ansible/latest/collections/community/kubernetes/k8s_module.html

##### Step3: Azure Cluster Setup with Secret keys

The AKS configuration is integrated on the Github VM to run the connection with authentication and install the required libraries to run the commands. The username and passwords are saved under Github  Settings>Secrets><name>

##### Step 4: Ansible Installation and execution of the playbook

In this step ansible is installed in the github VM and executes the playbook  ‘create_demo_tools’with toolist and namespace passed as variables as extra vars.


## Github Action Checking:-

  ###### 1. 	After the play book is run successfully, the window with build with ticks on steps is displayed.

##### 2. The output details are displayed here with to show the successful completion of the tasks as defined:-
  ######  I. 	Set up Job – The workflow action set up is completed successfully.
   ###### II.  Param Container deployment – The param container deployment workflow is initiated successfully.
   ###### III. Check out – The checkout confirms the successful installation and availability of Ansible software for further execution
   ######  IV. Check ansible version – In this step the ansible version is checked 
   ###### V. Echo value – The user input is fetched successfully
   ###### VI. Adding timestamp – the timestamp at which the workflow started is generated and is successful in passing the timestamp to the next step
   ###### VII. User current time – the current timestamp is extracted in the required format
   ###### VIII. Run Ansible playbook – the ansible playbook is run and is successful
  ###### IX. Complete job – The complete steps are successful and shows the completion of the workflow

  ##### The current tool may need addition of new tools in future based on the requirement. These tools should be updated following the current format and structure followed to avoid any error. The up-dation can be of two types:-

I.  Create new tool and append to the list of existing tool
II.  Adding new version of the existing tool

## 7.2.2. Github Action to Delete Scenarios

The workflow is created to delete the containers, once the demo is done and user want to delete the containers.

#  7.3.	Create New Tools

#### Suppose a new tool comes into picture, say , sonarqube, the following steps needs to be followed to include the tool in the existing Github repository.

 ###### Step 1:
    Navigate to the Digital-Deploy-Service folder.
 ###### Step 2:	
   Find the roles folder under Digital-Deploy-service and create a new file by clicking on the ‘create new file’ under the roles folder ,from the ‘add file’ section at the top right corner of the Github page
 ###### Step 3:
    Name this file as ‘sonarqube’, create two more folder under ‘sonarqube’: a) tasks b) vars.
 ###### Step 4:
     Put the deployment, service and other related files(e.g : config file) in the tasks folder.
 ###### Step 5:
	 Put the variables under the main.yaml file that includes the tool name, container port number and the external or target port number for the container.
 ###### Step 6:
	 The tool details has to be updated in the file ‘create_demo_tools’ yaml file.
	 
 The same process needs to be followed for any new tool that gets added in the repository.
