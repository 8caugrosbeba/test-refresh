## How to Delete Orphaned SIDs in ACLs

  
# How to Delete Orphaned SIDs in ACLs
 
A SID (security identifier) is a unique number that identifies a user, group, or computer account in Windows. Sometimes, when an account is deleted or renamed, the SID remains in the access control list (ACL) of a file or folder, causing an orphaned SID. Orphaned SIDs can cause security issues and clutter the ACLs, so it is recommended to remove them periodically.
 
## Delete orphaned SIDs in ACLs


[**Download File**](https://lomasmavi.blogspot.com/?c=2tLdtn)

 
There are different ways to delete orphaned SIDs in ACLs, depending on the type of resource and the level of access you have. Here are some common methods:
 
- Using File Explorer: If you have administrator privileges, you can use File Explorer to browse to the file or folder, right-click and select Properties, then go to the Security tab and remove the undesired user[^1^].
- Using PowerShell: If you have PowerShell access, you can use the Get-Acl and Set-Acl cmdlets to get and modify the ACLs of a file or folder. You can also use the Remove-OrphanedSidPermission function from the ALITAJRAN module to remove orphaned SIDs from a mailbox[^2^].
- Using icacls: If you have command-line access, you can use the icacls tool to display and modify the ACLs of a file or folder. You can use the /remove switch to remove a specific SID from an ACL.

For more information on how to delete orphaned SIDs in ACLs, you can refer to the following resources:

1. [Can't remove ACL entry that refers to orphaned SID](https://stackoverflow.com/questions/66626020/cant-remove-acl-entry-that-refers-to-orphaned-sid)
2. [Remove orphaned SIDs with PowerShell - ALI TAJRAN](https://www.alitajran.com/remove-orphaned-sids/)
3. [icacls | Microsoft Docs](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/icacls)

An access control list (ACL) is a list of permissions that determines who can access a file or folder and what actions they can perform. An ACL consists of one or more access control entries (ACEs), each of which specifies a user or group and a set of permissions. For example, an ACL for a file might have an ACE that grants read and write access to the owner, another ACE that grants read-only access to a group, and another ACE that denies access to everyone else.
 
When you delete or rename a user or group account, the corresponding SID in the ACL becomes invalid and does not match any existing account. This is called an orphaned SID. Orphaned SIDs can cause problems such as:

- Reducing the security of the file or folder, as anyone who knows the orphaned SID can impersonate it and gain access.
- Increasing the size and complexity of the ACL, making it harder to manage and audit.
- Slowing down the performance of the file system, as it takes longer to process the ACL.

Therefore, it is advisable to delete orphaned SIDs in ACLs regularly, using one of the methods described above.

One way to find orphaned SIDs in ACLs is to use the AccessChk tool from Sysinternals. AccessChk is a command-line utility that shows the effective permissions and access rights for files, folders, registry keys, processes, and more. You can use the -s switch to scan all subfolders and files, and the -n switch to show only objects that have no corresponding account name. For example, the following command will show all files and folders in C:\Temp that have orphaned SIDs:

    accesschk -s -n C:\Temp

Another way to find orphaned SIDs in ACLs is to use PowerShell. You can use the Get-Acl cmdlet to get the ACL of a file or folder, and the Translate method to try to translate a SID to a user or group name. If the translation fails, it means the SID is orphaned. For example, the following script will show all files and folders in C:\Temp that have orphaned SIDs:

    $path = "C:\Temp"
    Get-ChildItem -Path $path -Recurse | ForEach-Object  ForEach-Object 
            try 
                $_.IdentityReference.Translate([System.Security.Principal.NTAccount])
            
            catch 
                Write-Output "$($_.FileSystemRights) on $($_.Path) for $($_.IdentityReference)"

 0f148eb4a0
