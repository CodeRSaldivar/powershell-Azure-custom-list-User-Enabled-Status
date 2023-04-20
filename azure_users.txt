Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope LocalMachine
Install-Module -Name Az -Repository PSGallery -Force
Update-Module -Name Az -Force
Connect-AzAccount
foreach($user in Get-Content -Path c:\users.txt) { Get-AzADUser -Filter "startsWith(UserPrincipalName,'$($user)@md')" -Select 'UserPrincipalName,AccountEnabled' -AppendSelected | Select-Object UserPrincipalName, AccountEnabled }