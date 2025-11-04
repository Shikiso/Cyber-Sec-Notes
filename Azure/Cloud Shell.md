Create Resource:
`az group create --name IntroAzureRG --location eastus`

Create VM:
`az vm create --resource-group <ResourceName> --name <Name> --size <Size> --public-ip-sku <IP> --image <IOS> --admin-username <Username> --generate-ssh-keys`

# Smaller Commands
| Command         | Description                          |
| --------------- | ------------------------------------ |
| `code file.txt` | Opens file in  vscode in the browser |

# Add Ons
| Category           | Name                                                                                                                                                     |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Linux tools**    | bash  <br>zsh  <br>sh  <br>tmux  <br>dig                                                                                                                 |
| **Azure tools**    | [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/)  <br>AzCopy  <br>Azure Functions CLI  <br>Service Fabric CLI  <br>Batch Shipyard  <br>blobxfer |
| **Text editors**   | code (Cloud Shell editor)  <br>vim  <br>nano  <br>emacs                                                                                                  |
| **Source control** | git                                                                                                                                                      |
| **Build tools**    | make  <br>maven  <br>npm  <br>pip                                                                                                                        |
| **Containers**     | Docker Machine  <br>Kubectl  <br>Helm  <br>DC/OS CLI                                                                                                     |
| **Databases**      | MySQL client  <br>PostgreSql client  <br>sqlcmd Utility  <br>mssql-scripter                                                                              |
| **Other**          | iPython Client  <br>Cloud Foundry CLI  <br>Terraform  <br>Ansible  <br>Chef InSpec  <br>Puppet Bolt  <br>HashiCorp Packer  <br>Office 365 CLI            |

# Do's and Don'ts
## Do
- Open a command-line session from any browser
- Interact with resources without plug-ins
- Persist files for later use
- Edit files
## Dont
- Leave a session open for more than 20min for long running scripts.
- Use the CLI if you need admin permissions
- Install tools that are not supported
- Use storage from different regions
