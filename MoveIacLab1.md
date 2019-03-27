# Lab 1: Provision a server via the Azure Portal and use DSC to configure the IIS role

1. Log onto the [Azure Portal](https://portal.azure.com) (https://portal.azure.com):

<img src="images/Lab1_1.png" width="624"/>

2. Choose ‘Create a resource’:

<img src="images/Lab1_2.png" width="624"/>

3. Start typing ‘Virtual Machine’ until the option to create a Virtual Machine is displayed and then click on it:

<img src="images/Lab1_3.png" width="624"/>

4. Click the blue ‘Create’ button at the bottom of the screen:

<img src="images/Lab1_4.png" width="624"/>

5. Fill in the parameters as per the screenshot below for your virtual machine:

<img src="images/Lab1_5.png" width="624"/>
<img src="images/Lab1_6.png" width="624"/>
<img src="images/Lab1_7.png" width="624"/>

6. On the ‘Networking’ tab, if you do not have a demo / test virtual network (VNET) already provisioned then choose ‘Create new’ and fill in the parameters as per screenshot below:

<img src="images/Lab1_8.png" width="624"/>
<img src="images/Lab1_9.png" width="624"/>

7. The remainder of the ‘Networking’ settings can be left as default including the creation of a new public IP Address for your VM:

<img src="images/Lab1_10.png" width="624"/>

8. Click ‘Review + create’ and then ‘Create’ once the validation has passed:

<img src="images/Lab1_11.png" width="624"/>
<img src="images/Lab1_12.png" width="624"/>

9. Whilst the VM is provisioning, we can create an Azure Automation account which is required to setup and apply DSC profiles.

Click ‘Create a resource’ and start typing ‘Automation’ until the option of creating an Automation account appears and then click on it:

<img src="images/Lab1_14.png" width="624"/>

10. Click on the blue ‘Create’ button at the bottom of the screen:

<img src="images/Lab1_15.png" width="624"/>

11.	Fill in the parameters as per the screenshot below and then click ‘Create’:

<img src="images/Lab1_17.png" width="624"/>

12. Confirm your VM from step #8 has successfully completed provisioning by choosing ‘Virtual machines’ from the left hand menu (if you do not have a Virtual machines shortcut then just type the name of your VM into the search box at the top):

<img src="images/Lab1_18.png" width="624"/>
<img src="images/Lab1_19.png" width="624"/>

13. Verify the status is ‘Running’ and note the public IP Address that has been assigned:

<img src="images/Lab1_20.png" width="624"/>

14. RDP into the VM by clicking the ‘Connect’ button at the top using the credentials you provided in step #5 and verify you can logon on successfully:

<img src="images/Lab1_20.png" width="624"/>
<img src="images/Lab1_21.png" width="624"/>









[<- Introduction](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/README.md) | [Lab 2: Work with an ARM template from an existing resource](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab2.md)
