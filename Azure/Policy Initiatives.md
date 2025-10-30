A service that allows you to create, assign and manage governance policies that enforce rules and effects over Azure resources to ensure that they stay compliant with your IT governance standards.

# Cloud Adoption Framework
Offers comprehensive guidance for Azure. Includes best practices, documentation and tools that Microsoft employees, partners and customers contribute to formulate and implement effective business and technology strategies for the cloud.
## Steps for Cloud Governance
![](/Images/cloud_governance.png)
1. **Build a governance team** - Establish a dedicated cloud governance team that's responsible for defining, maintaining, and reporting on the progress of cloud governance policies.
2. **Assess cloud risks** - Conduct a thorough risk assessment that's unique to your organization, addressing all risk categories, including regulatory compliance, security, operations, costs, data management, resource management, and AI-related risks.
3. **Document cloud governance policies** - Clearly document cloud governance policies that dictate acceptable cloud usage and outline the rules and guidelines that mitigate identified risks.
4. **Enforce cloud governance policies** - Implement a systematic approach to ensure compliance with cloud governance policies. Use automated tools alongside manual oversight to enforce compliance. These tools help set guardrails, monitor configurations, and ensure adherence to policies.
5. **Monitor cloud governance** - Regularly monitor cloud usage and the governance teams to ensure ongoing compliance with the established cloud governance policies.

## Considerations for defining a cloud governance policy
- **Business risk** – You must document the evolving business risks and the business's tolerance for risk based on data classification and application criticality.
- **Policy and compliance** – You must convert risk decisions into policy statements to establish cloud adoption boundaries efficiently.
- **Process** – You must establish processes to monitor violations and adherence to corporate policies.
![](/Images/cloud_governance_considerations.png)

The five core disciplines of cloud governance are:
- **Cost management** – Evaluates and monitors costs, including controlling IT expenditures to establish well-defined cost management. It also includes adjusting resources according to demand. It's crucial to exercise control over cloud expenditure to derive greater value from your investments.
- **Security baseline** – Ensures compliance with IT security requirements by applying a security baseline to all adoption efforts.
- **Resource consistency** – Ensures consistency in resource configuration and enforcing practices for onboarding, recovery, and discoverability.
- **Identity baseline** – Ensures that the baseline for identity and access is enforced by consistently applying role definitions and assignments.
- **Deployment acceleration** – Accelerates the deployment of policies through centralization, consistency, and standardization across deployment templates.

# Azure Policy Resources
Enforces organizational standards and assesses the compliance at scale. It evaluates Azure resources and  actions by comparing their properties to business rules, providing an aggregated view of the environments overall state. 

Six policy resources are available in Azure.
![](/Images/azure_policy_resources.png)

# Azure Policy Definitions
Describes resource compliance conditions and the action or effects that take place if those conditions are met. The policy consists of two parts:
- A **condition** that compares a resource property field or a value, accessed by using aliases, to a required value.
- The **effect** determines what happens when the policy rule is evaluated to match the condition. For each new resource, an updated resource, or an existing resource, the effects behave differently.
## Anatomy of a Policy Definition
You can use JSON to create a policy definition that contains the elements show in the following table:

|Element|Description|Properties or values|
|---|---|---|
|_displayName (string, max 128 characters)_|Used to identify the policy definition.||
|_description (string, max 512 characters)_|Provides context for when the definition is used.||
|_policyType (read-only string)_|Indicates the origin of the policy definition. This property can't be set, but SDK returns three values which are visible in the portal.|● Built in: Provided and maintained by Microsoft.  <br>● Custom: Custom definitions created by the customer.  <br>● Static: Regulatory Compliance policy with Microsoft ownership.|
|_mode (string)_|Configured depending on the target of the policy: an Azure Resource Manager property or a Resource Provider property.|● Resource Manager Modes:  <br>    o On All: Evaluates resource groups, subscriptions, and all resource types.  <br>    o Indexed: Evaluates resource groups, subscriptions, and all resource types.  <br>● Resource Provider Modes (limited to Built in policies and fully supported):  <br>    o Microsoft.Kubernetes.Data  <br>    o Microsoft.KeyVault.Data  <br>    o Microsoft.Network.Data  <br>● Resource Provider Modes (limited to Built in policies and in preview mode):  <br>    o Microsoft.ManagedHSM.Data  <br>    o Microsoft.DataFactory.Data|
|_version (string, optional)_|Built-in policy definitions can host multiple versions with the same definitionID. If no version number is specified, all experiences show the latest version of the definition.||
|_metadata (object, optional, max 1,024 characters)_|Stores information about the policy definition.|Common properties (for Built-in policies):  <br>● _version (string)_: Tracks details about the version of the contents of a policy definition.  <br>● _category (string)_: Determines under which category in the Azure portal the policy definition is displayed.  <br>● _preview (Boolean)_: True or false flag that indicates if the policy definition is in preview.  <br>● _deprecated (Boolean)_: True or false flag that indicates if the policy definition is deprecated.  <br>● _portalReview (string)_: Determines if parameters require review in the portal.|
|_parameters (object, optional)_|Help simplify your policy management by reducing the number of policy definitions. By including parameters in a policy definition, you can reuse that policy for different scenarios by using different values.|Properties:  <br>● name  <br>● type (String, Array, Object, Boolean, Integer, Float, DateTime)  <br>● metadata (description, displayName, strongType, assignPermissions)  <br>● defaultValue  <br>● allowedValues  <br>● schema|
|_policyRule (object)_|The effect of a policy is defined in the _policyRule_. The policy rule consists of the _if and then_ blocks.  <br>● In the _if_ block, you define one or more conditions that specify when the policy applies.  <br>● In the _then_ block, you define the effect that happens when the _if_ conditions result true.||
Example:
```
{
  "displayName": "Allowed locations",
  "description": "This policy enables you to restrict the locations your organization can specify when deploying resources. Use to enforce your geo-compliance requirements. Excludes resource groups, Microsoft.AzureActiveDirectory/b2cDirectories, and resources that use the 'global' region.",
  "policyType": "BuiltIn",
  "mode": "Indexed",
  "metadata": {
    "version": "1.0.0",
    "category": "General"
  },
  "parameters": {
    "listOfAllowedLocations": {
      "type": "Array",
      "metadata": {
        "description": "The list of locations that can be specified when deploying resources.",
        "strongType": "location",
        "displayName": "Allowed locations"
      }
    }
  },
    "policyRule": {
      "if": {
        "allOf": [
          {
            "field": "location",
            "notIn": "[parameters('listOfAllowedLocations')]"
          },
          {
            "field": "location",
            "notEquals": "global"
          },
          {
            "field": "type",
            "notEquals": "Microsoft.AzureActiveDirectory/b2cDirectories"
          }
        ]
      },
      "then": {
        "effect": "deny"
      }
    }
  }
```

(For the syntax go [here](https://learn.microsoft.com/en-us/training/modules/sovereignty-policy-initiatives/azure-policy-definitions))

# Evaluation of Resources through Azure Policy
Azure provides control over resources in a subscription or management group. The control allows you to prevent resources being created in the wrong location, enforce common and consistent tag usage or audit existing resources for appropriate configurations and settings.

## Evaluation Triggers
Evaluations of assigned policies and initiatives happen as the result of various events:
- A policy or initiative is newly assigned to a scope
- A policy or initiative already assigned to a scope is updated
- A resource is deployed to or updated in a scope with an assignment through Azure Resource Manager, REST API, or a supported SDK
- A subscription (resource type Microsoft.Resources/subscriptions) is created or moved in a management group hierarchy with an assigned policy definition that targets the subscription resource type
- A policy exemption is created, updated, or deleted
- Standard compliance evaluation cycle
- The machine configuration resource provider is updated with compliance details by a managed resource
- On-demand scan

## Evaluation Timing
Compliance scans through Azure policies are triggered by various methods:
- **Automatic full scan** - A full compliance scan is triggered automatically every 24 hours.
- **Manual scan for Brownfield scenarios** - In cases where a new policy is applied to existing resources (Brownfield scenarios), you can manually trigger a compliance scan by running _az policy state trigger-scan_.

## Resource Compliance States
Evaluation provides one of the compliance states to each resource based on conditions in the policy rule and each resources adherence to those requirements.
- **Non-compliant**
- **Compliant**
- **Error** (for template or evaluation error)
- **Conflicting** (two or more policy assignments in the same scope with contradicting rules, such as two policies appending the same tag with different values)
- **Protected** (resource covered under an assignment with a _denyAction_ effect)
- **Exempted Unknown** (default state for definitions with a _manual_ effect)

When multiple resources or policies have varying compliance states, the overall compliance state is assessed individually for each resource and for each policy assignment.

# Enforcement Mode
A property of a policy assignment that lets you deactivate the enforcement of certain policy effects.
This mode allows you to test the policies outcome on existing resources without initiating the policy effect or triggering entries in the activity log.

# Policy Enforcement and Safe Deployment
Treating policy as code allows you to automate testing and make sure no manual error factor happens.
The best practices framework focuses on minimizing the impact of policy changes while ensuring compliance and it includes two aspects:
- **First aspect** - Start from Assignments of new policies with _enforcementMode_ Disabled. When assigning policies that include deny or modify actions, beginning with _enforcementMode_ Disabled allows you to view the compliance state and evaluate policy outcomes without triggering actions or denying operations. This "what-if" scenario minimizes impact and helps identify issues in the new policies or changes without disrupting the environment.
    
- **Second aspect** - Deploy policies in deployment rings. To control potential negative impacts, policies should be deployed gradually in smaller subsets and then in bigger sets. You can start with test and development environments and then move to production by applying the policy to a small subset first. This strategy helps in testing the policy thoroughly. Gradually expanding the scope (through deployment rings) can cover the full production environment.

The following diagram shows how to apply the safe deployment best practices framework for Azure Policy assignments.
![](/Images/azure_policy_assignments.png)
