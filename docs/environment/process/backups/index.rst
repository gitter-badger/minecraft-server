Ablauf Backup Prozess
========================


.. uml::

   @startuml
   participant User

   User -> "BackupNode" as BACKUPNODE: triggerBackup
   activate BACKUPNODE

   BACKUPNODE -> "GameServer" as GAMESERVER: start the backup
   activate GAMESERVER


   GAMESERVER --> BACKUPNODE: world data loadet
   deactivate GAMESERVER
   activate BACKUPNODE
   note left : start region fixer


   BACKUPNODE -> "archive storage" as ARCHIVESTORAGE: upload backup to archive
   deactivate BACKUPNODE
   activate ARCHIVESTORAGE

   ARCHIVESTORAGE --> BACKUPNODE: backup archived
   deactivate ARCHIVESTORAGE

   BACKUPNODE -> User: Finish
   deactivate BACKUPNODE

   @enduml
