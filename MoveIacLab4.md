# Lab 4: Failover between regions

# Part 1: Use Azure Traffic Manager to provide geo-redundancy for a Web App

1. Load Visual Studio (Community Edition available for free here)
 
<img src="images/Lab4_1.jpg" width="312"/>

2. Click File > New > Project

<img src="images/Lab4_2.jpg" width="312"/>

3. Choose ‘ASP.net Core Web Application’

<img src="images/Lab4_3.jpg" width="312"/>

4. Give the project a name that’s easy to identify
 
<img src="images/Lab4_4.jpg" width="312"/>

5. Choose ‘Web Application (Model-View-Controller)’ and untick ‘Enable Docker Support’ and ‘Configure for HTTPS’, then click ‘OK’

<img src="images/Lab4_5.jpg" width="312"/>

6. If it doesn’t display automatically, click ‘View > Solution Explorer’
 
<img src="images/Lab4_6.jpg" width="312"/>

7. In the Solution Explorer on the right hand side of the screen, expand Views > Home and click on ‘Index.cshtml’

<img src="images/Lab4_7.jpg" width="312"/>

8. Select all of the default text in the left-hand pane of Visual Studio and delete it

<img src="images/Lab4_8.jpg" width="312"/>

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
	 
<img src="images/Lab4_9.jpg" width="312"/>

10. Click ‘Save’

<img src="images/Lab4_10.jpg" width="312"/>

11. In ‘Solution Explorer’ right click your Web App and choose ‘Publish’
 
 












12. Choose ‘App Service’ and ‘Create New’ from the options and then click ‘Publish’ (note if you’ve not logged into an Azure subscription already you may be prompted to do so)
 













13. Choose an ‘App Name’ that is easily identifiable and choose an appropriate Resource Group for your web app, alternatively you can create a new one. For ‘Hosting Plan’ select ‘New’ and choose an App Service Plan name that is easily identifiable. Choose a location of ‘UK South’ and a size of ‘S1’. Then click ‘Create’
 

 



14. In the Azure portal, type in ‘App Services’ in the search bar at the top until the ‘App Services’ resource is displayed and then click it
 
15. Verify your Web App appears
 

16. Click on your Web App to display the overview dashboard

 

17. Click on ‘SSL Settings’
 


18. Set ‘HTTPS Only’ to ‘Off’
 

19. Click on ‘Overview’ on the left-hand menu for the Web App
 

20. Click on ‘Restart’
 

21. Open a new InPrivate / Incognito / Private Browsing tab in your browser and paste in the HTTP address for your web app. Verify you can see your edited home page
 
22. Repeat all previous steps to create another Web App and another App Service plan using names that easily identify them being different to the existing ones. 
IMPORTANT – Ensure to choose UK West as the region for your App Service plan
Example below:

<!DOCTYPE html>
<html>
<body>

<h1>This is <name>’s WebApp</h1>

<p>This is WebApp 2</p>

</body>
</html>


 
 

 
23. You should now have 2 Web Apps, both with SSL disabled, running in different App Service Plans in different geographical regions
 

 
	 







24. In the Azure portal, type ‘Traffic Manager’ in the search box at the top until ‘Traffic Manager profiles’ is displayed, then click on it
 

25. Click ‘Add’
 












26. Choose an appropriate name for this Traffic Manager profile, leaving all other settings as per screenshot below and then click ‘Create’
 

 

27. Once the profile has been created click on it
 

 
28. Click on ‘Configuration’
 















29. Edit the settings to reflect the screenshot below and click ‘Save’
 












30. Click on ‘Endpoints’
 

31. Click on ‘Add’
 







32. Add the first Web App you created ensuring you choose ‘App Service’ on the drop-down menu and click ‘OK’
 














33. Repeat the process for your second Web App (note the priority is auto set to 2)
 

34. Verify that both end points show as ‘Online’ under ‘Monitor Status’ (note you may need to wait a brief period whilst the initial probe is carried out during which time you will see ‘Checking endpoint’)
 

35. In the ‘Overview’ screen of your TM profile, note the DNS name that has been created
 


36. If you are able, log onto your DNS registrar / provider for your domain, and create a CNAME DNS record that references the DNS name of your traffic manager identified in the previous step
 

37. Verify that name resolution works correctly and your custom domain resolves to the traffic manager DNS name
 







38. In the Azure portal, type ‘App Service’ in the search bar until you see the ‘App Services’ resource appear and click on it

 


39. Click on your first Web App
 

40. Click on ‘Custom Domains’ from the left-hand menu
 


41. Click on ‘Add hostname’
 
42. Type the DNS CNAME record from step #36 and click ‘Validate’
 











43. Verify that domain validation passed successfully and then click ‘Add hostname’
 

44. Repeat steps #40 thru #43 for your second Web App










45. Open a new InPrivate / Incognito / Private Browsing tab in your browser and paste in the HTTP address for your custom traffic manager record. Verify connectivity to your first Web App

 
46. In the Azure portal, on the overview page for your first Web App click ‘Stop’
 


47. Still in the Azure portal, start typing ‘Traffic Manager’ in the search box at the top until the ‘Traffic Manager profiles’ resource is displayed, then click it

 





48. Click on ‘Endpoints’
 

49. Verify that your first Web App is marked as ‘Stopped’
 

50. Open a new InPrivate / Incognito / Private Browsing tab in your browser and paste in the HTTP address for your custom traffic manager record. Verify connectivity to your second Web App
 




[Lab 3: Creating ARM templates from scratch](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab3.md) | [Lab 5: IaaS Automation](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab5.md)
