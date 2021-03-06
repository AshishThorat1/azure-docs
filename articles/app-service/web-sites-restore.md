---
title: Restore an app in Azure
description: Learn how to restore your app from a backup.
services: app-service
documentationcenter: ''
author: cephalin
manager: erikre
editor: jimbe

ms.assetid: 4444dbf7-363c-47e2-b24a-dbd45cb08491
ms.service: app-service
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/06/2016
ms.author: cephalin

---
# Restore an app in Azure
This article shows you how to restore an app in [Azure App Service](../app-service/app-service-web-overview.md)
that you have previously backed up (see [Back up your app in Azure](web-sites-backup.md)). You can restore your app
with its linked databases on-demand to a previous state, or create a new app based on one of
your original app's backup. Azure App Service supports the following databases for backup and restore:
- [SQL Database](https://azure.microsoft.com/en-us/services/sql-database/)
- [Azure Database for MySQL (Preview)](https://azure.microsoft.com/en-us/services/mysql)
- [Azure Database for PostgreSQL (Preview)](https://azure.microsoft.com/en-us/services/postgres)
- [ClearDB MySQL](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/SuccessBricksInc.ClearDBMySQLDatabase?tab=Overview)
- [MySQL in-app](https://blogs.msdn.microsoft.com/appserviceteam/2017/03/06/announcing-general-availability-for-mysql-in-app)

Restoring from backups is available to apps running in **Standard** and **Premium** tier. For information about scaling
up your app, see [Scale up an app in Azure](web-sites-scale.md). **Premium** tier allows a greater number of daily
backups to be performed than **Standard** tier.

<a name="PreviousBackup"></a>

## Restore an app from an existing backup
1. On the **Settings** blade of your app in the Azure Portal, click **Backups** to display the **Backups** blade. Then click **Restore**.
   
    ![Choose restore now][ChooseRestoreNow]
2. In the **Restore** blade, first select the backup source.
   
    ![](./media/web-sites-restore/021ChooseSource1.png)
   
    The **App backup** option shows you all the existing backups of the current app, and you can easily select one.
    The **Storage** option lets you select any backup ZIP file from any existing Azure Storage account and container in your subscription.
    If you're trying to restore a backup of another app, use the **Storage** option.
3. Then, specify the destination for the app restore in **Restore destination**.
   
    ![](./media/web-sites-restore/022ChooseDestination1.png)
   
   > [!WARNING]
   > If you choose **Overwrite**, all existing data in your current app is erased and overwritten. Before you click **OK**,
   > make sure that it is exactly what you want to do.
   > 
   > 
   
    You can select **Existing App** to restore the app backup to another app in the same resoure group. Before you use this option, you should have already created another app in your resource group with mirroring database configuration to the one defined in the app backup. You can also Create a **New** app to restore your content to.

4. Click **OK**.

<a name="StorageAccount"></a>

## Download or delete a backup from a storage account
1. From the main **Browse** blade of the Azure portal, select **Storage accounts**. A list of your existing storage accounts is displayed.
2. Select the storage account that contains the backup that you want to download or delete.The blade for the storage account is displayed.
3. In the storage account blade, select the container you want
   
    ![View Containers][ViewContainers]
4. Select backup file you want to download or delete.
   
    ![ViewContainers](./media/web-sites-restore/03ViewFiles.png)
5. Click **Download** or **Delete** depending on what you want to do.  

<a name="OperationLogs"></a>

## Monitor a restore operation
To see details about the success or failure of the app restore operation, navigate to the **Activity Log** blade in the Azure portal.  
 

Scroll down to find the desired restore operation and click to select it.

The details blade displays the available information related to the restore operation.

<!-- ## Next Steps
You can backup and restore App Service apps using REST API. -->


<!-- IMAGES -->
[ChooseRestoreNow]: ./media/web-sites-restore/02ChooseRestoreNow1.png
[ViewContainers]: ./media/web-sites-restore/03ViewContainers.png
