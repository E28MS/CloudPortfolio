### What is Bicep?

Bicep is a domain-specific language (DSL) that uses declarative syntax to deploy Azure resources. In a Bicep file, you define the infrastructure you want to deploy to Azure, and then use that file throughout the development lifecycle to repeatedly deploy your infrastructure. Your resources are deployed in a consistent manner.

Bicep provides concise syntax, reliable type safety, and support for code reuse. Bicep offers a first-class authoring experience for your infrastructure-as-code solutions in Azure.

### Declarative syntax to provision IaC.

In Azure, a declarative code approach is accomplished by using templates. Many types of templates are available to use, including:

*JSON
*Bicep
*Ansible, by RedHat
*Terraform, by HashiCorp

### Key Terms

*Idempotence* is a term that's frequently associated with infrastructure as code. When an operation is idempotent, it means that it provides the same result each time it's run. If you choose tooling that uses idempotent operations, you can avoid configuration drift.

With *imperative code*, you execute a sequence of commands, in a specific order, to reach an end configuration. This process defines what the code should accomplish, and it defines how to accomplish the task. The imperative approach is like a step-by-step instruction manual.

With *declarative code*, you specify only the end configuration. The code doesn't define how to accomplish the task. The declarative approach is like the exploded view instruction manual.

*Azure Resource Manager template (ARM template)*: A template file that defines one or more resources to deploy to a resource group, subscription, management group, or tenant. You can use the template to deploy the resources in a consistent and repeatable way. There are two types of ARM template files: JSON and Bicep. 

###Benefits of Bicep

### Resources

[Learn Microsoft Introduction to IaC](https://learn.microsoft.com/en-us/training/modules/introduction-to-infrastructure-as-code-using-bicep/2-what-infrastructure-code)


