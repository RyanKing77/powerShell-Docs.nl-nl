---
title: Voorbeeld van Runspace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1100d91d-249d-4af7-9854-2d6a423ac2f4
caps.latest.revision: 7
ms.openlocfilehash: 70577a6a42ce26e9791360fa30baae9d7a492daf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082633"
---
# <a name="runspace08-sample"></a>Voorbeeld Runspace08

In dit voorbeeld laat zien hoe u opdrachten en argumenten toevoegen aan de pijplijn met een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object en hoe u de opdrachten synchroon worden uitgevoerd.

## <a name="requirements"></a>Vereisten

In dit voorbeeld is Windows PowerShell 2.0 vereist.

## <a name="demonstrates"></a>Ziet u

In dit voorbeeld ziet u het volgende.

- Het maken van een [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object met behulp van de [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) klasse.

- Het maken van een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object dat de runspace gebruikt.

- Cmdlets toe te voegen aan de pijplijn met de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

- De cmdlets synchroon uitgevoerd.

- Uitpakken van de eigenschappen van de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objecten geretourneerd door de opdracht.

## <a name="example"></a>Voorbeeld

In dit voorbeeld wordt uitgevoerd de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets met behulp van een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace08
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands. The
    /// PowerShell object builds a pipeline that include the get-process cmdlet,
    /// which is then piped to the sort-object cmdlet. Parameters are added to the
    /// sort-object cmdlet to sort the HandleCount property in descending order.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates:
    /// 1. Creating a PowerShell object
    /// 2. Adding individual commands to the PowerShell object.
    /// 3. Adding parameters to the commands.
    /// 4. Running the pipeline of the PowerShell object synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> results; // Holds the result of the pipeline execution.

      // Create the PowerShell object. Notice that no runspace is specified so a
      // new default runspace is used.
      PowerShell powershell = PowerShell.Create();

      // Use the using statement so that we can dispose of the PowerShell object
      // when we are done.
      using (powershell)
      {
        // Add the get-process cmdlet to the pipeline of the PowerShell object.
        powershell.AddCommand("get-process");

        // Add the sort-object cmdlet and its parameters to the pipeline of
        // the PowerShell object so that we can sort the HandleCount property
        //  in descending order.
        powershell.AddCommand("sort-object").AddParameter("descending").AddParameter("property", "handlecount");

        // Run the commands of the pipeline synchronously.
        results = powershell.Invoke();
      }

      // Even after disposing of the PowerShell object, we still
      // need to set the powershell variable to null so that the
      // garbage collector can clean it up.
      powershell = null;

      Console.WriteLine("Process              HandleCount");
      Console.WriteLine("--------------------------------");

      // Display the results returned by the commands.
      foreach (PSObject result in results)
      {
        Console.WriteLine(
                          "{0,-20} {1}",
                          result.Members["ProcessName"].Value,
                          result.Members["HandleCount"].Value);
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-hosttoepassing schrijven](./writing-a-windows-powershell-host-application.md)