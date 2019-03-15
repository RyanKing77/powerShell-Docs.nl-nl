---
title: Cmdlet Sets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcf0739e-920e-4dd8-afca-2c6d6927bc2a
caps.latest.revision: 10
ms.openlocfilehash: e9c59474b7e2bbc07166df8a8b4fa8099edd360f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849047"
---
# <a name="cmdlet-sets"></a><span data-ttu-id="29cc0-102">Cmdlet-reeksen</span><span class="sxs-lookup"><span data-stu-id="29cc0-102">Cmdlet Sets</span></span>

<span data-ttu-id="29cc0-103">Bij het ontwerpen van uw cmdlets, kunnen er gevallen waarin u verschillende acties uitvoeren op de dezelfde hoeveelheid gegevens.</span><span class="sxs-lookup"><span data-stu-id="29cc0-103">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="29cc0-104">Bijvoorbeeld, moet u mogelijk ophalen en het instellen van gegevens of het starten en stoppen van een proces.</span><span class="sxs-lookup"><span data-stu-id="29cc0-104">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="29cc0-105">Hoewel u maken van afzonderlijke cmdlets wilt voor het uitvoeren van elke actie, moet het ontwerp van de cmdlet een basisklasse die de klassen voor de afzonderlijke cmdlets zijn afgeleid bevatten.</span><span class="sxs-lookup"><span data-stu-id="29cc0-105">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="29cc0-106">De volgende zaken waarmee u rekening moet houden bij het implementeren van een basisklasse.</span><span class="sxs-lookup"><span data-stu-id="29cc0-106">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="29cc0-107">Algemene parameters die worden gebruikt door alle afgeleide cmdlets in de basisklasse declareren.</span><span class="sxs-lookup"><span data-stu-id="29cc0-107">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="29cc0-108">Cmdlet-specifieke parameters toevoegen aan de juiste cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="29cc0-108">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="29cc0-109">De juiste invoer verwerken methode in de basisklasse overschrijven.</span><span class="sxs-lookup"><span data-stu-id="29cc0-109">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="29cc0-110">Declareer de [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) kenmerk op alle klassen van de cmdlet, maar niet declareren op de basisklasse.</span><span class="sxs-lookup"><span data-stu-id="29cc0-110">Declare the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="29cc0-111">Implementeer een [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) of [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasse waarvan de naam en beschrijving weerspiegelt de sets met cmdlets.</span><span class="sxs-lookup"><span data-stu-id="29cc0-111">Implement a [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="29cc0-112">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="29cc0-112">Example</span></span>

<span data-ttu-id="29cc0-113">Het volgende voorbeeld ziet de implementatie van een basisklasse die wordt gebruikt door Get-Proc en de cmdlet Stop-Proc die zijn afgeleid van de dezelfde basisklasse.</span><span class="sxs-lookup"><span data-stu-id="29cc0-113">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace.

namespace Microsoft.Samples.PowerShell.Commands
{

  #region ProccessCommands

  /// <summary>
  /// This class implements a Stop-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>
  [Cmdlet(VerbsLifecycle.Stop, "Proc", SupportsShouldProcess = true)]
  public class StopProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      if (ShouldProcess(process.ProcessName, "Stop-Proc"))
      {
        process.Kill();
      }
    }
  }

  /// <summary>
  /// This class implements a Get-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>

  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      WriteObject(process);
    }
  }

  /// <summary>
  /// This class is the base class that defines the common
  /// functionality used by the Get-Proc and Stop-Proc
  /// cmdlets.
  /// </summary>
  public class BaseProcCommand : Cmdlet
  {
    #region Parameters

    // Defines the Name parameter that is used to
    // specify a process by its name.
    [Parameter(
               Position = 0,
               Mandatory = true,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true
    )]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    // Defines the Exclude parameter that is used to
    // specify which processes should be excluded when
    // the cmdlet performs its action.
    [Parameter()]
    public string[] Exclude
    {
      get { return excludeNames; }
      set { excludeNames = value; }
    }
    private string[] excludeNames = new string[0];
    #endregion Parameters

    public virtual void ProcessObject(Process process)
    {
      throw new NotImplementedException("This method should be overridden.");
    }

    #region Cmdlet Overrides
    // <summary>
    // For each of the requested process names, retrieve and write
    // the associated processes.
    // </summary>
    protected override void ProcessRecord()
    {
      // Set up the wildcard chracters used in resolving
      // the process names.
      WildcardOptions options = WildcardOptions.IgnoreCase |
                                WildcardOptions.Compiled;

      WildcardPattern[] include = new WildcardPattern[Name.Length];
      for (int i = 0; i < Name.Length; i++)
      {
        include[i] = new WildcardPattern(Name[i], options);
      }

      WildcardPattern[] exclude = new WildcardPattern[Exclude.Length];
      for (int i = 0; i < Exclude.Length; i++)
      {
        exclude[i] = new WildcardPattern(Exclude[i], options);
      }

      foreach (Process p in Process.GetProcesses())
      {
        foreach (WildcardPattern wIn in include)
        {
          if (wIn.IsMatch(p.ProcessName))
          {
            bool processThisOne = true;
            foreach (WildcardPattern wOut in exclude)
            {
              if (wOut.IsMatch(p.ProcessName))
              {
                processThisOne = false;
                break;
              }
            }
            if (processThisOne)
            {
              ProcessObject(p);
            }
            break;
          }
        }
      }
    }
    #endregion Cmdlet Overrides
  }
    #endregion ProcessCommands
}
```

## <a name="see-also"></a><span data-ttu-id="29cc0-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="29cc0-114">See Also</span></span>

[<span data-ttu-id="29cc0-115">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="29cc0-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)