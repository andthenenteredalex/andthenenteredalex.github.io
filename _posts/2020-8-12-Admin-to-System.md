---
categories: ['welcome']
published:false
---


# Run an executable as system from an Administrative account and bypass UAC prompt

With administrative access to a computer running Windows, it is trivial to run an executable as system. 

Here's how.

Windows Task Scheduler. We've all used it. If you define the user to run the task as System, you can run the task manually from an Administrator account. Administrative rights are required to create the task to run using the system account.

My regular user Burt does not have administrative rights because Burt does not need them. Burt does not have the option to run a task as System, the option throws an error, however Burt does still have the rights required to create a task.
![useful image331]({{ site.url }}/images/Burt1.PNG)

If a user has Admin rights, opening Task Scheduler will automatically elevate due to the presence of the "highestAvailable" statement in the mmc.exe manifest. Explanations asInvoker and uiAccess are out of scope and will likely be a future blog post, though ample write ups on this functionality in Windows are already available.
In order to run the task programatically via Powershell though, even an administrative user must run an elevated powershell or cmd prompt as these executables do not automatically elevate due to the asInvoker statement in their manifests.

But if administrative user Alex creates a task to run an executable as System, who is able to run the task, and hence the executable? (Make sure the "Allow task to be run on demand" box is checked.)

Regular user Burt is not able to, even if he is explicitly granted access to the tasks folder %systemroot%\system32\tasks. 

Neither regular user Burt nor Administrative user Alex is able to run the task from an unelevated powershell window, and Burt cannot run the task from Powershell or Task Scheduler.
We can see why if we look at the privileges of the tokens for Burt's powershell process and Alex's. Alex's unelevated prompt and Burt's prompts are identical, yet it's easy to see the extra privileges associated with an elevated prompt run by Alex.
![useful image331]({{ site.url }}/images/burtprivileges.PNG)
![useful image331]({{ site.url }}/images/alextokens.PNG)


Just run `schtasks /run /tn "whoami test"`.
![useful image331]({{ site.url }}/images/run.PNG)
But when powershell is run elevated (with the higher integrity token) by Alex, the task runs as System. 

We can prove this. For the purposes of this example we will run a powershell script that writes the results from a whoami /all to a text file. 
The script:

`whoami /all | Out-File -FilePath C:\users\Alex\whoami.log`


![useful image331]({{ site.url }}/images/whoamiresults.PNG)

If we run the task as a different user, say, for example, Alex, we can see the results of that output as well.


I'm going to keep journeying down this road.

This exercise was performed on a fully patched Windows 1903 system.

Until next time and thanks for reading.


Alex
