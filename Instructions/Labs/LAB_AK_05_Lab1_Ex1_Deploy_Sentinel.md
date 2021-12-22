# Module 5 - Lab 1 - Exercise 1 - Configure your Microsoft Sentinel environment

## Lab scenario

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for setting up the Microsoft Sentinel environment to meet the company requirement to minimize cost, meet compliance regulations, and provide the most manageable environment for your security team to perform their daily job responsibilities.


### Task 1: Initialize the Microsoft Sentinel Workspace.

In this task, you will create an Microsoft Sentinel workspace.

1. Log in to WIN1 virtual machine as Azureuser Admin with the password as provided in the Environment tab.  

1. Open the Edge browser.

1. In the Edge browser, navigate to the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select **+ Create**.

1. Next, In Add Microsoft Sentinel to a workspace page.

1. Select your existed workspace that created in the previous lab, then select **Add**. This could take a few minutes.

1. Navigate around the newly created Microsoft Sentinel workspace to become familiar with the user interface options.


### Task 2: Create a Watchlist.

In this task, you will create a watchlist in Microsoft Sentinel.

1. In the search box at the bottom of the Windows 10 screen, enter *Notepad*.  Select **Notepad** from the results.

1. Type **Hostname** then enter for a new line.

1. In Row 2 through 6 of the notepad, copy the following hostnames, each one in a different line:

```Notepad
Host1
Host2
Host3
Host4
Host5
```

4. From the menu select, **File - Save As**, Name the file *HighValue.csv*.  Then change the file type to **All files(*.*)**.  Then select **Save**.  The file can be saved in the *Documents* folder for the PC.

5. Close Notepad.

6. In Microsoft Sentinel, select the **Watchlist** option in the Configuration area.

7. Select **+ Add new** from the command bar.

8. In the Watchlist wizard, enter the following:

    |General setting|Value|
    |---|---|
    |Name|**HighValueHosts**|
    |Description|**High Value Hosts**|
    |Watchlist alias|**HighValueHosts**|

9. Select, **Next: Source >**.

10. Select **Browse for files** under *Upload file* and browse for the *HighValue.csv* file you just created.

11. In the *SearchKey field* select **Hostname**.

12. Select **Next: Review and Create >**.

13. Review the settings you entered and select **Create**.

14. The screen returns to the watchlists list.

15. Select your new watchlist.  On the right tab, select **View in Log Analytics**.

16. You can now use the _GetWatchlist('HighValueHosts') in your own KQL statements to access the list. The column to reference would be *Hostname*.

```KQL
_GetWatchlist('HighValueHosts')
```

   **Note:** It could take a couple of minutes for the import to complete. You can continue with the following task and come back later to run this command.

17. Close the *Logs* window by selecting the 'x' in the top-right and click **OK** to discard the unsaved edits.


### Task 3: Create a Threat Indicator.

In this task, you will create an indicator in Microsoft Sentinel.

1. In Microsoft Sentinel, select the **Threat intelligence** option in the Threat management area.

1. Select **+ Add New** from the command bar.

1. Review the different indicator types available in the *Types* dropdown. Select the **domain-name**. Enter your initials in the Domain box. An example would be *fmg.com*.

1. For the *Threat types*, select **malicious-activity**.

1. For the *Name*, enter the same value used for the Domain. An example would be *fmg.com*.

1. Set the *Valid from* field to today's date.

1. Select **Apply**.

    **Note:** It could take a couple of minute for the indicator to appear.

1. Select the **Logs** option in the General area. You may need to disable the "Always show queries" option and close the *Queries* window to get run the statements.

1. Run the following KQL statement.

```KQL
ThreatIntelligenceIndicator
```
Scroll the results to the right to see the DomainName column. You can also run the following KQL statement to just see the DomainName column.  

```KQL
ThreatIntelligenceIndicator
| project DomainName
```

## You have completed the lab.
