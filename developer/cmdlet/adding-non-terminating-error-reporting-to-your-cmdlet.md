---
title: Toevoegen van niet-afsluitfouten die fouten rapporteren aan uw Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 2f3bb481722363557c93ebbc5e6df62baeff2555
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851014"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="df753-102">Rapportage aan uw cmdlet toevoegen voor fouten die niet leiden tot de beëindiging van een functie of bewerking</span><span class="sxs-lookup"><span data-stu-id="df753-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="df753-103">Cmdlets afsluitfouten kunt melden door het aanroepen van de [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode en nog steeds kan functioneren op het huidige invoerobject of verdere inkomende pipeline-objecten.</span><span class="sxs-lookup"><span data-stu-id="df753-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="df753-104">In deze sectie wordt uitgelegd hoe u een cmdlet die afsluitfouten uit de invoer verwerkingsmethoden rapporten maken.</span><span class="sxs-lookup"><span data-stu-id="df753-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="df753-105">Voor afsluitfouten (evenals afsluitende fouten), de cmdlet moet slagen voor een [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object identificeren van de fout.</span><span class="sxs-lookup"><span data-stu-id="df753-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object identifying the error.</span></span> <span data-ttu-id="df753-106">Elke foutrecord wordt geïdentificeerd door een unieke tekenreeks met de naam van de 'fout-id."</span><span class="sxs-lookup"><span data-stu-id="df753-106">Each error record is identified by a unique string called the "error identifier."</span></span> <span data-ttu-id="df753-107">Naast de-id, de categorie van elke fout die is opgegeven door de constanten zijn gedefinieerd door een [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) opsomming.</span><span class="sxs-lookup"><span data-stu-id="df753-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="df753-108">De gebruiker kan zien fouten op basis van hun categorie door in te stellen de `$ErrorView` variabele 'CategoryView'.</span><span class="sxs-lookup"><span data-stu-id="df753-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="df753-109">Zie voor meer informatie over foutrecords [Windows PowerShell-foutrecords](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="df753-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="df753-110">Onderwerpen in deze sectie bevatten het volgende:</span><span class="sxs-lookup"><span data-stu-id="df753-110">Topics in this section include the following:</span></span>

- [<span data-ttu-id="df753-111">De Cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="df753-111">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="df753-112">Parameters definiëren</span><span class="sxs-lookup"><span data-stu-id="df753-112">Defining Parameters</span></span>](#Defining-Parameters)

- [<span data-ttu-id="df753-113">Invoer verwerking van methoden overschrijven</span><span class="sxs-lookup"><span data-stu-id="df753-113">Overriding Input Processing Methods</span></span>](#Overriding-Input-Processing-Methods)

- [<span data-ttu-id="df753-114">Rapportage afsluitfouten</span><span class="sxs-lookup"><span data-stu-id="df753-114">Reporting Nonterminating Errors</span></span>](#Reporting-Nonterminating-Errors)

- [<span data-ttu-id="df753-115">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="df753-115">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="df753-116">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="df753-116">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="df753-117">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df753-117">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="df753-118">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df753-118">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="df753-119">De Cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="df753-119">Defining the Cmdlet</span></span>

<span data-ttu-id="df753-120">De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="df753-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="df753-121">Dit smdlet haalt procesinformatie, dus de hier gekozen naam van de term 'Ophalen'.</span><span class="sxs-lookup"><span data-stu-id="df753-121">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="df753-122">(Bijna elk soort cmdlet waarmee het ophalen van gegevens kan opdrachtregel invoer verwerken). Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="df753-122">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="df753-123">Hier volgt de definitie voor deze cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="df753-123">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="df753-124">Details van deze definitie zijn vermeld in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="df753-124">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="df753-125">Parameters definiëren</span><span class="sxs-lookup"><span data-stu-id="df753-125">Defining Parameters</span></span>

<span data-ttu-id="df753-126">Indien nodig, moet de cmdlet-parameters voor het verwerken van invoer definiëren.</span><span class="sxs-lookup"><span data-stu-id="df753-126">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="df753-127">Deze cmdlet Get-Proc definieert een `Name` parameter zoals beschreven in [Parameters die invoer van de opdrachtregel proces toe te voegen](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="df753-127">This Get-Proc cmdlet defines a `Name` parameter as described in [Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="df753-128">Hier is de parameterdeclaratie voor de `Name` parameter van deze cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="df753-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="df753-129">Invoer verwerking van methoden overschrijven</span><span class="sxs-lookup"><span data-stu-id="df753-129">Overriding Input Processing Methods</span></span>

<span data-ttu-id="df753-130">Alle cmdlets moet ten minste één van de invoer voor het verwerken van methoden die door overschrijven de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse.</span><span class="sxs-lookup"><span data-stu-id="df753-130">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="df753-131">Deze methoden worden besproken in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="df753-131">These methods are discussed in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="df753-132">De cmdlet moet onafhankelijk mogelijk elke record verwerken.</span><span class="sxs-lookup"><span data-stu-id="df753-132">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="df753-133">Deze cmdlet Get-Proc overschrijft de [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het afhandelen van de `Name` parameter voor invoer geleverd door de gebruiker of een script.</span><span class="sxs-lookup"><span data-stu-id="df753-133">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter for input provided by the user or a script.</span></span> <span data-ttu-id="df753-134">Deze methode krijgt de processen voor elke gewenste procesnaam of alle processen als er geen naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="df753-134">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="df753-135">Details van deze overschrijving worden vermeld in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="df753-135">Details of this override are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

#### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="df753-136">Om te onthouden wanneer die fouten rapporteren</span><span class="sxs-lookup"><span data-stu-id="df753-136">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="df753-137">De [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) -object dat de cmdlet wordt doorgegeven tijdens het schrijven van een fout is een uitzondering in de kern vereist.</span><span class="sxs-lookup"><span data-stu-id="df753-137">The [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="df753-138">Volg de richtlijnen voor .NET bij het bepalen van de uitzondering te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="df753-138">Follow the .NET guidelines when determining the exception to use.</span></span> <span data-ttu-id="df753-139">In feite, als de fout semantisch gelijk zijn aan een bestaande uitzondering is, de cmdlet moet gebruiken of afgeleid van de uitzondering.</span><span class="sxs-lookup"><span data-stu-id="df753-139">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="df753-140">Anders moet afleiden een nieuwe uitzondering of uitzonderingen hiërarchie rechtstreeks vanuit de [System.Exception](/dotnet/api/System.Exception) klasse.</span><span class="sxs-lookup"><span data-stu-id="df753-140">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception](/dotnet/api/System.Exception) class.</span></span>

<span data-ttu-id="df753-141">Houd er rekening mee met het volgende bij het maken van fout-id's (toegankelijk via de eigenschap FullyQualifiedErrorId van de klasse ErrorRecord).</span><span class="sxs-lookup"><span data-stu-id="df753-141">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="df753-142">Gebruik tekenreeksen die zijn bedoeld voor diagnostische doeleinden zodat bij de inspectie van de volledig gekwalificeerde id kunt u bepalen wat de fout is en waar de fout die afkomstig zijn uit.</span><span class="sxs-lookup"><span data-stu-id="df753-142">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="df753-143">Als volgt kan een juist opgemaakte volledig gekwalificeerde fout-id zijn.</span><span class="sxs-lookup"><span data-stu-id="df753-143">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

<span data-ttu-id="df753-144">U ziet dat in het vorige voorbeeld wordt de fout-id (de eerste token) Hiermee wordt aangegeven wat de fout is en het resterende deel geeft aan waar de fout afkomstig zijn uit.</span><span class="sxs-lookup"><span data-stu-id="df753-144">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="df753-145">Voor complexere scenario's, kan de fout-id een punt van elkaar gescheiden-token dat kan worden geparseerd voor controle zijn.</span><span class="sxs-lookup"><span data-stu-id="df753-145">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="df753-146">Hiermee kunt dat u ook op de onderdelen van de fout-id, evenals de fout-id en de fout categorie vertakking.</span><span class="sxs-lookup"><span data-stu-id="df753-146">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="df753-147">De cmdlet moet specifieke fout-id's toewijzen aan andere codepaden.</span><span class="sxs-lookup"><span data-stu-id="df753-147">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="df753-148">Houd er rekening mee voor de toewijzing van fout-id's de volgende informatie:</span><span class="sxs-lookup"><span data-stu-id="df753-148">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="df753-149">Een fout-id moet ongewijzigd blijft gedurende de levenscyclus van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df753-149">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="df753-150">De semantiek van een fout-id tussen versies van de cmdlet niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="df753-150">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="df753-151">Gebruik de tekst voor een fout-id die tersely overeenkomt met de fout wordt gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="df753-151">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="df753-152">Gebruik geen spaties of leestekens.</span><span class="sxs-lookup"><span data-stu-id="df753-152">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="df753-153">De cmdlet genereert alleen fout-id's die kunnen worden gereproduceerd hebben.</span><span class="sxs-lookup"><span data-stu-id="df753-153">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="df753-154">Er moet een id die een proces-id bevat bijvoorbeeld niet gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="df753-154">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="df753-155">Fout-id's zijn handig om een gebruiker alleen als ze overeenkomen met de id's die zijn zichtbaar voor andere gebruikers hetzelfde probleem ondervindt.</span><span class="sxs-lookup"><span data-stu-id="df753-155">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="df753-156">Niet-verwerkte uitzonderingen zijn niet opgepikt door Windows PowerShell in de volgende voorwaarden:</span><span class="sxs-lookup"><span data-stu-id="df753-156">Unhandled exceptions are not caught by Windows PowerShell in the following conditions:</span></span>

- <span data-ttu-id="df753-157">Als een cmdlet maakt een nieuwe thread en code die wordt uitgevoerd in deze thread een niet-verwerkte uitzondering genereert, wordt Windows PowerShell wordt de fout niet onderscheppen en wordt het proces is beëindigd.</span><span class="sxs-lookup"><span data-stu-id="df753-157">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="df753-158">Als een object heeft de code in de destructor of Dispose methoden die ervoor zorgt een niet-verwerkte uitzondering dat, wordt Windows PowerShell wordt de fout niet onderscheppen en wordt het proces is beëindigd.</span><span class="sxs-lookup"><span data-stu-id="df753-158">If an object has code in its destructor or Dispose methods that causes an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="df753-159">Rapportage afsluitfouten</span><span class="sxs-lookup"><span data-stu-id="df753-159">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="df753-160">Een van de invoer verwerkingsmethoden kan een nonterminating fout rapporteren aan de uitvoer stream met de [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode.</span><span class="sxs-lookup"><span data-stu-id="df753-160">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="df753-161">Hier volgt een voorbeeld van deze cmdlet Get-procedure die laat zien van de aanroep van [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) uit binnen de onderdrukking van de [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.</span><span class="sxs-lookup"><span data-stu-id="df753-161">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from within the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="df753-162">In dit geval wordt de aanroep uitgevoerd als de cmdlet kan een proces voor een opgegeven proces-id niet vinden.</span><span class="sxs-lookup"><span data-stu-id="df753-162">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="df753-163">Om te onthouden over het schrijven van afsluitfouten</span><span class="sxs-lookup"><span data-stu-id="df753-163">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="df753-164">Voor een nonterminating fout, moet de cmdlet een specifieke fout-id voor elke specifieke invoerobject genereren.</span><span class="sxs-lookup"><span data-stu-id="df753-164">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="df753-165">Een cmdlet moet vaak wijzigen van de Windows PowerShell-actie die wordt geproduceerd door een nonterminating fout.</span><span class="sxs-lookup"><span data-stu-id="df753-165">A cmdlet frequently needs to modify the Windows PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="df753-166">Dit kan worden gedaan door te definiëren de `ErrorAction` en `ErrorVariable` parameters.</span><span class="sxs-lookup"><span data-stu-id="df753-166">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="df753-167">Als u definieert de `ErrorAction` parameter, de cmdlet geeft de gebruikersopties [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), u kunt ook rechtstreeks van invloed zijn op de actie door in te stellen de `$ErrorActionPreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="df753-167">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="df753-168">De cmdlet afsluitfouten kunt opslaan naar een variabele met de `ErrorVariable` parameter, die wordt niet beïnvloed door de instelling van `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="df753-168">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="df753-169">Fouten kunnen worden toegevoegd aan een bestaande variabele van de fout door een plusteken (+) toe te voegen aan het begin van de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="df753-169">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="df753-170">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="df753-170">Code Sample</span></span>

<span data-ttu-id="df753-171">Voor de volledige C# voorbeeldcode, Zie [GetProcessSample04 voorbeeld](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="df753-171">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="df753-172">Definieer objecttypen en opmaak</span><span class="sxs-lookup"><span data-stu-id="df753-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="df753-173">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="df753-173">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="df753-174">Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of de cmdlet moet mogelijk om uit te breiden van een bestaand type geleverd door een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df753-174">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="df753-175">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="df753-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="df753-176">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df753-176">Building the Cmdlet</span></span>

<span data-ttu-id="df753-177">Na de implementatie van een cmdlet, moet u deze registreren met Windows PowerShell via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="df753-177">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="df753-178">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="df753-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="df753-179">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df753-179">Testing the Cmdlet</span></span>

<span data-ttu-id="df753-180">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="df753-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="df753-181">We gaan de voorbeeld-cmdlet Get-Proc om te zien of er een fout gemeld testen:</span><span class="sxs-lookup"><span data-stu-id="df753-181">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="df753-182">Start Windows PowerShell en gebruik de cmdlet Get-procedure voor het ophalen van de processen met de naam 'TEST'.</span><span class="sxs-lookup"><span data-stu-id="df753-182">Start Windows PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="df753-183">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="df753-183">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="df753-184">Zie ook</span><span class="sxs-lookup"><span data-stu-id="df753-184">See Also</span></span>

[<span data-ttu-id="df753-185">Parameters die proces Pipeline ingevoerd toe te voegen</span><span class="sxs-lookup"><span data-stu-id="df753-185">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="df753-186">Parameters die opdrachtregel verwerken toe te voegen</span><span class="sxs-lookup"><span data-stu-id="df753-186">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="df753-187">Het maken van uw eerste Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df753-187">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="df753-188">Objecttypen uitbreiden en opmaak</span><span class="sxs-lookup"><span data-stu-id="df753-188">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="df753-189">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="df753-189">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="df753-190">Windows PowerShell-referentie</span><span class="sxs-lookup"><span data-stu-id="df753-190">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="df753-191">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="df753-191">Cmdlet Samples</span></span>](./cmdlet-samples.md)