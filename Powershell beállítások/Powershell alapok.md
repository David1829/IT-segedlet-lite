# Powershell alapok

>[!NOTE]
> OU létrehozása

`New-ADOrganizationalUnit -Name "Nev" -Path "DC=Fixitlater,DC=com" -ProtectedFromAccidentalDeletion $false`

>[!NOTE]
> Csoport létrehozása

`New-ADGroup -Name "Nev" -SamAccountName Nev -GroupCategory Security -GroupScope Global -DisplayName "Nev" -Path "OU=Nev,DC=Fixitlater,DC=com" -Description "Nev"`

>[!NOTE]
> User hozzáadása

`$password = ConvertTo-SecureString "Password123" -AsPlainText -Force`

`New-ADUser -Name "Nev Nev" -AccountPassword $password -SamAccountName "nev" -Path "OU=Nev,DC=Fixitlater,DC=com"`

>[!NOTE]
> User hozzáadása csoporthoz

`Add-ADGroupMember -Identity "Csoportnev" -Members nev`

>[!NOTE]
> Nem hitelesített gép hozzáadása

`New-ADComputer -Name "Nev" -SamAccountName "Nev$" -Path "OU=Nev,DC=Fixitlater,DC=com" -Enabled $true`

>[!NOTE]
> IIS telepitese

`Install-WindowsFeature -name Web-Server -IncludeManagementTools`
