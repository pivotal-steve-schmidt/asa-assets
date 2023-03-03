# Demo Azure Spring Apps Enterprise

Setting up Azure Sprint Apps Enterprise
Deploying the ACME Fitness Store Example
Configuring Single Sign On

## Update

	Thu Mar  2 09:23:32 CET 2023

	ASA-E added Tanzu Developer Tools in Preview: Accelerators, App Live View, TAP GUI

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
	your-name            AzureCloud   8f********************************d5  29********************************c1  Enabled  True
...

## The next steps need to be done once

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

## Real Start

### Clone the example repo

	git clone https://github.com/Azure-Samples/acme-fitness-store

### Edit the schell scripts to define the group and service names

	vi ./deploy-fit.sh
	vi ./deploy-sso.sh

### Run the first script

	bash ./deploy-fit.sh

### Verify that evrything is working - except the login

### Run the second script

	bash ./deploy-sso.sh

### Verify login is working
