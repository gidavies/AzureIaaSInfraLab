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

<img src="images/Lab1_16.png" width="624"/>

12. Confirm your VM from step #8 has successfully completed provisioning by choosing ‘Virtual machines’ from the left hand menu (if you do not have a Virtual machines shortcut then just type the name of your VM into the search box at the top):

<img src="images/Lab1_17.png" width="624"/>
<img src="images/Lab1_18.png" width="624"/>

13. Verify the status is ‘Running’ and note the public IP Address that has been assigned:

<img src="images/Lab1_19.png" width="624"/>

14. RDP into the VM by clicking the ‘Connect’ button at the top using the credentials you provided in step #5 and verify you can logon on successfully:

<img src="images/Lab1_20.png" width="624"/>
<img src="images/Lab1_21.png" width="624"/>

15.	In the Azure portal start typing ‘Automation’ into the search bar until your Automation account that you provisioned in step #11 is displayed, then click on it:

<img src="images/Lab1_22.png" width="624"/>

16.	Click on ‘State configuration (DSC)’:

<img src="images/Lab1_23.png" width="624"/>

17.	Click on ‘Gallery’:

<img src="images/Lab1_24.png" width="624"/>

18.	Click on ‘WindowsIISServerConfig’:

<img src="images/Lab1_25.png" width="624"/>

19.	Click on ‘Import’ and then the blue ‘OK’ button:

<img src="images/Lab1_26.png" width="624"/>
<img src="images/Lab1_27.png" width="624"/>
<img src="images/Lab1_28.png" width="624"/>

20.	Click on ‘labautomation – State configuration (DSC) to get back to the main dashboard:

<img src="images/Lab1_29.png" width="624"/>

21.	Click on ‘Configurations’ and verify that the WindowsIISServerConfig PS configuration imported successfully:

<img src="images/Lab1_30.png" width="624"/>

22.	Click on ‘WindowsIISServerConfig’:

<img src="images/Lab1_31.png" width="624"/>

23.	Click on ‘Compile’ and ‘Yes’:

<img src="images/Lab1_32.png" width="624"/>
<img src="images/Lab1_33.png" width="624"/>

24.	Click on ‘labautomation – State configuration (DSC) to get back to the main dashboard:

<img src="images/Lab1_34.png" width="624"/>

25.	Click on ‘Compiled configurations’ and then click ‘Refresh’. Note that the WindowsIISServerConfig does not appear:

<img src="images/Lab1_35.png" width="624"/>

26.	Click on ‘Configurations’ and then ‘WindowsIISServerConfig’:

<img src="images/Lab1_36.png" width="624"/>

27.	Note that the status is marked as ‘Suspended’. Click on the status and note the exception error displayed:

<img src="images/Lab1_37.png" width="624"/>
<img src="images/Lab1_38.png" width="624"/>

28.	This error message is displayed because we haven’t (yet) loaded the PS module for IIS administration into our DSC repository. 

Delete the WindowsIISServerConfig module from the pull server clicking ‘Yes’ at the prompt:

<img src="images/Lab1_39.png" width="624"/>

29.	 Click on ‘lab automation – State configuration (DSC)’ to return to the main dashboard:

<img src="images/Lab1_40.png" width="624"/>

30.	Click on ‘Modules’ from the left-hand side menu:

<img src="images/Lab1_41.png" width="624"/>

31.	Click on ‘Browse Gallery’:

<img src="images/Lab1_42.png" width="624"/>

32.	Type ‘xWeb’ and press enter:

<img src="images/Lab1_43.png" width="624"/>

33.	Click on the xWebAdministration module and choose ‘Import’ and ‘OK’:

<img src="images/Lab1_44.png" width="624"/>
<img src="images/Lab1_45.png" width="624"/>
<img src="images/Lab1_46.png" width="624"/>

34.	Click ‘labautomation – Modules’ to confirm that the xWebAdministration module has now been loaded (it may show as importing for a brief period):

<img src="images/Lab1_47.png" width="624"/>

35.	Click on ‘State configuration (DSC)’ to return to the DSC dashboard and repeat steps #17 thru #23 to import the WindowsIISServerConfig DSC profile again:

<img src="images/Lab1_48.png" width="624"/>
<img src="images/Lab1_49.png" width="624"/>

36.	Click on ‘Configurations’ and then ‘WindowsIISServerConfig’:

<img src="images/Lab1_50.png" width="624"/>

37.	Note that the status is marked as ‘Suspended’ again. Click on the status and note the same exception error displayed as in step #27:

<img src="images/Lab1_51.png" width="624"/>
<img src="images/Lab1_52.png" width="624"/>

38.	Compare the version of xWebAdministration that the WindowIISServerConfig PS is looking for versus the version that we have loaded into our PS modules:

<img src="images/Lab1_52.png" width="624"/>

39.	In order to edit the WindowsIISServerConfig PS to utilise the later version of xWebAdministration we can export the script, make a simple edit and re-upload it. 
Click ‘Export’ at the top of the screen and save the WindowsIISServerConfig PS locally on your PC:

<img src="images/Lab1_53.png" width="624"/>
<img src="images/Lab1_54.png" width="624"/>

40.	Open the PS script with a text editor and change the value of the xWebAdministration version from 1.19.0.0 to 2.5.00 and save it:

<img src="images/Lab1_55.png" width="624"/>

41.	Delete the existing WindowsIISServerConfig module from the pull server clicking ‘Yes’ at the prompt:

<img src="images/Lab1_56.png" width="624"/>

42.	Click on ‘lab automation – State configuration (DSC)’ to return to the main dashboard:

<img src="images/Lab1_57.png" width="624"/>

43.	Click on ‘Add’ and browse to the edited PS file you created in step #40 clicking ‘OK’ to confirm:

<img src="images/Lab1_58.png" width="624"/>
<img src="images/Lab1_59.png" width="624"/>
<img src="images/Lab1_60.png" width="624"/>

44.	Repeat steps #22 thru #25 to compile the edited WindowsIISServerConfig PS and add it to the pull server. Note that this time it should load successfully:

<img src="images/Lab1_61.png" width="624"/>

45.	Click on ‘lab automation – State configuration (DSC)’ to return to the main dashboard and then click on ‘Nodes’:

<img src="images/Lab1_62.png" width="624"/>
<img src="images/Lab1_63.png" width="624"/>

46.	Click on ‘Add’:

<img src="images/Lab1_64.png" width="624"/>

47.	Pick the VM you provisioned at the start of this lab and click connect:

<img src="images/Lab1_65.png" width="624"/>
<img src="images/Lab1_66.png" width="624"/>

48.	Choose the WindowsIISServerConfig profile from the dropdown menu leaving everything else as default, then click OK:

<img src="images/Lab1_67.png" width="624"/>

49.	The VM should show “Connecting” and eventually ‘Connected’. Your VM should then show up under nodes as ‘Compliant’:

<img src="images/Lab1_68.png" width="624"/>
<img src="images/Lab1_69.png" width="624"/>

50.	Log onto your VM via RDP and verify that the IIS role is now installed. You can also look in the Windows Event Viewer to verify configuration was done via Azure Automation (DSC):

<img src="images/Lab1_70.png" width="624"/>
<img src="images/Lab1_71.png" width="624"/>













[<- Introduction](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/README.md) | [Lab 2: Work with an ARM template from an existing resource](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab2.md)
