# ARM Template for Setting Subscription Diagnostic Settings

[Microsoft documentation](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-settings-subscription)

The ARM template in this repo only deploys the diagnostic settings for Service Health and Resource Health activity to be forwarded to a Log Analytics Workspace of your choice for your subscription.

Deploy using a subscription deployment command:

```bash
az deployment create --template-file template.json --parameters parameters.json -l uksouth
```

```powershell
New-AzDeployment -TemplateParameterFile parameters.json -TemplateFile template.json -Location uksouth
```

## Notes
I've had to use a `concat` in the ARM template vs a `resourceId` - adds flexibility of either deploying at a subscription level or to a resource group (`resourceId` at a subscription level [doesn't provide the output required for the `workspaceId` field](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-functions-resource#return-value-5))