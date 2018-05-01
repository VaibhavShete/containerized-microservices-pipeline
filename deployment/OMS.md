## Install OMS Agent onto Cluster
1. Navigate to your OMS Workspace in the portal by finding it under your "Log Analytics" resources
2. Find your Workspace Key by clicking on the Advanced Settings blade, then Connected Sources > Linux Servers
3. Copy the primary key and paste it into the helm command in step 5
4. Open a terminal and run this command to find the Workspace ID:

```
WSID=$(az resource show --resource-group resourcegroupname  --resource-type Microsoft.OperationalInsights/workspaces --name loganalyticsworkspacename | grep customerId | sed -e 's/.*://')
```
5. Run the following with your proper Workspace Key:

```
#helm install --name omsagent --set omsagent.secret.wsid=$WSID --set omsagent.secret.key=<key-value> stable/msoms
```
