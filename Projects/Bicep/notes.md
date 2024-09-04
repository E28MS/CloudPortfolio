## Things I learnt Setting up Virtual Networks:

### 1.  Choosing IP addresses/ranges/prefixes:

In order to adhere to the ranges provided for subnets, I used the following information:

### IP Ranges Given:
- **VNet 1**: 10.10.10.0/24
- **VNet 2**: 10.20.20.0/24

Each `/24` subnet provides 256 IP addresses, ranging from `.0` to `.255`. However, certain IP addresses are reserved and cannot be used:

1. **Network Address**: The first IP address (e.g., `10.10.10.0`).
2. **Broadcast Address**: The last IP address (e.g., `10.10.10.255`).
3. **Azure Reserved Addresses**: The first three IP addresses after the network address (e.g., `10.10.10.1`, `10.10.10.2`, and `10.10.10.3`).

### Breakdown for VNet 1 (10.10.10.0/24):

#### Subnet 1:
- **Subnet Range**: Let's assume you need a subnet with 128 addresses (e.g., `/25`).
  - **Subnet Address Range**: `10.10.10.0/25`
  - **Total IPs**: 128 (from `10.10.10.0` to `10.10.10.127`)
  - **Usable IPs**: `10.10.10.4` to `10.10.10.126` (the first 3 and last 1 IPs are reserved)

#### Subnet 2:
- **Subnet Range**: Let's assign the remaining IP range in VNet 1 to Subnet 2 (also `/25`).
  - **Subnet Address Range**: `10.10.10.128/25`
  - **Total IPs**: 128 (from `10.10.10.128` to `10.10.10.255`)
  - **Usable IPs**: `10.10.10.132` to `10.10.10.254` (the first 3 and last 1 IPs are reserved)

### Breakdown for VNet 2 (10.20.20.0/24):

#### Subnet 1:
- **Subnet Range**: Similarly, let's divide VNet 2 into two subnets with 128 addresses each.
  - **Subnet Address Range**: `10.20.20.0/25`
  - **Total IPs**: 128 (from `10.20.20.0` to `10.20.20.127`)
  - **Usable IPs**: `10.20.20.4` to `10.20.20.126` (the first 3 and last 1 IPs are reserved)

#### Subnet 2:
- **Subnet Range**: The remaining IP range in VNet 2 can be allocated to Subnet 2.
  - **Subnet Address Range**: `10.20.20.128/25`
  - **Total IPs**: 128 (from `10.20.20.128` to `10.20.20.255`)
  - **Usable IPs**: `10.20.20.132` to `10.20.20.254` (the first 3 and last 1 IPs are reserved)

### Summary:

- **VNet 1: 10.10.10.0/24**
  - **Subnet 1: 10.10.10.0/25** 
    - Usable IPs: `10.10.10.4` to `10.10.10.126`
  - **Subnet 2: 10.10.10.128/25** 
    - Usable IPs: `10.10.10.132` to `10.10.10.254`

- **VNet 2: 10.20.20.0/24**
  - **Subnet 1: 10.20.20.0/25** 
    - Usable IPs: `10.20.20.4` to `10.20.20.126`
  - **Subnet 2: 10.20.20.128/25** 
    - Usable IPs: `10.20.20.132` to `10.20.20.254`

This breakdown ensures that each subnet has an adequate number of IP addresses and adheres to Azure's reserved address requirements.

### 2.  Choosing API versions:

The version date `2023-02-01` in the `virtualNetworks@2023-02-01` resource type refers to the **API version** of the Azure Resource Manager (ARM) resource provider used in your Bicep file. This API version specifies which version of the Azure resource provider's schema is being used to define and deploy the resource.

### Why `2023-02-01`?

1. **Latest Features and Compatibility**: Azure regularly updates its resource providers to include new features, improvements, and bug fixes. The API version `2023-02-01` is a recent version that ensures compatibility with the latest features and practices as of that date.

2. **Documentation Reference**: When you look up Azure resources in the official [Azure Resource Manager REST API documentation](https://learn.microsoft.com/en-us/rest/api/virtualnetwork/), you will see different API versions listed. Using a specific API version ensures that the properties and parameters you're using are well-defined and supported as of that version.

3. **Stability**: Specifying an API version like `2023-02-01` ensures that your Bicep template will behave consistently even as Azure evolves. If you don't specify an API version, Azure might use the latest available version, which could introduce unexpected changes if newer versions are released.

### Where Did This Come From?

- **Azure Resource Manager (ARM) API Versions**: Azure resource providers (like `Microsoft.Network`, which manages virtual networks) release new versions over time. Each API version corresponds to a specific state of the resource provider's capabilities and schema.
- **Documentation and IntelliSense**: When developing Bicep or ARM templates, tools like Visual Studio Code with the Bicep extension provide IntelliSense that suggests API versions. You can select from the available API versions to ensure you're using one that meets your needs.

### Is It Necessary?

Yes, specifying the API version is necessary to:

- **Ensure Consistency**: It locks your template to a specific version, making sure your deployment won't break if Azure updates the resource provider.
- **Access Specific Features**: Some features or properties might only be available in newer API versions. By choosing a recent API version, you can take advantage of these features.
- **Avoid Deprecation Issues**: Older API versions may be deprecated over time, so using a more recent version helps future-proof your template.

### How to Find the Right API Version

1. **Azure Portal**: When you manually create resources in the Azure Portal, it uses the latest API version. You can inspect these resources in the "Export template" section to see which API version was used.

2. **Bicep Extension in VS Code**: The Bicep extension offers IntelliSense that suggests API versions based on the resource you're defining.

3. **Official Documentation**: Check the official Azure documentation for the latest and previous API versions.

In summary, `2023-02-01` is chosen because it's a recent version that likely includes the latest features and improvements for virtual networks, ensuring compatibility and stability in your Bicep templates.
