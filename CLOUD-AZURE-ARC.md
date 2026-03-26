# Azure - ARC

## Installing 

Edit the following script and save it as .sh
```
export subscriptionId="<your subscription id>";
export resourceGroup="<your resource group";
export tenantId="<your tenant id";
export location="<your region>";
export authType="token";
export correlationId="<your correlation id>";
export cloud="AzureCloud";
LINUX_INSTALL_SCRIPT="/tmp/install_linux_azcmagent.sh"
if [ -f "$LINUX_INSTALL_SCRIPT" ]; 
    then rm -f "$LINUX_INSTALL_SCRIPT"; 
fi;

output=$(wget https://gbl.his.arc.azure.com/azcmagent-linux -O "$LINUX_INSTALL_SCRIPT" 2>&1);

if [ $? != 0 ]; 
    then wget -qO- --method=PUT --body-data="{\"subscriptionId\":\"$subscriptionId\",\"resourceGroup\":\"$resourceGroup\",\"tenantId\":\"$tenantId\",\"location\":\"$location\",\"correlationId\":\"$correlationId\",\"authType\":\"$authType\",\"operation\":\"onboarding\",\"messageType\":\"DownloadScriptFailed\",\"message\":\"$output\"}" "https://gbl.his.arc.azure.com/log" &> /dev/null || true; 
fi;
echo "$output";
bash "$LINUX_INSTALL_SCRIPT";
sleep 5;
sudo azcmagent connect --resource-group "$resourceGroup" --tenant-id "$tenantId" --location "$location" --subscription-id "$subscriptionId" --cloud "$cloud" --tags '<your list of tags separated by comma>' --correlation-id "$correlationId";
```

Showing `azcmagent` (ARC agent) informations
```
azcmagent show
```

Checking installed extensions on machine
```
sudo azcmagent extension list
```

Stopping service of MDE.linux
```
sudo systemctl stop mdatp
```

Disable service of MDE.linux
```
sudo systemctl disable mdatp
```

Deleting an extension. Example of extension name: `MDE.Linux`
```
sudo azcmagent extension remove --name <extension_name>
```

azcmagent logs
```
/var/opt/azcmagent/log/himds.log
/var/lib/GuestConfig/ext_mgr_logs/gc_ext.log
```


### Disabling Endpoint protection

Enter to:
 - Microsoft Defender for cloud
 - Management > Environment Settings
 - Azure > Tenant Root (x of x subscriptions) > click on your tenant name
 - Click on the button "Settings & monitoring"

### AZ CLI - EXTENSIONS

To see all of extensions are installed to your az cli
```
az extension list -o table
```
