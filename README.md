7.2. Github Action Wokflow

The GitHub action workflow allows to create custom workflow directly in the GitHub repository. This helps in running different tasks automatically based on the events. This also helps in CI/CD capabilities directly in the repository. The workflow has been created in the GitHub repository which receives the API call from the webserver and the actions defined in the workflow gets triggered followed with running of the Ansible Playbook. The structure and the content of the workflow and the Ansible playbook has been described in this document. The Github action are created for the below two scenarios:

Github action to intiate the demo with selected containers
Github action to delete the containers
 
