Create Resource:
`az group create --name IntroAzureRG --location eastus`

Create VM:
`az vm create --resource-group <ResourceName> --name <Name> --size <Size> --public-ip-sku <IP> --image <IOS> --admin-username <Username> --generate-ssh-keys`