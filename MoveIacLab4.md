# Lab 4: Failover between regions

# Part 1: Use Azure Traffic Manager to provide geo-redundancy for a Web App

1. Load Visual Studio (Community Edition available for free here):
 
<img src="images/Lab4_1.png" width="624"/>

2. Click File > New > Project:

<img src="images/Lab4_2.png" width="624"/>

3. Choose ‘ASP.net Core Web Application’:

<img src="images/Lab4_3.png" width="624"/>

4. Give the project a name that’s easy to identify:
 
<img src="images/Lab4_4.png" width="624"/>

5. Choose ‘Web Application (Model-View-Controller)’ and untick ‘Enable Docker Support’ and ‘Configure for HTTPS’, then click ‘OK’:

<img src="images/Lab4_5.png" width="624"/>

6. If it doesn’t display automatically, click ‘View > Solution Explorer’:
 
<img src="images/Lab4_6.png" width="624"/>

7. In the Solution Explorer on the right hand side of the screen, expand Views > Home and click on ‘Index.cshtml’:

<img src="images/Lab4_7.png" width="624"/>

8. Select all of the default text in the left-hand pane of Visual Studio and delete it:

<img src="images/Lab4_8.png" width="624"/>

9. Type / paste in some basic HTML that identifies this Web App (sample below):

```html
<!DOCTYPE html>
<html>
<body>

<h1>This is <name>’s WebApp</h1>

<p>This is WebApp 1</p>

</body>
</html>
```
	 
<img src="images/Lab4_9.png" width="624"/>

10. Click ‘Save’:

<img src="images/Lab4_10.png" width="624"/>

11. In ‘Solution Explorer’ right click your Web App and choose ‘Publish’:
 
<img src="images/Lab4_11a.png" width="624"/>
<img src="images/Lab4_11b.png" width="624"/>

12. Choose ‘App Service’ and ‘Create New’ from the options and then click ‘Publish’ (note if you’ve not logged into an Azure subscription already you may be prompted to do so):
 
<img src="images/Lab4_12.png" width="624"/>

13. Choose an ‘App Name’ that is easily identifiable and choose an appropriate Resource Group for your web app, alternatively you can create a new one. For ‘Hosting Plan’ select ‘New’ and choose an App Service Plan name that is easily identifiable. Choose a location of ‘UK South’ and a size of ‘S1’. Then click ‘Create’:
 
<img src="images/Lab4_13.png" width="624"/>
<img src="images/Lab4_13b.png" width="624"/>

14. In the Azure portal, type in ‘App Services’ in the search bar at the top until the ‘App Services’ resource is displayed and then click it:

<img src="images/Lab4_14.png" width="624"/>

15. Verify your Web App appears:
 
<img src="images/Lab4_15.png" width="624"/>

16. Click on your Web App to display the overview dashboard:

<img src="images/Lab4_16.png" width="624"/>
 
17. Click on ‘SSL Settings’:

<img src="images/Lab4_17.png" width="312"/>

18. Set ‘HTTPS Only’ to ‘Off’:
 
<img src="images/Lab4_18.png" width="624"/>

19. Click on ‘Overview’ on the left-hand menu for the Web App:

<img src="images/Lab4_19.png" width="624"/>
 
20. Click on ‘Restart’:

<img src="images/Lab4_20.png" width="624"/>
 
21. Open a new InPrivate / Incognito / Private Browsing tab in your browser and paste in the HTTP address for your web app. Verify you can see your edited home page:

<img src="images/Lab4_21.png" width="624"/>
 
22. Repeat all previous steps to create another Web App and another App Service plan using names that easily identify them being different to the existing ones. 
IMPORTANT – Ensure to choose UK West as the region for your App Service plan
Example below:

```html
<!DOCTYPE html>
<html>
<body>

<h1>This is <name>’s WebApp</h1>

<p>This is WebApp 2</p>

</body>
</html>
```
<img src="images/Lab4_22.png" width="624"/>
<img src="images/Lab4_22b.png" width="624"/>
<img src="images/Lab4_22c.png" width="624"/>

23. You should now have 2 Web Apps, both with SSL disabled, running in different App Service Plans in different geographical regions:
 
<img src="images/Lab4_23.png" width="624"/>
<img src="images/Lab4_23b.png" width="624"/>
<img src="images/Lab4_23c.png" width="624"/>
 
24. In the Azure portal, type ‘Traffic Manager’ in the search box at the top until ‘Traffic Manager profiles’ is displayed, then click on it:
 
<img src="images/Lab4_24.png" width="624"/>

25. Click ‘Add’:
 
<img src="images/Lab4_25.png" width="624"/>

26. Choose an appropriate name for this Traffic Manager profile, leaving all other settings as per screenshot below and then click ‘Create’:
 
<img src="images/Lab4_26.png" width="624"/>
<img src="images/Lab4_26b.png" width="312"/>

27. Once the profile has been created click on it:
 
<img src="images/Lab4_27.png" width="624"/>
<img src="images/Lab4_27b.png" width="624"/>

28. Click on ‘Configuration’:
 
<img src="images/Lab4_28.png" width="312"/>

29. Edit the settings to reflect the screenshot below and click ‘Save’:
 
<img src="images/Lab4_29.png" width="624"/>

30. Click on ‘Endpoints’:
 
<img src="images/Lab4_30.png" width="312"/>

31. Click on ‘Add’:
 
<img src="images/Lab4_31.png" width="624"/>

32. Add the first Web App you created ensuring you choose ‘App Service’ on the drop-down menu and click ‘OK’:
 
<img src="images/Lab4_32.png" width="624"/>

33. Repeat the process for your second Web App (note the priority is auto set to 2):

<img src="images/Lab4_33.png" width="624"/>

34. Verify that both end points show as ‘Online’ under ‘Monitor Status’ (note you may need to wait a brief period whilst the initial probe is carried out during which time you will see ‘Checking endpoint’):
 
<img src="images/Lab4_34.png" width="624"/>

35. In the ‘Overview’ screen of your TM profile, note the DNS name that has been created:
 
<img src="images/Lab4_35.png" width="624"/>

36. If you are able, log onto your DNS registrar / provider for your domain, and create a CNAME DNS record that references the DNS name of your traffic manager identified in the previous step:
 
<img src="images/Lab4_36.png" width="624"/>

37. Verify that name resolution works correctly and your custom domain resolves to the traffic manager DNS name:
 
<img src="images/Lab4_37.png" width="624"/>

38. In the Azure portal, type ‘App Service’ in the search bar until you see the ‘App Services’ resource appear and click on it:

<img src="images/Lab4_38.png" width="624"/>
 
39. Click on your first Web App:
 
<img src="images/Lab4_39.png" width="624"/>

40. Click on ‘Custom Domains’ from the left-hand menu:
 
<img src="images/Lab4_40.png" width="312"/>

41. Click on ‘Add hostname’:

<img src="images/Lab4_41.png" width="624"/>

42. Type the DNS CNAME record from step #36 and click ‘Validate’:
 
<img src="images/Lab4_42.png" width="624"/>

43. Verify that domain validation passed successfully and then click ‘Add hostname’:
 
<img src="images/Lab4_43.png" width="624"/>

44. Repeat steps #40 thru #43 for your second Web App.

45. Open a new InPrivate / Incognito / Private Browsing tab in your browser and paste in the HTTP address for your custom traffic manager record. Verify connectivity to your first Web App:

<img src="images/Lab4_45.png" width="624"/>
 
46. In the Azure portal, on the overview page for your first Web App click ‘Stop’:
 
<img src="images/Lab4_46.png" width="624"/>

47. Still in the Azure portal, start typing ‘Traffic Manager’ in the search box at the top until the ‘Traffic Manager profiles’ resource is displayed, then click it:

<img src="images/Lab4_47.png" width="624"/>

48. Click on ‘Endpoints’:
 
<img src="images/Lab4_48.png" width="312"/>

49. Verify that your first Web App is marked as ‘Stopped’:
 
<img src="images/Lab4_49.png" width="624"/>

50. Open a new InPrivate / Incognito / Private Browsing tab in your browser and paste in the HTTP address for your custom traffic manager record. Verify connectivity to your second Web App:
 
<img src="images/Lab4_50.png" width="624"/>

## Part 2: Implementing Geo-Failover for A Virtual Machine Utilising Azure Site Recovery (ASR)

1. Log into the [Azure portal](https://ms.portal.azure.com/):
 
<img src="images/Lab4b_1.png" width="624"/>

2. Start typing “Recovery Services Vault’ into the search bar at the top of the screen until the Recovery Services Vault resource is available, then click on it:
 
<img src="images/Lab4b_2.png" width="624"/>

3. Click ‘Add’:

<img src="images/Lab4b_3.png" width="624"/>

4. Enter an appropriate name for the Recovery Services Vault and leave all other settings as per screenshot below and then click ‘Create’:
<span style="background-color: #FFFF00">Important – The Recovery Services Vault must be created in a different Azure region (geo) to the VM you wish to protect. If your VM is running in UK South, create the RSV in UK West. If your VM is running in UK West, create the RSV in UK South</span>
 
<img src="images/Lab4b_4.png" width="624"/>

5. Verify the Recovery Services Vault created OK and is now visible in the portal and then click on it:
  
<img src="images/Lab4b_5.png" width="624"/>

6. Click on ‘Site Recovery’ under ‘Getting started’:
 
<img src="images/Lab4b_6.png" width="624"/>

7. Click on ‘Replicate Application’:

<img src="images/Lab4b_7.png" width="624"/>

8. Configure the settings as per the screenshot below replacing ‘Source Location’ and ‘Source Resource Group’ for your own values then click ‘OK’:

<img src="images/Lab4b_8a.png" width="624"/>
<img src="images/Lab4b_8b.png" width="624"/>

9. Select your VM from the list and click ‘OK’:
 
<img src="images/Lab4b_9.png" width="624"/>

10. Default resource names and values are automatically selected for you in the target location. If you wish to edit any of these properties, click ‘Customize’:

<img src="images/Lab4b_10.png" width="624"/>

11. Click ‘Create target resources’:

<img src="images/Lab4b_11.png" width="624"/>

12. Click on ‘Enable Replication’ and monitor the progress via the Azure portal notification(s):

<img src="images/Lab4b_12a.png" width="624"/>
<img src="images/Lab4b_12b.png" width="624"/>

13.	Once replication has been enabled click on ‘Replicated Items’:

<img src="images/Lab4b_13.png" width="624"/>

14. Verify your VM is marked as healthy and click on ‘Enabling Protection’ to monitor progress of replication:

<img src="images/Lab4b_14a.png" width="624"/>
<img src="images/Lab4b_14b.png" width="624"/>

15. Once replication has completed your VM should display ‘Protected’. Click on the name of your VM:

<img src="images/Lab4b_15.png" width="624"/>

16. Click ‘Failover’:
 
<img src="images/Lab4b_16.png" width="624"/>

17. Click ‘Yes’ to the warning about test failover, and then click ‘OK’ at the failover screen:

<img src="images/Lab4b_17a.png" width="624"/>
<img src="images/Lab4b_17b.png" width="624"/>

18. Click the notification in the Azure portal to monitor failover progress:
 
<img src="images/Lab4b_18.png" width="624"/>
<img src="images/Lab4b_18b.png" width="624"/>

19. Verify the failed over VM is now running in the target region:

<img src="images/Lab4b_19.png" width="624"/>

20.	Start typing “Recovery Services Vault’ into the search bar at the top of the screen until the Recovery Services Vault resource is available, then click on it:
 
<img src="images/Lab4b_20.png" width="624"/>

21. Click on ‘Replicated Items:

<img src="images/Lab4b_21.png" width="624"/>

22. Click on your VM which should show a status of ‘Failover Completed’:

<img src="images/Lab4b_22.png" width="624"/>

23. Click ‘Re-protect’:

<img src="images/Lab4b_23.png" width="624"/>
 
24.	Click ‘OK’ at the Re-protect screen:

<img src="images/Lab4b_24a.png" width="624"/>
<img src="images/Lab4b_1b.png" width="624"/>

25. Verify that the VM is replicating back to its original region from its failed over region:

<img src="images/Lab4b_25a.png" width="624"/>
<img src="images/Lab4b_25b.png" width="624"/>

[Lab 3: Creating ARM templates from scratch](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab3.md) | [Lab 5: IaaS Automation](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab5.md)
