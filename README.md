This section of the document gives an overview of the solution architecture on activities related to Github action as a CD pipeline integrated with Ansible to  intiate containers in  Azure Kubernetes Service. The application is developed using microservice architecture to support better agility, independent deployment, and scalability.

The user selects the tool and the version from the from end from an approved list of tools. The front end collects the data and sends the list of selected tool to Github action workflow through an API calling the required containers. 
