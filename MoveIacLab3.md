# Lab 3: Creating ARM templates from scratch

This lab will walk through some of the options for creating ARM templates.

## Part 1: Azure QuickStart Templates

1.  In a browser navigate to the [Azure QuickStart Templates](https://azure.microsoft.com/en-us/resources/templates/) (https://azure.microsoft.com/en-us/resources/templates/). This is a community resource of hundreds of examples of ARM Templates, from Microsoft and 3rd parties. If you have an infrastructure configuration in mind it's always worth searching to see if there are examples that would deliver, or at least give you a good start in creating, the ARM Templates required. We'll walk through finding an ARM template to match the manually created Windows Server with IIS Feature enabled in Lab 1.

<img src="images/Lab3_1.jpg" width="624"/>

2. In the Search field enter "IIS DSC", and select the "IIS Server using DSC extension on a Windows VM" option:

<img src="images/Lab3_2.jpg" width="624"/>

3. Take a look at the information on the page, which includes details of the ARM template, the parameters to be supplied and examples of how to invoke the ARM template from the command line and powershell. Every ARM template in the QuickStart Gallery maintains the ARM template files in GitHub so that they are available to be reused. To take a look, once you've had a look at the information on the page, select Browse on GitHub:

<img src="images/Lab3_3.jpg" width="624"/>

4. You'll see a list of all the files in the GitHub repo. The most important are the .json files for the ARM Template itself, and the parameters file. Click on the azuredeploy.json file:

<img src="images/Lab3_4.jpg" width="624"/>

5. You'll now see the contents of the ARM Template, most of which you should now be familiar with (parameters, resources etc.). Scroll down to the bottom of the template to see how DSC is used to enable the IIS feature on the Windows VM. Note that the DSC script that is to be run is passed in as a parameter (modulesURL):

<img src="images/Lab3_5.jpg" width="624"/>

6. To understand where the modulesURL is set and what it points to, go back in the browser to the previous contents page and select the azuredeploy.parameters.json file:

<img src="images/Lab3_6.jpg" width="624"/>

7. The parameters file sets all the default parameters to be passed into the main ARM template, unless they are overridden. Note that the default value for modulesURL is to a file in the same GitHub repository:

<img src="images/Lab3_7.jpg" width="624"/>

Copy the modulesURL value (https://github.com/Azure/azure-quickstart-templates/raw/master/dsc-extension-iis-server-windows-vm/ContosoWebsite.ps1.zip) to the clipboard or notepad for use in a minute.

8. Go back to the previous contents page again and the file that is being referenced in the parameter is the .ps1.zip file:

<img src="images/Lab3_8.jpg" width="624"/>

9. You could fork or download the files and then change them or reuse them as you see fit but let's return to the Azure QuickStart page (back in the browser or if needed search for the template again as above). Click on the Deploy to Azure button to deploy directly into your subscription:

<img src="images/Lab3_9.jpg" width="624"/>

10. You will be taken into the Azure Portal and onto the template deployment page. Check all the fields but create a new resource group (again for easy deletion), vm name, admin user, password and copy in the modulesURL from above. Then agree to the terms and conditions and click Purchase:

<img src="images/Lab3_10.jpg" width="624"/>

11. You should see the deployment gets underway:

<img src="images/Lab3_11.jpg" width="624"/>

12. Find the VM in the portal and once it shows as running select the extensions blade to see that DSC has been configured and is in the process of updating the VM:

<img src="images/Lab3_12.jpg" width="624"/>

13. Select the status details and, depending on timing, you'll see it's status change from transitioning to succeedeed:

<img src="images/Lab3_13.jpg" width="624"/>

14. If you want to confirm, connect to the VM and you'll see that the IIS feature is enabled and running and/or open the browser and connect to http://localhost to see the default IIS page running.

<img src="images/Lab3_14.jpg" width="624"/>

This VM won't be needed any longer so delete the resource group whenever you've finished to ensure minimum cost.












[Lab 2: Work with an ARM template from an existing resource](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab2.md) | [Lab 4: Failover between regions](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab4.md)
