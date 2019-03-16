---
title: Schrijven van een provider artikel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058183"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="34535-102">Een itemprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="34535-102">Writing an item provider</span></span>

<span data-ttu-id="34535-103">Dit onderwerp wordt beschreven hoe u voor het implementeren van de methoden van een Windows PowerShell-provider die openen en te bewerken van items in het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="34535-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="34535-104">Als u voor toegang tot items, een provider moet zijn afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="34535-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="34535-105">De provider in de voorbeelden in dit onderwerp maakt gebruik van een Access-database als de gegevensopslag.</span><span class="sxs-lookup"><span data-stu-id="34535-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="34535-106">Er zijn verschillende methoden en klassen die worden gebruikt om te communiceren met de database.</span><span class="sxs-lookup"><span data-stu-id="34535-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="34535-107">Zie voor het complete voorbeeld met de Help-methoden, [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="34535-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="34535-108">Zie voor meer informatie over Windows PowerShell-providers, [overzicht van Windows PowerShell-Provider](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34535-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="34535-109">Implementeren van item methoden</span><span class="sxs-lookup"><span data-stu-id="34535-109">Implementing item methods</span></span>

<span data-ttu-id="34535-110">De [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse beschrijft de verschillende methoden die kunnen worden gebruikt voor toegang tot en manipuleren van de items in een gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="34535-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="34535-111">Zie voor een volledige lijst van deze methoden, [ItemCmdletProvider methoden](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="34535-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="34535-112">In dit voorbeeld zullen we vier van deze methoden implementeren.</span><span class="sxs-lookup"><span data-stu-id="34535-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="34535-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) opgehaald van een item in een opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="34535-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="34535-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) stelt de waarde van het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="34535-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="34535-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) wordt gecontroleerd of er een item in het opgegeven pad bestaat.</span><span class="sxs-lookup"><span data-stu-id="34535-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="34535-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) controleert of een pad om te zien als het wordt toegewezen aan een locatie in het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="34535-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="34535-117">In dit onderwerp bouwt voort op de informatie in [Quick Start Windows PowerShell-Provider](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="34535-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="34535-118">In dit onderwerp heeft geen betrekking op de basisprincipes van het instellen van een provider-project, of het implementeren van de methoden die zijn overgenomen van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse die u maakt en schijven verwijderen.</span><span class="sxs-lookup"><span data-stu-id="34535-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="34535-119">De providerklasse declareren</span><span class="sxs-lookup"><span data-stu-id="34535-119">Declaring the provider class</span></span>

<span data-ttu-id="34535-120">Declareer de provider worden afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse en opmaken met de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="34535-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="34535-121">GetItem implementeren</span><span class="sxs-lookup"><span data-stu-id="34535-121">Implementing GetItem</span></span>

<span data-ttu-id="34535-122">De [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) door de PowerShell-engine wordt aangeroepen wanneer een gebruiker roept de [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet uit op uw de provider.</span><span class="sxs-lookup"><span data-stu-id="34535-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="34535-123">De methode retourneert het item in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="34535-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="34535-124">In het voorbeeld van de database toegang met de methode gecontroleerd of het item het station zelf, een tabel in de database, of een rij in de database wordt.</span><span class="sxs-lookup"><span data-stu-id="34535-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="34535-125">De methode verzendt het item naar de PowerShell-engine door het aanroepen van de [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) methode.</span><span class="sxs-lookup"><span data-stu-id="34535-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a><span data-ttu-id="34535-126">SetItem implementeren</span><span class="sxs-lookup"><span data-stu-id="34535-126">Implementing SetItem</span></span>

<span data-ttu-id="34535-127">De [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode wordt aangeroepen door het aanroepen van de PowerShell-engine als een gebruiker roept de [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet .</span><span class="sxs-lookup"><span data-stu-id="34535-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="34535-128">De waarde van het item wordt ingesteld op het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="34535-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="34535-129">In het voorbeeld van de database toegang tot het verstandig om de waarde van een item alleen als dit item een rij is, genereert de methode [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) wanneer het item is niet een rij.</span><span class="sxs-lookup"><span data-stu-id="34535-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a><span data-ttu-id="34535-130">ItemExists implementeren</span><span class="sxs-lookup"><span data-stu-id="34535-130">Implementing ItemExists</span></span>

<span data-ttu-id="34535-131">De [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) methode wordt aangeroepen door de PowerShell-engine als een gebruiker roept de [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="34535-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="34535-132">De methode bepaalt of er een item in het opgegeven pad is.</span><span class="sxs-lookup"><span data-stu-id="34535-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="34535-133">Als het item bestaat, de methode geeft deze terug naar de PowerShell-engine door het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="34535-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a><span data-ttu-id="34535-134">IsValidPath implementeren</span><span class="sxs-lookup"><span data-stu-id="34535-134">Implementing IsValidPath</span></span>

<span data-ttu-id="34535-135">De [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) methode wordt gecontroleerd of het opgegeven pad een ongeldige syntaxis voor de huidige provider is.</span><span class="sxs-lookup"><span data-stu-id="34535-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="34535-136">Er wordt niet gecontroleerd of een item in het pad bestaat.</span><span class="sxs-lookup"><span data-stu-id="34535-136">It does not check whether an item exists at the path.</span></span>

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a><span data-ttu-id="34535-137">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="34535-137">Next steps</span></span>

<span data-ttu-id="34535-138">Een typische real-world-provider is kan ondersteunen van items die andere items bevatten, en van het verplaatsen van items uit een pad naar de andere in het station.</span><span class="sxs-lookup"><span data-stu-id="34535-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="34535-139">Zie voor een voorbeeld van een provider die ondersteuning biedt voor containers, [schrijven van een provider container](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="34535-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="34535-140">Zie voor een voorbeeld van een provider die ondersteuning biedt voor items verplaatsen [schrijven van een provider navigatie](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="34535-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34535-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="34535-141">See Also</span></span>

[<span data-ttu-id="34535-142">Schrijven van een container-provider</span><span class="sxs-lookup"><span data-stu-id="34535-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="34535-143">Schrijven van een provider navigatie</span><span class="sxs-lookup"><span data-stu-id="34535-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="34535-144">Overzicht van Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="34535-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)