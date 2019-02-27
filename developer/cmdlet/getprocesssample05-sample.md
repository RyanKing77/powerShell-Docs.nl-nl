---
title: Voorbeeld van GetProcessSample05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6aebd53f-0610-4959-88b2-42339588c859
caps.latest.revision: 6
ms.openlocfilehash: c3546301cfd77ca40dd4683a3d2fe2d040b7c4a7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850944"
---
# <a name="getprocesssample05-sample"></a><span data-ttu-id="72e35-102">Voorbeeld GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="72e35-102">GetProcessSample05 Sample</span></span>

<span data-ttu-id="72e35-103">In dit voorbeeld ziet u een volledige versie van de cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="72e35-103">This sample shows a complete version of the Get-Proc cmdlet.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="72e35-104">Over het bouwen van het voorbeeld met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72e35-104">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="72e35-105">Open Windows Verkenner en navigeer naar de map GetProcessSample05 onder de map Samples.</span><span class="sxs-lookup"><span data-stu-id="72e35-105">Open Windows Explorer and navigate to the GetProcessSample05 directory under the Samples directory.</span></span>

   <span data-ttu-id="72e35-106">Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="72e35-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample05 folder.</span></span> <span data-ttu-id="72e35-107">De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="72e35-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span></span>

2. <span data-ttu-id="72e35-108">Dubbelklik op het pictogram voor het oplossingsbestand (.sln).</span><span class="sxs-lookup"><span data-stu-id="72e35-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="72e35-109">Hiermee opent u het voorbeeldproject in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72e35-109">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="72e35-110">In de **bouwen** in het menu **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="72e35-110">In the **Build** menu, select **Build Solution**.</span></span>

   <span data-ttu-id="72e35-111">De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.</span><span class="sxs-lookup"><span data-stu-id="72e35-111">The library for the sample will be built in the default \bin or \bin\debug directories.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="72e35-112">Hoe u het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="72e35-112">How to run the sample</span></span>

1. <span data-ttu-id="72e35-113">Maak de volgende modulemap:</span><span class="sxs-lookup"><span data-stu-id="72e35-113">Create the following module folder:</span></span>

   `[user]/documents/windowspowershell/modules/GetProcessSample05`

2. <span data-ttu-id="72e35-114">Kopieer de voorbeeld-assembly naar de modulemap.</span><span class="sxs-lookup"><span data-stu-id="72e35-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="72e35-115">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72e35-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="72e35-116">Voer de volgende opdracht om het laden van de assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="72e35-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

   `Import-module getprossessample05`

5. <span data-ttu-id="72e35-117">Voer de volgende opdracht om uit te voeren van de cmdlet:</span><span class="sxs-lookup"><span data-stu-id="72e35-117">Run the following command to run the cmdlet:</span></span>

   `get-proc`

## <a name="requirements"></a><span data-ttu-id="72e35-118">Vereisten</span><span class="sxs-lookup"><span data-stu-id="72e35-118">Requirements</span></span>

<span data-ttu-id="72e35-119">In dit voorbeeld is Windows PowerShell 2.0 vereist.</span><span class="sxs-lookup"><span data-stu-id="72e35-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="72e35-120">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="72e35-120">Demonstrates</span></span>

<span data-ttu-id="72e35-121">In dit voorbeeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="72e35-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="72e35-122">Het declareren van een cmdlet-klasse met behulp van de Cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="72e35-122">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="72e35-123">Cmdlet-parameter met behulp van de Parameter-kenmerk declareren.</span><span class="sxs-lookup"><span data-stu-id="72e35-123">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="72e35-124">Functies voor parameters opgeven.</span><span class="sxs-lookup"><span data-stu-id="72e35-124">Specifying positions for parameters.</span></span>

- <span data-ttu-id="72e35-125">Op te geven dat parameters duren invoer van de pijplijn voordat kunnen.</span><span class="sxs-lookup"><span data-stu-id="72e35-125">Specifying that parameters can take input from the pipeline.</span></span> <span data-ttu-id="72e35-126">De invoer kan worden uitgevoerd van een object of een waarde van een eigenschap van een object waarvan de de eigenschapsnaam hetzelfde als de naam van de parameter is.</span><span class="sxs-lookup"><span data-stu-id="72e35-126">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="72e35-127">Een kenmerk validatie voor de parameter invoer declareren.</span><span class="sxs-lookup"><span data-stu-id="72e35-127">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="72e35-128">Afhandeling van fouten en uitzonderingen.</span><span class="sxs-lookup"><span data-stu-id="72e35-128">Handling errors and exceptions.</span></span>

- <span data-ttu-id="72e35-129">Foutopsporingsberichten schrijven.</span><span class="sxs-lookup"><span data-stu-id="72e35-129">Writing debug messages.</span></span>

## <a name="example"></a><span data-ttu-id="72e35-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="72e35-130">Example</span></span>

<span data-ttu-id="72e35-131">Dit voorbeeld laat zien hoe u een cmdlet die een lijst weer van de opgegeven processen geeft maken.</span><span class="sxs-lookup"><span data-stu-id="72e35-131">This sample shows how to create a cmdlet that displays a list of specified processes.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Collections.Generic;
    using System.Diagnostics;
    using System.Management.Automation;    // Windows PowerShell namespace.
    using System.Security.Permissions;
    using Win32Exception = System.ComponentModel.Win32Exception;
    #region GetProcCommand

    /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc",
      DefaultParameterSetName = "ProcessName")]
   public class GetProcCommand : PSCmdlet
   {
       #region Fields
       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

       /// <summary>
       /// The identifiers of the processes to act on.
       /// </summary>
       private int[] processIds;

       /// <summary>
       /// The process objects to act on.
       /// </summary>
       private Process[] inputObjects;

       #endregion Fields

       #region Parameters

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ParameterSetName = "ProcessName",
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      /// <summary>
      /// Gets or sets the list of process identifiers on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         ParameterSetName = "Id",
         Mandatory = true,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true,
         HelpMessage = "The unique id of the process to get.")]
      public int[] Id
      {
         get { return this.processIds; }
         set { this.processIds = value; }
      }

      /// <summary>
      /// Gets or sets Process objects directly. If the input is a
      /// stream of [collection of] Process objects, the cmdlet bypasses the
      /// ProcessName and Id parameters and reads the Process objects
      /// directly.  This allows the cmdlet to deal with processes that have
      /// wildcard characters in their name.
      /// <value>Process objects</value>
      /// </summary>
      [Parameter(
         ParameterSetName = "InputObject",
         Mandatory = true,
         ValueFromPipeline = true)]
      public Process[] Input
      {
         get { return this.inputObjects; }
         set { this.inputObjects = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes. Then, the WriteObject
      /// method writes the associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         List<Process> matchingProcesses;

         WriteDebug("Obtaining the list of matching process objects.");

         switch (ParameterSetName)
         {
            case "Id":
               matchingProcesses = this.GetMatchingProcessesById();
               break;
            case "ProcessName":
               matchingProcesses = this.GetMatchingProcessesByName();
               break;
            case "InputObject":
               matchingProcesses = this.GetProcessesByInput();
               break;
            default:
               ThrowTerminatingError(
                   new ErrorRecord(
                       new ArgumentException("Bad ParameterSetName"),
                       "UnableToAccessProcessList",
                       ErrorCategory.InvalidOperation,
                       null));
               return;
         } // switch (ParameterSetName)

         WriteDebug("Outputting the matching process objects.");

         matchingProcesses.Sort(ProcessComparison);

         foreach (Process process in matchingProcesses)
         {
            WriteObject(process);
         }
      } // ProcessRecord

      #endregion Overrides

      #region protected Methods and Data

      /// <summary>
      /// Retrieves the list of all processes matching the ProcessName
      /// parameter and generates a nonterminating error for each
      /// specified process name which is not found even though the name
      /// contains no wildcards.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesByName()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> allProcesses =
            new List<Process>(Process.GetProcesses());

         // The keys dictionary is used for rapid lookup of
         // processes that are already in the matchingProcesses list.
         Dictionary<int, byte> keys = new Dictionary<int, byte>();

         List<Process> matchingProcesses = new List<Process>();

         if (null == this.processNames)
         {
             matchingProcesses.AddRange(allProcesses);
         }
         else
         {
             foreach (string pattern in this.processNames)
             {
                 WriteVerbose("Finding matches for process name \""
                    + pattern + "\".");

                 // WildCard serach on the available processes
                 WildcardPattern wildcard =
                    new WildcardPattern(
                        pattern,
                        WildcardOptions.IgnoreCase);

                 bool found = false;

                 foreach (Process process in allProcesses)
                 {
                     if (!keys.ContainsKey(process.Id))
                     {
                         string processName = SafeGetProcessName(process);

                         // Remove the process from the allProcesses list
                         // so that it is not tested again.
                         if (processName.Length == 0)
                         {
                             allProcesses.Remove(process);
                         }

                         // Perform a wildcard search on this particular
                         // process name and check whether it matches the
                         // pattern specified.
                         if (!wildcard.IsMatch(processName))
                         {
                             continue;
                         }

                         WriteDebug("Found matching process id "
                            + process.Id + ".");

                         // A match is found.
                         found = true;

                         // Store the process identifier so that the same process
                         // is not added twice.
                         keys.Add(process.Id, 0);

                         // Add the process to the processes list.
                         matchingProcesses.Add(process);
                     }
                 } // foreach (Process...

                 if (!found &&
                   !WildcardPattern.ContainsWildcardCharacters(pattern))
                 {
                     WriteError(new ErrorRecord(
                        new ArgumentException("Cannot find process name "
                           + "\"" + pattern + "\"."),
                        "ProcessNameNotFound",
                        ErrorCategory.ObjectNotFound,
                        pattern));
                 }
             } // foreach (string...
         } // if (null...

         return matchingProcesses;
      } // GetMatchingProcessesByName

      /// <summary>
      /// Returns the name of a process.  If an error occurs, a blank
      /// string is returned.
      /// </summary>
      /// <param name="process">The process whose name is
      /// returned.</param>
      /// <returns>The name of the process.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand, Unrestricted = true)]
      protected static string SafeGetProcessName(Process process)
      {
         new EnvironmentPermission(PermissionState.Unrestricted).Assert();
         string name = String.Empty;

         if (process != null)
         {
            try
            {
                return process.ProcessName;
            }
            catch (Win32Exception)
            {
            }
            catch (InvalidOperationException)
            {
            }
         }

         return name;
     } // SafeGetProcessName

      #endregion Cmdlet Overrides

      #region Private Methods

      /// <summary>
      /// Function to sort by process name first, and then by
      /// the process identifier.
      /// </summary>
      /// <param name="x">First process object.</param>
      /// <param name="y">Second process object.</param>
      /// <returns>
      /// Returns less than zero if x is less than y,
      /// greater than 0 if x is greater than y, and 0 if x == y.
      /// </returns>
      private static int ProcessComparison(Process x, Process y)
      {
         int diff = String.Compare(
            SafeGetProcessName(x),
            SafeGetProcessName(y),
            StringComparison.CurrentCultureIgnoreCase);

         if (0 != diff)
         {
             return diff;
         }
         else
         {
             return x.Id.CompareTo(y.Id);
         }
      }

      /// <summary>
      /// Retrieves the list of all processes matching the Id
      /// parameter and generates a nonterminating error for
      /// each specified process identofier which is not found.
      /// </summary>
      /// <returns>
      /// An array of processes that match the given identifier.
      /// </returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesById()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.processIds)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (int processId in this.processIds)
            {
               WriteVerbose("Finding match for process id "
                  + processId + ".");

               if (!keys.ContainsKey(processId))
               {
                  Process process;
                  try
                  {
                      process = Process.GetProcessById(processId);
                  }
                  catch (ArgumentException ex)
                  {
                     WriteError(new ErrorRecord(
                        ex,
                        "ProcessIdNotFound",
                        ErrorCategory.ObjectNotFound,
                        processId));
                     continue;
                  }

                  WriteDebug("Found matching process.");

                  matchingProcesses.Add(process);
                  keys.Add(processId, 0);
               }
            }
         }

         return matchingProcesses;
      } // GetMatchingProcessesById

      /// <summary>
      /// Retrieves the list of all processes matching the InputObject
      /// parameter.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetProcessesByInput()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.Input)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (Process process in this.Input)
            {
               WriteVerbose("Refreshing process object.");

               if (!keys.ContainsKey(process.Id))
               {
                  try
                  {
                      process.Refresh();
                  }
                  catch (Win32Exception)
                  {
                  }
                  catch (InvalidOperationException)
                  {
                  }

                  matchingProcesses.Add(process);
               }
            }
         }

         return matchingProcesses;
      } // GetProcessesByInput
      #endregion Private Methods
    } // End GetProcCommand class.

    #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="72e35-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="72e35-132">See Also</span></span>

[<span data-ttu-id="72e35-133">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="72e35-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
