---
title: Voorbeeld van Runspace04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a04f15-b5d8-475b-ac9c-e75c58ec8933
caps.latest.revision: 8
ms.openlocfilehash: 3cb370cd1bfe9ce7198980cc1c26fafb126d00a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082667"
---
# <a name="runspace04-sample"></a>Voorbeeld Runspace04

In dit voorbeeld laat zien hoe u de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasse voor het uitvoeren van opdrachten, en hoe u afsluitende catch-fouten die worden gegenereerd wanneer de opdrachten uitvoert. Twee opdrachten worden uitgevoerd en de laatste opdracht wordt een parameterargument dat is niet geldig doorgegeven. Als gevolg hiervan geen objecten worden geretourneerd en wordt er een afsluitfout wordt gegenereerd.

## <a name="requirements"></a>Vereisten

In dit voorbeeld is Windows PowerShell 2.0 vereist.

## <a name="demonstrates"></a>Ziet u

In dit voorbeeld ziet u het volgende.

- Het maken van een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

- Opdrachten toe te voegen aan de pijplijn van de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

- Parameter argumenten toevoegen aan de pijplijn.

- De opdrachten aanroepen synchroon.

- Met behulp van [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objecten die u wilt extraheren en weergave-eigenschappen van de objecten die worden geretourneerd door de opdrachten.

- Ophalen en weergeven van foutrecords die zijn gegenereerd tijdens het uitvoeren van de opdrachten.

- Worden vastgelegd en wordt beëindigd uitzonderingen die door de opdrachten weergegeven.

## <a name="example"></a>Voorbeeld

In dit voorbeeld wordt de opdrachten synchroon uitgevoerd in de standaard-runspace geleverd door Windows PowerShell. De laatste opdracht genereert een afsluitfout omdat een parameterargument dat is niet geldig is doorgegeven aan de opdracht. De afsluitfout onderschept en weergegeven.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
          Console.WriteLine("\nThe following non-terminating errors occurred:\n");
          PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
          if (errors != null && errors.Count > 0)
          {
            foreach (ErrorRecord err in errors)
            {
              System.Console.WriteLine("    error: {0}", err.ToString());
            }
          }
        }
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-hosttoepassing schrijven](./writing-a-windows-powershell-host-application.md)