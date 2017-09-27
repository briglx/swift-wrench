# swift-wrench


Steps to run this code

# Create a Subscription for Monitoring (This is a shared subscription that holds all storage accounts)
# Create a Storage Account in each Region where you have a VM you want monitored


Sample parameters.json
{
	"subscriptions": ["subscriptionid","subscriptionid","subscriptionid"],
	"storageSubscription": "nameofstoragesubscription"
}

Sample parameters2.json
{
	"subscriptions": ["*"]
	"storageSubscription": "nameofstoragesubscription"
}



$storageAccounts = ["East US", "StorageName", "StorageKey",...}]


Update-VmMonitoringFlags -parameters parameters.json

Flags

- subscriptions: List of subscription. 
	If *, all subscriptions the user has access to will be updated

- vms: List of vms to enable. (Optional) 
	All vms in list will be updated, unless in blacklist
	If empty, all VMs will be updated, unless in blacklist

- blacklist: List of vms to not-enable: (Optional)
	VMs in this list will not be modified...ever.




Sample Storage Accounts

	{
		account: { 
	    	"location" : "East US 2", 
	    	"version" : "arm"
			"Storage Name": "mystorageaccountname", 
			"Storage Key": "mykeythatendsin_"
	    },
	    account: { 
	    	"location" : "East US 2", 
	    	"version" : "asm"
			"Storage Name": "mystorageaccountname", 
			"Storage Key": "mykeythatendsin_"
	    },
	    account: { 
	    	"location" : "East US", 
	    	"version" : "arm"
			"Storage Name": "mystorageaccountname", 
			"Storage Key": "mykeythatendsin_"
	    }
	}


# Todo

- Whitelist/blacklist VMs
- Provide list of Subscriptions