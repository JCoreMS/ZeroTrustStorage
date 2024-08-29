
# Deploy Zero Trust Storage

This will deploy the following considering Zero Trusts configuration:

1. Storage Account (With File Share for FSLogix)
2. Key Vault (Used to create and house Customer Managed Keys)
3. Management VM (Used to domain join storage and configure NTFS permissions) --AD JOIN Option--
4. Managed User Identity (mapped to the Storage Account for Key Vault Access)
5. Private DNS Endpoint (for the Storage Account)

The overall solution provides a quick way to create a Storage Account for your FSLogix needs with an AD Domain Joined scenario and assumes you have a VNet with DNS to your Domain Controllers already configured. Additionally, you'll need to ensure you have an existing Private DNS Zone for Azure Files to store the endpoint created. Lastly, you'll need to ensure the deployment has access to this GitHub site in order to pull the needed "domainJoinStorage.ps1" script to the Management VM.

## AD Join Option

Upon completion of the deployment, there will be a running VM that you'll need to shutdown or remove if not needed. The VM will also have a log file on the root of the C: Drive called `cse_FileShareSetup` for troubleshooting.

Eventually there will be an update to provide an option for the following:
A. Remove/ Delete Management VM

## Entra ID Join Option

This option does NOT use or create the management VM and requires additional AVD VM configuration per:
https://learn.microsoft.com/en-us/azure/virtual-desktop/create-profile-container-azure-ad#configure-the-session-hosts

**Deploy Zero Trust Storage**

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#blade/Microsoft_Azure_CreateUIDef/CustomDeploymentBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2FJCoreMS%2FZeroTrustStorage%2Fmaster%2FsolutionStorage.json/uiFormDefinitionUri/https%3A%2F%2Fraw.githubusercontent.com%2FJCoreMS%2FZeroTrustStorage%2Fmaster%2FuiDefinitionStorage.json) [![Deploy to Azure Gov](https://aka.ms/deploytoazuregovbutton)](https://portal.azure.us/#blade/Microsoft_Azure_CreateUIDef/CustomDeploymentBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2FJCoreMS%2FZeroTrustStorage%2Fmaster%2FsolutionStorage.json/uiFormDefinitionUri/https%3A%2F%2Fraw.githubusercontent.com%2FJCoreMS%2FZeroTrustStorage%2Fmaster%2FuiDefinitionStoragegov.json)