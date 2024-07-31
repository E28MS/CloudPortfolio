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

*Transpilation* is the process of converting source code written in one language into another language.  When you deploy a resource or series of resources to Azure, you submit the Bicep template to Resource Manager, which still requires JSON templates. The tooling that's built into Bicep converts your Bicep template into a JSON template. This process is known as transpilation, which essentially treats the ARM template as an intermediate language.

### Benefits of Bicep

Bicep provides many improvements over JSON for template authoring, including:

* Simpler syntax: Bicep provides a simpler syntax for writing templates. You can reference parameters and variables directly, without using complicated functions. String interpolation is used in place of concatenation to combine values for names and other items. You can reference the properties of a resource directly by using its symbolic name instead of complex reference statements. These syntax improvements help both with authoring and reading Bicep templates.

* Modules: You can break down complex template deployments into smaller module files and reference them in a main template. These modules provide easier management and greater reusability. You can even share your modules with your team.

* Automatic dependency management: In most situations, Bicep automatically detects dependencies between your resources. This process removes some of the work involved in template authoring.

* Type validation and IntelliSense: The Bicep extension for Visual Studio Code features rich validation and IntelliSense for all Azure resource type API definitions. This feature helps provide an easier authoring experience.

### Resources

[Learn Microsoft Introduction to IaC](https://learn.microsoft.com/en-us/training/modules/introduction-to-infrastructure-as-code-using-bicep/2-what-infrastructure-code)


