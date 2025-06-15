**Azure CLI and Azure PowerShell command guide** across **Basic**, **Intermediate**, and **Advanced** categories for you.
I’ll focus on Azure CLI (`az` commands), with equivalent PowerShell notes where helpful.

---

## 📖 Azure Command Cheat Sheet

---

## 🌱 Basic Azure CLI Commands

| Purpose                     | Command (Azure CLI)                                         |
| :-------------------------- | :---------------------------------------------------------- |
| Login to Azure              | `az login`                                                  |
| Set a specific subscription | `az account set --subscription "<subscription-name-or-id>"` |
| List all subscriptions      | `az account list -o table`                                  |
| Show current subscription   | `az account show`                                           |
| List all resource groups    | `az group list -o table`                                    |
| Create a resource group     | `az group create --name MyResourceGroup --location eastus`  |
| Delete a resource group     | `az group delete --name MyResourceGroup`                    |
| List available locations    | `az account list-locations -o table`                        |
| List VM images              | `az vm image list --output table`                           |

---

## ⚙️ Intermediate Azure CLI Commands

| Purpose                                          | Command (Azure CLI)                                                                                            |
| :----------------------------------------------- | :------------------------------------------------------------------------------------------------------------- |
| Create a virtual machine                         | `az vm create --resource-group MyRG --name MyVM --image UbuntuLTS --generate-ssh-keys`                         |
| List all virtual machines                        | `az vm list -d -o table`                                                                                       |
| Start a VM                                       | `az vm start --name MyVM --resource-group MyRG`                                                                |
| Stop (deallocate) a VM                           | `az vm stop --name MyVM --resource-group MyRG`                                                                 |
| Delete a VM                                      | `az vm delete --name MyVM --resource-group MyRG`                                                               |
| Create a storage account                         | `az storage account create --name mystorageaccount --resource-group MyRG --location eastus --sku Standard_LRS` |
| List storage accounts                            | `az storage account list -o table`                                                                             |
| Create an Azure Container Registry (ACR)         | `az acr create --resource-group MyRG --name MyContainerRegistry --sku Basic --admin-enabled true`              |
| Create an Azure Kubernetes Service (AKS) cluster | `az aks create --resource-group MyRG --name MyAKSCluster --node-count 2 --generate-ssh-keys`                   |
| Get AKS credentials (for `kubectl`)              | `az aks get-credentials --resource-group MyRG --name MyAKSCluster`                                             |
| List Kubernetes nodes                            | `kubectl get nodes`                                                                                            |

---

## 🚀 Advanced Azure CLI Commands

| Purpose                                 | Command (Azure CLI)                                                                                                                                                                |
| :-------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Create a custom VM image                | `az image create --resource-group MyRG --name MyCustomImage --source MyVM`                                                                                                         |
| Attach a new data disk to a VM          | `az vm disk attach --resource-group MyRG --vm-name MyVM --name MyDataDisk`                                                                                                         |
| Resize a VM                             | `az vm resize --resource-group MyRG --name MyVM --size Standard_DS2_v2`                                                                                                            |
| Create a Virtual Network (VNet)         | `az network vnet create --resource-group MyRG --name MyVNet --address-prefix 10.0.0.0/16`                                                                                          |
| Create a subnet within a VNet           | `az network vnet subnet create --resource-group MyRG --vnet-name MyVNet --name MySubnet --address-prefixes 10.0.1.0/24`                                                            |
| Set a NSG (Network Security Group) rule | `az network nsg rule create --resource-group MyRG --nsg-name MyNSG --name AllowSSH --protocol Tcp --priority 1000 --destination-port-ranges 22 --access Allow --direction Inbound` |
| Create an Azure Managed Identity        | `az identity create --name MyIdentity --resource-group MyRG`                                                                                                                       |
| Assign a role to a Managed Identity     | `az role assignment create --assignee <clientId> --role "Contributor" --scope /subscriptions/<subscription-id>/resourceGroups/MyRG`                                                |
| Create an Azure Function App            | `az functionapp create --resource-group MyRG --consumption-plan-location eastus --runtime node --functions-version 4 --name myfunctionapp --storage-account mystorageaccount`      |
| Export ARM template from resource group | `az group export --name MyRG --output json > template.json`                                                                                                                        |

---

## ⚡ Bonus: Azure PowerShell Basic Examples

| Purpose                 | Command (Azure PowerShell)                                      |
| :---------------------- | :-------------------------------------------------------------- |
| Login                   | `Connect-AzAccount`                                             |
| Set subscription        | `Set-AzContext -SubscriptionName "My Subscription"`             |
| List resource groups    | `Get-AzResourceGroup`                                           |
| Create a resource group | `New-AzResourceGroup -Name MyResourceGroup -Location "East US"` |
| List VMs                | `Get-AzVM`                                                      |

---

## 📚 Pro Tips

* Use `-o table` for human-readable table output.
* Use `--query` for JMESPath filtering, example:
  `az vm list --query "[].{Name:name, Status:powerState}" -o table`
* Combine Azure CLI commands with Bash scripting for automation.
* Use Azure CLI in **Cloud Shell** or local installation.
* Learn `az extension list-available` for extra Azure services (like K8s-preview, DevOps etc.)

---
