# Lab 2: Work with an ARM template from an existing resource

This lab will step through exporting an ARM template from a virtual machine and then reusing it as Infrastructure as Code in the Azure Portal.

This lab will create a new Virtual Machine in order to keep the steps simpler as the previously created VM will have a large number of paramters related to DSC (a total of 55 parameters).

## Part 1: Export an ARM Template from an existing resource

1. In the [Azure Portal](https://portal.azure.com) (https://portal.azure.com)  go to Create a Resource and select Windows Server DataCenter 2016:

<img src="images/Lab2_0_1.jpg" width="624"/>

2. Create a new resource group (to keep it seperate from the earlier VM), and complete the name, username and password fields. Add the RDP port and then click review and create (i.e. keep all other defaults for storage and networking), then create when the validation is complete:

<img src="images/Lab2_0_2.jpg" width="624"/>

3. Find the Virtual Machine that you created in the previous lab, and select the Export Template blade: 

<img src="images/Lab2_1.jpg" width="624"/>

4. Take a moment to look at the exported ARM template, the parameters and how you could use CLI, Powershell or code to invoke the ARM template. Some resources can't be exported at the moment but you can ignore those warnings for now and then click Add to Library:

<img src="images/Lab2_2.jpg" width="624"/>

5. Give the template a name and optionally a description, and then click Save:

<img src="images/Lab2_3.jpg" width="624"/>

6. Search for templates in the Azure Portal search and select Templates (preview):

<img src="images/Lab2_4.jpg" width="624"/>

7. You should see your template listed and you now have the start of a library of templates from which to create new resources:

<img src="images/Lab2_4_1.jpg" width="624"/>

## Part 2: Creating new resources from templates in the library

1. In the templates click on your newly created template:

<img src="images/Lab2_5.jpg" width="624"/>

2. There are options to edit the template which we'll explore later, but for now select Deploy:

<img src="images/Lab2_6.jpg" width="624"/>

3. This will now create a new VM using the ARM template. Create a new resource group so that you can easily see (and later delete) everything that gets created. Notice that various parameters are exposed for you to override if you wish. You can leave the defaults:

<img src="images/Lab2_7.jpg" width="624"/>

4. Review the terms and conditions at the bottom of the page, check the box and click Purchase:

<img src="images/Lab2_8.jpg" width="624"/>


[Lab 1: Create a virtual machine in the portal](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab1.md) | [Lab 3: Creating ARM templates from scratch](https://github.com/gidavies/MovingToInfraAsCodeLab/blob/master/MoveIacLab3.md)
