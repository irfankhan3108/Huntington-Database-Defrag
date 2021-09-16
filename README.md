# Huntington-Database-Defrag
HMG Database is about 1.23 TB so need to defrag it
#
New-MoveRequest "bh@huntingtongroup.com" -TargetDatabase HMG01 -Priority Highest -BadItemLimit 50
#
Get-MoveRequest | Get-MoveRequestStatistics
#
Remove-MoveRequest -Identity "Joyce Sanchez"
#
Get-MailboxStatistics -Identity "David Valle" | select -Property DisplayName, TotalItemSize
#
New-MailboxExportRequest -ContentFilter {(Received -lt '12/31/2019')} -Mailbox "HWalker" -Name HWalkerexp -FilePath \\HMG-DC01\E\PSTs\HWalker.pst
#
Search-Mailbox -Identity HWalker -SearchQuery 'Received<12/31/2019' -DeleteContent -Force
#
New-MailboxExportRequest -Mailbox MTGInfo -FilePath \\HMG-DC01\E\PSTs\MTGInfo.PST
#
