---
title: Taken plannen met de Windows PowerShell-API
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 280067072c5c8e289a38745364294af842a455c6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845428"
---
# <a name="scheduling-jobs-with-the-windows-powershell-api"></a><span data-ttu-id="aa23a-102">Taken plannen met de Windows PowerShell-API</span><span class="sxs-lookup"><span data-stu-id="aa23a-102">Scheduling Jobs with the Windows PowerShell API</span></span>

<span data-ttu-id="aa23a-103">U kunt de objecten die worden weergegeven door de N:Microsoft.PowerShell.ScheduledJob-naamruimte te maken van een geplande taak, definiëren wanneer deze wordt uitgevoerd en resultaten over de voltooide taak ontvangen nadat deze is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aa23a-103">You can use the objects exposed by the N:Microsoft.PowerShell.ScheduledJob namespace to create a scheduled job, define when it runs, and get results about the completed job after it has run.</span></span>

## <a name="triggering-the-job"></a><span data-ttu-id="aa23a-104">De taak wordt geactiveerd</span><span class="sxs-lookup"><span data-stu-id="aa23a-104">Triggering the Job</span></span>

<span data-ttu-id="aa23a-105">De eerste stap bij het maken van een geplande taak is op te geven wanneer de taak moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aa23a-105">The first step in creating a scheduled job is specifying when the job should run.</span></span> <span data-ttu-id="aa23a-106">Dit doen door het maken en configureren van een T:Microsoft.PowerShell.ScheduledJob.ScheduledJobTriggerobject.</span><span class="sxs-lookup"><span data-stu-id="aa23a-106">Do this by creating and configuring a T:Microsoft.PowerShell.ScheduledJob.ScheduledJobTriggerobject.</span></span> <span data-ttu-id="aa23a-107">De volgende code maakt een trigger die een taak één keer in de toekomst 20 seconden wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aa23a-107">The following code creates a trigger that schedules a job to run a single time 20 seconds in the future.</span></span>

```csharp
ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
    DateTime.Now.AddSeconds(20),        // Create trigger to start job 20 seconds after now.
    TimeSpan.Zero,                      // No random delay
    null,                               // No repetition interval time
    null,                               // No repetition interval duration
    1,                                  // Trigger Id
    true);                              // Create trigger enabled
```

## <a name="defining-the-job"></a><span data-ttu-id="aa23a-108">De taak definiëren</span><span class="sxs-lookup"><span data-stu-id="aa23a-108">Defining the Job</span></span>

<span data-ttu-id="aa23a-109">Een Windows PowerShell-taak definieert u het maken van een woordenlijst parameter.</span><span class="sxs-lookup"><span data-stu-id="aa23a-109">You define a Windows PowerShell job by creating a parameter dictionary.</span></span> <span data-ttu-id="aa23a-110">De volgende parameters worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="aa23a-110">The following parameters are supported.</span></span>

|<span data-ttu-id="aa23a-111">Parameternaam</span><span class="sxs-lookup"><span data-stu-id="aa23a-111">Parameter Name</span></span>|<span data-ttu-id="aa23a-112">Description</span><span class="sxs-lookup"><span data-stu-id="aa23a-112">Description</span></span>|
|---|---|
|<span data-ttu-id="aa23a-113">Naam</span><span class="sxs-lookup"><span data-stu-id="aa23a-113">Name</span></span>|<span data-ttu-id="aa23a-114">De naam van de taak.</span><span class="sxs-lookup"><span data-stu-id="aa23a-114">The name of the job.</span></span>|
|<span data-ttu-id="aa23a-115">ScriptBock</span><span class="sxs-lookup"><span data-stu-id="aa23a-115">ScriptBock</span></span>|<span data-ttu-id="aa23a-116">Een blok van de Windows PowerShell-script waarmee wordt aangegeven wat de taak doet.</span><span class="sxs-lookup"><span data-stu-id="aa23a-116">A Windows PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="aa23a-117">FilePath</span><span class="sxs-lookup"><span data-stu-id="aa23a-117">FilePath</span></span>|<span data-ttu-id="aa23a-118">Een pad naar een bestand met Windows PowerShell-scriptblok waarmee wordt aangegeven wat de taak doet.</span><span class="sxs-lookup"><span data-stu-id="aa23a-118">A path to a file that contains Windows PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="aa23a-119">InitializationScript</span><span class="sxs-lookup"><span data-stu-id="aa23a-119">InitializationScript</span></span>|<span data-ttu-id="aa23a-120">Een blok van de Windows PowerShell-script waarmee de taak wordt geïnitialiseerd.</span><span class="sxs-lookup"><span data-stu-id="aa23a-120">A Windows PowerShell script block that initializes the job.</span></span>|
|<span data-ttu-id="aa23a-121">ArgumentList</span><span class="sxs-lookup"><span data-stu-id="aa23a-121">ArgumentList</span></span>|<span data-ttu-id="aa23a-122">Een matrix met objecten die argumenten opgeeft die het duurt de taak uit.</span><span class="sxs-lookup"><span data-stu-id="aa23a-122">An array of objects that specify arguments that the job takes.</span></span>|
|<span data-ttu-id="aa23a-123">RunAs32</span><span class="sxs-lookup"><span data-stu-id="aa23a-123">RunAs32</span></span>|<span data-ttu-id="aa23a-124">Een Booleaanse waarde waarmee wordt aangegeven of de taak uitvoeren in een 32-bits proces.</span><span class="sxs-lookup"><span data-stu-id="aa23a-124">A boolean value that specifies whether to run the job in a 32-bit process.</span></span>|

<span data-ttu-id="aa23a-125">De volgende code maakt een parameter dictionary-object en stelt u de naam en ScriptBlock parameters.</span><span class="sxs-lookup"><span data-stu-id="aa23a-125">The following code creates a parameter dictionary object and sets the Name and ScriptBlock parameters.</span></span>

```csharp
string schedJobDefName = "MySampleSchedJob";
Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
jobDefParameters.Add("Name", schedJobDefName);      // Unique name is requiried.

ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                   // is required.
```

## <a name="creating-the-invocation-and-job-definition-objects"></a><span data-ttu-id="aa23a-126">Het maken van de aanroep en de taak de definitie van objecten</span><span class="sxs-lookup"><span data-stu-id="aa23a-126">Creating the Invocation and Job Definition Objects</span></span>

<span data-ttu-id="aa23a-127">Vervolgens maakt u ScheduledJobInvicationInfo en SheduledJobDefinition objecten voor het uitvoeren van de taak.</span><span class="sxs-lookup"><span data-stu-id="aa23a-127">You then create ScheduledJobInvicationInfo and SheduledJobDefinition objects to run the job.</span></span> <span data-ttu-id="aa23a-128">De volgende code laat dit zien.</span><span class="sxs-lookup"><span data-stu-id="aa23a-128">The following code demonstrates this.</span></span>

```csharp
ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
    nw JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
    jobDefParameters);

schedJobDefinition = new ScheduledJobDefinition(
    jobInvocationInfo,                          // Defines the PowerShell job to run.
    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
    null,                                       // No custom options.  We accept default.
    null);                                      // No credentials.  PowerShell job is run
                                                // in default Task Scheduler process, account.
```

## <a name="registering-the-job-with-the-task-scheduler"></a><span data-ttu-id="aa23a-129">Registreren van de taak met de Taakplanner</span><span class="sxs-lookup"><span data-stu-id="aa23a-129">Registering the Job with the Task Scheduler</span></span>

<span data-ttu-id="aa23a-130">De volgende code wordt de taak met de Windows Taakplanner geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="aa23a-130">The following code registers the job with the Windows Task Scheduler.</span></span>

```csharp
schedJobDefinition.Register();
registrationSucceeded = true;
Console.WriteLine("Scheduled job has been registered.  Waiting 30 seconds for it to be started and run.");
```

## <a name="complete-code-example"></a><span data-ttu-id="aa23a-131">Voorbeeld van de volledige Code</span><span class="sxs-lookup"><span data-stu-id="aa23a-131">Complete Code Example</span></span>

<span data-ttu-id="aa23a-132">Hier volgt het volledige codevoorbeeld van waaruit de vorige codefragmenten zijn uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aa23a-132">The following is the complete code example from which the previous snippets were taken.</span></span>

```csharp
using System;
using System.Threading;
using System.Collections.Generic;
using System.Management.Automation;             // Windows PowerShell namespace.
using Microsoft.PowerShell.ScheduledJob;        // Windows PowerShell ScheduledJob namespace.

namespace Microsoft.Samples.PowerShell.ScheduledJob
{
    /// <summary>
    /// This class contains the Main enrty point for the application.
    /// </summary>
    public class ScheduledJobSample
    {
        /// <summary>
        /// This sample shows how to use the PowerShell ScheduledJob API to create
        /// a simple PowerShell scheduled job, register it with a trigger object
        /// that defines when the job will run and retrieve job run results from
        /// the job file store.
        /// </summary>
        /// <param name="args"></param>
        public static void Main(string[] args)
        {
            // ScheduledJobDefinition contains all elements of a PowerShell scheduled
            // job including the PowerShell job script or script file path, scheduling
            // triggers, and scheduling options.
            ScheduledJobDefinition schedJobDefinition = null;
            bool registrationSucceeded = false;

            try
            {
                // First create a scheduled job trigger object.  This object will
                // define when the PowerShell job is scheduled to run.  For this
                // example we will create a trigger to run the job just one time
                // 20 seconds after the trigger object is created.
                // Note: If you are stepping through this code in a debugger you
                // may want to increase the 20 seconds value so that the trigger time
                // remains in the future once you register the scheduled job.
                ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20),        // Create trigger to start job 20 seconds after now.
                    TimeSpan.Zero,                      // No random delay
                    null,                               // No repetition interval time
                    null,                               // No repetition interval duration
                    1,                                  // Trigger Id
                    true);                              // Create trigger enabled

                // Create a parameter dictionary that defines the PowerShell job.
                // For this example we will create a simple script that runs for
                // 5 seconds generating output.
                // Here are the parameters supported to define the PowerShell job.
                // Name                 - Job name string.
                // ScriptBlock          - PowerShell ScriptBlock type.
                // FilePath             - PowerShell script file path string.
                // InitializationScript - PowerShell Scriptblock type.
                // ArgumentList         - object[] type.
                // RunAs32              - Switch (boolean type).
                string schedJobDefName = "MySampleSchedJob";
                Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
                jobDefParameters.Add("Name", schedJobDefName);      // Unique name is requiried.

                ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
                jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                                   // is required.

                // Now create a JobInvocation object that contains all information about
                // the PowerShell job to run.
                ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
                    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
                    jobDefParameters);

                // Finally create the scheduled job definition object that pulls all
                // of this information together.
                schedJobDefinition = new ScheduledJobDefinition(
                    jobInvocationInfo,                          // Defines the PowerShell job to run.
                    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
                    null,                                       // No custom options.  We accept default.
                    null);                                      // No credentials.  PowerShell job is run
                                                                // in default Task Scheduler process, account.

                // Next we register this scheduled job object with Windows Task Scheduler.
                // The Task Scheduler will run the PowerShell script based on the provided job trigger.
                schedJobDefinition.Register();
                registrationSucceeded = true;
                Console.WriteLine("Scheduled job has been registered.  Waiting 30 seconds for it to be started and run.");

                // You can see this PowerShell job task registered in the Task Scheduler UI.
                // Look under path: Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs

                // Wait for Task Scheduler to run the PowerShell job.  This should happen in 20 seconds
                // and then the job will take about 5 seconds to run.  If PowerShell job task doesn't
                // run try increasing the trigger time in the ScheduledJobTrigger object.  You can also
                // run this task manully from the Task Scheduler UI.
                for (int count = 1; count < 31; ++count)
                {
                    Thread.Sleep(1000);
                    Console.WriteLine(count + " seconds elapsed");
                }

                Console.WriteLine();
                Console.WriteLine("Job run results.");
                Console.WriteLine();

                // Since the PowerShell job runs in a non-interactive Task Scheduler
                // process the job status and output data is written to a file based
                // job store and the directory location is the current user local app
                // data ($env:LOCALAPPDATA).
                // This job store can be accessed through the ScheduledJobSourceAdapter class.
                ScheduledJobSourceAdapter schedJobSourceAdpater = new ScheduledJobSourceAdapter();
                IList<Job2> jobRuns = schedJobSourceAdpater.GetJobs();
                foreach (var jobRun in jobRuns)
                {
                    // Check for jobs in finished state.
                    // Note that job data is not written to the job store until the job
                    // has reached a finished state.
                    JobState jobState = jobRun.JobStateInfo.State;
                    if (jobState == JobState.Completed ||
                        jobState == JobState.Stopped ||
                        jobState == JobState.Failed)
                    {
                        // Write job run finished state.
                        Console.WriteLine("Job Status: " + jobRun.JobStateInfo.State);
                        Console.WriteLine();
                        Console.WriteLine("Job Data");

                        // Write output data.
                        foreach (var item in jobRun.Output)
                        {
                            Console.WriteLine(item.ToString());
                        }

                        // Write any errors.
                        foreach (var item in jobRun.Error)
                        {
                            Console.WriteLine(item.ToString());
                        }
                    }
                }

                Console.WriteLine();
                Console.WriteLine("Press any key to continue...");
                Console.ReadKey();
            }
            catch (ScheduledJobException e)
            {
                Console.WriteLine("Error: " + e.Message);
            }
            finally
            {
                // Unregister this scheduled job or an error will be thrown when
                // running this sample code again (scheduled job already exists.)
                // because all registered scheduled jobs must have a unique name.
                if (registrationSucceeded)
                {
                    schedJobDefinition.Remove(true);
                }
            }
        }
    }
}
```
