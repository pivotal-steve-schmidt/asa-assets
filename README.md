# Demo Azure Spring Apps Enterprise

Setting up Azure Sprint Apps Enterprise
Deploying the ACME Fitness Store Example
Configuring Single Sign On

## Update

Thu Mar  2 09:23:32 CET 2023

- ASA-E added Tanzu Developer Tools in Preview: Accelerators, App Live View, TAP GUI

NOTE: After doing all the steps outlined in this README, you need to
      - Enable: App Live View
      - Enable: App Accelerators
      This will automatically enable the Dev Tools Portal (tap-gui-server)

WARNING: After enabling the dev tools in the GUI, I had to start an INCOGNITO session
         to see the App Live View and App Accelerators

NOTE: Then I had to Assign endpoint for the Spring Cloud Gateway (in the GUI) to see the
      ACME application frontend
      Also for the API Portal the endpoint needs to be enabled in the GUI


## Original date

Wed 12 Oct 2022 13:23:04 CEST

## Quickstart

https://learn.microsoft.com/en-gb/azure/spring-apps/quickstart-deploy-apps-enterprise?tabs=azure-portal


% az account list --output table
Name                 CloudName    SubscriptionId                        TenantId                              State    IsDefault
-------------------  -----------  ------------------------------------  ------------------------------------  -------  -----------
PA-sschmidt          AzureCloud   8f914e8d-c81c-4137-ad8e-3a7305687ad5  29248f74-371f-4db2-9a50-c62a6877a0c1  Enabled  False
tdh-azure-schmidtst  AzureCloud   c3f83ceb-1b49-45b1-90c9-e522c11b02a4  b39138ca-3cee-4b4a-a4d6-cd83d9dd62f0  Enabled  True
schmidtst            AzureCloud   807f60ac-95f8-4afa-bc5f-39c3e5d0c59e  b39138ca-3cee-4b4a-a4d6-cd83d9dd62f0  Enabled  False

NOTE: needs to be done once

% az provider register --namespace Microsoft.SaaS

Registering is still on-going. You can monitor using 'az provider show -n Microsoft.SaaS'

% az provider show -n Microsoft.SaaS | grep -i state
  "providerAuthorizationConsentState": null,
  "registrationState": "Registered",

% az term accept \
    --publisher vmware-inc \
    --product azure-spring-cloud-vmware-tanzu-2 \
    --plan asa-ent-hr-mtr

% az account list-locations

##
## Real Start
##

# Clone the example repo

git clone https://github.com/Azure-Samples/acme-fitness-store

# Edit the schell scripts to define the group and service names

vi ./deploy-fit.sh
vi ./deploy-sso.sh

# Run the first script

bash ./deploy-fit.sh

# Verify that evrything is working - except the login

# Run the second script

bash ./deploy-sso.sh

# Verify login is working
