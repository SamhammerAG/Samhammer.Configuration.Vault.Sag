# Samhammer.Configuration.Vault.Sag

This is an internally used convenience library to add Samhammer.ConfigurationVault.

It does the following in addition:
* Locally: Uses the url and token returned by sagctl
* Kubernetes: Does a kubernetes role auth

## Prerequirements

### Locally

Sagctl has to be installed: https://samhammer.atlassian.net/wiki/spaces/K8S/pages/158793743/How+to+use+sagctl

### In the cluster

You need to set the following two environment variables:
* VaultUrl: With the url to vault
* VaultKubernetesRole: The vault role of the application

## How to use in Program.cs

```csharp
configurationBuilder.AddAuthenticatedVault(vaultOptions);

builder.Services
        .AddHealthChecks()
        .AddAuthenticatedVault()
```

See this documentation for the vault options: https://github.com/SamhammerAG/Samhammer.Configuration.Vault#vaultoptions
