---
title: Cached Mode is Required for this Mailbox
author: bradhugh
ms.author: bradhugh
manager: tpolitis
audience: ITPro 
ms.topic: article 
ms.service: remote-connect-tool
ms.localizationpriority: medium
description: 
---

<div data-xmlns="https://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="https://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="https://msdn.microsoft.com/">

<div data-asp="https://msdn2.microsoft.com/asp">

# Cached Mode is Required for this Mailbox

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2011-02-10_

The Microsoft Remote Connectivity Analyzer queries the Exchange Server and attempts to log on to the Information Store using online mode. The Microsoft Remote Connectivity Analyzer tool displays the following warning when the Exchange server has been configured to force connections using Cached Exchange mode.

"Store logon returned ecCachedModeRequired 1249. Cached Mode is required for this mailbox."

Exchange 2007 and Exchange 2010 administrators can prevent users from connecting using online mode by using the Set-CasMailbox cmdlet to set the MAPIBlockOutlookNonCachedMode attribute to True. If cached mode is required, then users who try to connect using an Outlook profile configured for online mode will receive the following error message.

"Your Exchange Server administrator has blocked the version of Outlook that you are using. Contact your administrator for assistance."

<div>

## For More Information

The warning generated by the Microsoft Remote Connectivity Analyzer isn't necessarily indicative of a problem. Forcing Cached Exchange Mode is a legitimate configuration option. However, if you ran Microsoft Remote Connectivity Analyzer because you have Outlook clients who are unable to successfully connect, then you should confirm whether those clients can successfully connect using Cached Exchange mode.

**To verify the profile settings for Outlook and confirm whether the Cached Exchange Mode checkbox is checked**

1.  Click Start, click Run, type control, and then click OK.

2.  Double-click Mail, and then click Show Profiles.

3.  Select your profile, and then click Properties.

4.  Click E-mail Accounts, select View or Change Existing E-mail Accounts, and then click Next.

5.  Select the Exchange account, and then click Change.

6.  Click to select the Use Cached Exchange Mode check box.

**To Determine whether Cached Exchange Mode is required for your mailbox using the Exchange Management Shell**

1.  Run the following command:
    
        Get-CasMailbox MailboxName | fl MapiBlockOutlookNonCachedMode

If this command returns True, then you must connect to Exchange 2007 or Exchange 2010 using Cached Exchange Mode. Alternatively, you can disable the requirement of using Cached Exchange Mode for the user.

**To allow a user to connect without using Cached Mode using the Exchange Management Shell**

1.  Run the following command:
    
        Set-CasMailbox MailboxName -MapiBlockOutlookNonCachedMode:$false

For more information, see Microsoft Knowledge Base article, "When you use Outlook with an Exchange 2007 mailbox, you cannot connect to Exchange 2007, and you receive an error message" ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=924625](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=924625)).

For information about the Set-CasMailbox cmdlet, see [Set-CASMailbox](https://technet.microsoft.com/library/bb125264.aspx)

</div>

</div>

<span> </span>

</div>

</div>

</div>

