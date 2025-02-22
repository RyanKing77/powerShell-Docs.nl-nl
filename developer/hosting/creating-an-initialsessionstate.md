---
title: Het maken van een InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263831"
---
# <a name="creating-an-initialsessionstate"></a>Een InitialSessionState maken

PowerShell-opdrachten uitvoeren in een runspace.
Voor het hosten van PowerShell in uw toepassing, moet u een [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.
Elke runspace heeft een [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) die zijn gekoppeld aan dit object.
De InitialSessionState Hiermee geeft u de kenmerken van de runspace, zoals welke opdrachten, variabelen en -modules beschikbaar voor deze runspace zijn.

## <a name="create-a-default-initialsessionstate"></a>Een standaard InitialSessionState maken

De [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) en [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methoden van de **InitialSessionState** klasse kan worden gebruikt voor het maken van een **InitialSessionState**object.
De **CreateDefault** methode maakt u een **InitialSessionState** met alle van de ingebouwde opdrachten geladen, terwijl de **CreateDefault2** methode alleen de opdrachten wordt geladen vereist voor de host PowerShell (de opdrachten in de module Microsoft.PowerShell.Core).

Als u wilt de opdrachten die beschikbaar zijn in uw hosttoepassing verder te beperken die u wilt maken van een beperkte runspace.
Zie voor meer informatie, [het maken van een beperkte runspace](creating-a-constrained-runspace.md).

De volgende code toont het maken van een **InitialSessionState**, deze toewijzen aan een runspace, opdrachten toevoegen aan de pijplijn in deze runspace en aanroepen van de opdrachten.
Zie voor meer informatie over het toevoegen en aanroepen van opdrachten [toevoegen en aanroepen van opdrachten](adding-and-invoking-commands.md).

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a>Zie ook

[Het maken van een beperkte runspace](creating-a-constrained-runspace.md)

[Toe te voegen en aan te roepen opdrachten](adding-and-invoking-commands.md)
