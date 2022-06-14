# Landex Backend

Backend for Landex project, written with serverless framework and host on Microsoft Azure.

Refer to [Serverless docs](https://serverless.com/framework/docs/providers/azure/guide/intro/) for more information.

## Create a Service Principal

Refer to [Azure authentication with service principal](https://docs.microsoft.com/en-us/azure/developer/java/sdk/identity-service-principal-auth)

To deploy the app, first create a service prinical which will be required for deploying:
```bash
$ az ad sp create-for-rbac -n "<Name of the App>" --role Contributor --scopes /subscriptions/<subscriptionId>
```

You will get the credentials in json object, save them and create following session variables:
```bash
$ export AZURE_SUBSCRIPTION_ID='<subscriptionId>'
$ export AZURE_TENANT_ID='<tenant>'
$ export AZURE_CLIENT_ID='<clienId>'
$ export AZURE_CLIENT_SECRET='<password>'
```

For `clientId`:
1. go to Azure dashborad and navigate to `Azure Active Directory`.
2. From left side menu, go to `App registrations`.
3. You will get a list of all service principals, copy the `Application (client) ID`.
4. Set the session variable with this value: `export AZURE_CLIENT_ID='<clienId>'`


## Deploy

```bash
$ sls deploy
```