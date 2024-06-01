# Infrastructure as Code

Instead of creating our services through the GUI, we can create them using a code-based approach. In this way we can have the truth source written as code.  

## Creating a PostgreSQL service using IAC concepts.  

The PostgreSQL cluster and database will be created in DigitalOcean, but instead of creating them directly using the GUI, we'll use Terraform to write the params as code.  

### DigitalOcean

DigitalOcean is an Infrastructure as a Service solution.  
Differences between IaaS, PaaS, SaaS and CaaS: [here](https://cloud.google.com/learn/paas-vs-iaas-vs-saas)  

### Terraform

Init terraform based on the configuration files  
`terraform init`  

Check if the files are formatted correctly  
`terraform fmt`  

Show the actions terraform will take according to the configuration files  
`terraform plan`  

Apply terraform actions listed in `terraform plan`  
`terraform apply -auto-approve`  

`terraform plan --destroy`
