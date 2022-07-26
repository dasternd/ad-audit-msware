[Главная](/) - Скрипты PowerShell

# Используемые PS-скрипты для сбора данных для аудита Active Directory

Для проведения аудита Active Directory используются следующие PS-скрипты:
- [Prerequisite.ps1](/PowerShell/Prerequisite.ps1)
- [Start-AuditAD.ps1](/PowerShell/Start-AuditAD.ps1)


## Prerequisite.ps1

Для сбора необходимой информации в автоматическом режиме необходимо убедится что выполнены все [требования](/Prerequisite/).

Запуск скрипта Prerequisite.ps1 позволит определить готовность окружения и инфраструктуры к сбору информации для проведения аудита Active Directory.

По завршению скрипта будет сформирован лог-файл (**Prerequisite-2022_08_08_19_00.log**), где ***2022_08_08_19_00*** является дата и время запуска скрипта.

пример содержимого скрипта:
```log
[08.08.22 19:00:09] List Domain Controllers
[08.08.22 19:00:10] [OK] Test connect to domain controller DC1.MSware.ru is OK
[08.08.22 19:00:10] [OK] Test connect to domain controller DC2.MSware.ru is OK
[08.08.22 19:00:10] [Info] Total Domain Controllers 2
[08.08.22 19:00:10] Version PowerShell
[08.08.22 19:00:11] [Warning] DC1.MSware.ru have PS version 4.0 need update PowerShells to version 5.1
[08.08.22 19:00:11] [OK] DC2.MSware.ru have PS version 5.1.17763.1490 is OK
```

## Start-AuditAD.ps1

Используется для запуска процесса сбора необходимой информации в автоматическом режиме для проведения аудита Active Directory.

По завершению будет создан лог файл **Start-AuditAD-2022_08_08_17_23.log**, где ***2022_08_08_17_23*** является дата и время запуска скрипта.

По окончанию выполнения скрипта, будет создан архивный файл **AuditAD.zip** в котором будут содержаться все файлы с собранными данными по текущей инфраструктуре.

пример содержимого скрипта:
```log
[08.08.22 17:23:01] START AUDIT ACTIVE DIRECTORY
[08.08.22 17:23:01] GET INFORMATION ABOUT WINDOWS EVENTS [ 1 / 9 ]
[08.08.22 17:23:01] [Info] Created new folder to path C:\AuditAD\Events\
[08.08.22 17:23:01] [Info] Connecting to Domain Controller DC1.MSware.ru ...
[08.08.22 17:23:01] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:23:01] [Info] Processing DC1.MSware.ru\Application ...
[08.08.22 17:23:03] [Info] Processing DC1.MSware.ru\System ...
[08.08.22 17:23:06] [Info] Processing DC1.MSware.ru\DFS Replication ...
[08.08.22 17:23:06] [Info] Processing DC1.MSware.ru\Directory Service ...
[08.08.22 17:23:07] [Info] Processing DC1.MSware.ru\DNS Server ...
[08.08.22 17:23:07] [Info] Exporting Windows Events ...
[08.08.22 17:23:11] [OK] Exported Windows Events to C:\AuditAD\Events\Events_DC1.MSware.ru.csv OK
[08.08.22 17:23:11] [Info] Connecting to Domain Controller DC2.MSware.ru ...
[08.08.22 17:23:11] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:23:11] [Info] Processing DC2.MSware.ru\Application ...
[08.08.22 17:23:16] [Info] Processing DC2.MSware.ru\System ...
[08.08.22 17:23:18] [Info] Processing DC2.MSware.ru\DFS Replication ...
[08.08.22 17:23:18] [Info] Processing DC2.MSware.ru\Directory Service ...
[08.08.22 17:23:18] [Info] Processing DC2.MSware.ru\DNS Server ...
[08.08.22 17:23:18] [Info] Exporting Windows Events ...
[08.08.22 17:23:24] [OK] Exported Windows Events to C:\AuditAD\Events\Events_DC2.MSware.ru.csv OK
[08.08.22 17:23:24] START INVENTORY SOFTWARE [ 2 / 9 ]
[08.08.22 17:23:24] [Info] Created new folder to path C:\AuditAD\Inventory\
[08.08.22 17:23:24] [Info] Connecting to Domain Controller DC1.MSware.ru ...
[08.08.22 17:23:24] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:23:24] [Info] Processing Inventory Software DC1.MSware.ru ...
[08.08.22 17:23:24] [Info] Exporting Information about Inventory Software ...
[08.08.22 17:23:24] [OK] Exported Information about Inventory Software to C:\AuditAD\Inventory\InventorySoftware_DC1.MSware.ru.csv OK
[08.08.22 17:23:24] [Info] Connecting to Domain Controller DC2.MSware.ru ...
[08.08.22 17:23:24] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:23:24] [Info] Processing Inventory Software DC2.MSware.ru ...
[08.08.22 17:24:04] [Info] Exporting Information about Inventory Software ...
[08.08.22 17:24:04] [OK] Exported Information about Inventory Software to C:\AuditAD\Inventory\InventorySoftware_DC2.MSware.ru.csv OK
[08.08.22 17:24:04] START INVENTORY HARDWARE [ 3 / 9 ]
[08.08.22 17:24:04] [Info] Connecting to Domain Controller DC1.MSware.ru ...
[08.08.22 17:24:04] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:24:04] [Info] Processing Inventory Hardware ...
[08.08.22 17:24:05] [Info] Connecting to Domain Controller DC2.MSware.ru ...
[08.08.22 17:24:05] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:24:05] [Info] Processing Inventory Hardware ...
[08.08.22 17:24:07] [Info] Exporting Inventory Hardware DC2.MSware.ru ...
[08.08.22 17:24:07] [OK] Exported Information about Inventory Hardware to C:\AuditAD\Inventory\InventoryHardware_DomainControllers.csv OK
[08.08.22 17:24:07] START INVENTORY HOTFIXes [ 4 / 9 ]
[08.08.22 17:24:07] [Info] Connecting to Domain Controller DC1.MSware.ru ...
[08.08.22 17:24:07] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:24:07] [Info] Processing Inventory HotFix DC1.MSware.ru ...
[08.08.22 17:24:07] [Info] Exporting Information about Inventory HotFix ...
[08.08.22 17:24:07] [OK] Exported Information about Inventory HotFix to C:\AuditAD\Inventory\InventoryHotfix_DC1.MSware.ru.csv
[08.08.22 17:24:07] [Info] Connecting to Domain Controller DC2.MSware.ru ...
[08.08.22 17:24:07] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:24:07] [Info] Processing Inventory HotFix DC2.MSware.ru ...
[08.08.22 17:24:09] [Info] Exporting Information about Inventory HotFix ...
[08.08.22 17:24:09] [OK] Exported Information about Inventory HotFix to C:\AuditAD\Inventory\InventoryHotfix_DC2.MSware.ru.csv
[08.08.22 17:24:09] GET INFORMATION ABOUT OS [ 5 / 9 ]
[08.08.22 17:24:09] [Info] Connecting to Domain Controller DC1.MSware.ru ...
[08.08.22 17:24:09] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:24:09] [Info] Processing Get Information about OS DC1.MSware.ru ...
[08.08.22 17:24:09] [OK] Exporting Information about OS
[08.08.22 17:24:09] [OK] Exported Information about OS to C:\AuditAD\Inventory\InfoOS_DC1.MSware.ru.csv
[08.08.22 17:24:09] [Info] Connecting to Domain Controller DC2.MSware.ru ...
[08.08.22 17:24:09] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:24:09] [Info] Processing Get Information about OS DC2.MSware.ru ...
[08.08.22 17:24:13] [OK] Exporting Information about OS
[08.08.22 17:24:13] [OK] Exported Information about OS to C:\AuditAD\Inventory\InfoOS_DC2.MSware.ru.csv
[08.08.22 17:24:13] GET INFORMATION ABOUT INSTALLED WINDOWS FEATURE [ 6 / 9 ]
[08.08.22 17:24:13] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:24:13] [OK] Processing Get Information Installed Windows Feature DC1.MSware.ru
[08.08.22 17:24:15] [Info] Exporting Information about Inventory Windows Feature ...
[08.08.22 17:24:15] [OK] Exported Information about Inventory Windows Feature to C:\AuditAD\Inventory\WindowsFeature_DC1.MSware.ru.csv OK
[08.08.22 17:24:15] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:24:15] [OK] Processing Get Information Installed Windows Feature DC2.MSware.ru
[08.08.22 17:24:16] [Info] Exporting Information about Inventory Windows Feature ...
[08.08.22 17:24:16] [OK] Exported Information about Inventory Windows Feature to C:\AuditAD\Inventory\WindowsFeature_DC2.MSware.ru.csv OK
[08.08.22 17:24:16] START TEST DCDIAG [ 7 / 9 ]
[08.08.22 17:24:16] [Info] Created new folder to path C:\AuditAD\AD\
[08.08.22 17:24:16] [Info] Connecting to Domain Controller DC1.MSware.ru ...
[08.08.22 17:24:16] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:24:16] [Info] Processing Start DCDIAG DC1.MSware.ru ...
[08.08.22 17:24:17] [Info] Exporting Result DCDIAG ...
[08.08.22 17:24:17] [OK] Exporting Result DCDIAG to C:\AuditAD\AD\DCDIAG_DC1.MSware.ru.txt OK
[08.08.22 17:24:17] [Info] Connecting to Domain Controller DC2.MSware.ru ...
[08.08.22 17:24:17] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:24:17] [Info] Processing Start DCDIAG DC2.MSware.ru ...
[08.08.22 17:24:19] [Info] Exporting Result DCDIAG ...
[08.08.22 17:24:19] [OK] Exporting Result DCDIAG to C:\AuditAD\AD\DCDIAG_DC2.MSware.ru.txt OK
[08.08.22 17:24:19] START TEST REPADMIN [ 8 / 9 ]
[08.08.22 17:24:19] [Info] Connecting to Domain Controller DC1.MSware.ru ...
[08.08.22 17:24:19] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:24:19] [Info] Processing Start REPADMIN DC1.MSware.ru ...
[08.08.22 17:24:19] [Info] Exporting Result REPADMIN ...
[08.08.22 17:24:19] [OK] Exported Result REPADMIN to C:\AuditAD\AD\REPADMIN_DC1.MSware.ru.txt OK
[08.08.22 17:24:19] [Info] Connecting to Domain Controller DC2.MSware.ru ...
[08.08.22 17:24:19] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:24:19] [Info] Processing Start REPADMIN DC2.MSware.ru ...
[08.08.22 17:24:19] [Info] Exporting Result REPADMIN ...
[08.08.22 17:24:19] [OK] Exported Result REPADMIN to C:\AuditAD\AD\REPADMIN_DC2.MSware.ru.txt OK
[08.08.22 17:24:19] GET INFORMATION ABOUT DNS [ 9 / 9 ]
[08.08.22 17:24:19] [Info] Connecting to Domain Controller DC1.MSware.ru ...
[08.08.22 17:24:19] [OK] Connected to Domain Controller DC1.MSware.ru is OK
[08.08.22 17:24:19] [Info] Processing Start InfoDNS DC1.MSware.ru ...
[08.08.22 17:24:20] [Info] Exporting Result InfoDNS ...
[08.08.22 17:24:20] [OK] Exported Result InfoDNS to C:\AuditAD\AD\InfoDNS_DC1.MSware.ru.txt OK
[08.08.22 17:24:20] [Info] Connecting to Domain Controller DC2.MSware.ru ...
[08.08.22 17:24:20] [OK] Connected to Domain Controller DC2.MSware.ru is OK
[08.08.22 17:24:20] [Info] Processing Start InfoDNS DC2.MSware.ru ...
[08.08.22 17:24:20] [Info] Exporting Result InfoDNS ...
[08.08.22 17:24:20] [OK] Exported Result InfoDNS to C:\AuditAD\AD\InfoDNS_DC2.MSware.ru.txt OK
```