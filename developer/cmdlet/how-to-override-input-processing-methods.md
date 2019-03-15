---
title: Het onderdrukken van invoer verwerkingsmethoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846751"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="4f58c-102">Invoerverwerkingsmethoden negeren</span><span class="sxs-lookup"><span data-stu-id="4f58c-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="4f58c-103">Deze voorbeelden laten zien hoe de invoer voor het verwerken van methoden die in een cmdlet overschrijven.</span><span class="sxs-lookup"><span data-stu-id="4f58c-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="4f58c-104">Deze methoden worden gebruikt om uit te voeren van de volgende bewerkingen:</span><span class="sxs-lookup"><span data-stu-id="4f58c-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="4f58c-105">De [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode wordt gebruikt voor het opstarten van eenmalige-bewerkingen die geldig voor alle objecten die zijn verwerkt door de cmdlet zijn uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4f58c-105">The [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="4f58c-106">Deze methode worden slechts één keer aanroept in de Windows PowerShell-runtime.</span><span class="sxs-lookup"><span data-stu-id="4f58c-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="4f58c-107">De [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode wordt gebruikt voor het verwerken van de objecten die zijn doorgegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f58c-107">The [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="4f58c-108">De Windows PowerShell-runtime wordt deze methode voor elk object doorgegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f58c-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="4f58c-109">De [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode wordt gebruikt voor het uitvoeren van bewerkingen voor de verwerking eenmalige post.</span><span class="sxs-lookup"><span data-stu-id="4f58c-109">The [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="4f58c-110">Deze methode worden slechts één keer aanroept in de Windows PowerShell-runtime.</span><span class="sxs-lookup"><span data-stu-id="4f58c-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="4f58c-111">Voor de onderdrukking van de methode BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="4f58c-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="4f58c-112">Declareer een beveiligde onderdrukking van de [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode.</span><span class="sxs-lookup"><span data-stu-id="4f58c-112">Declare a protected override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="4f58c-113">De volgende klasse worden afgedrukt een voorbeeldbericht weergegeven.</span><span class="sxs-lookup"><span data-stu-id="4f58c-113">The following class prints a sample message.</span></span> <span data-ttu-id="4f58c-114">Voor het gebruik van deze klasse het werkwoord en een zelfstandig naamwoord in de Cmdlet-kenmerk wijzigen, wijzigt u de naam van de klasse in overeenstemming met de nieuwe werkwoord en een zelfstandig naamwoord en vervolgens de gewenste functionaliteit toevoegen aan de onderdrukking van de [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode.</span><span class="sxs-lookup"><span data-stu-id="4f58c-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="4f58c-115">Voor de onderdrukking van de methode ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="4f58c-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="4f58c-116">Declareer een beveiligde onderdrukking van de [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.</span><span class="sxs-lookup"><span data-stu-id="4f58c-116">Declare a protected override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="4f58c-117">De volgende klasse worden afgedrukt een voorbeeldbericht weergegeven.</span><span class="sxs-lookup"><span data-stu-id="4f58c-117">The following class prints a sample message.</span></span> <span data-ttu-id="4f58c-118">Voor het gebruik van deze klasse het werkwoord en een zelfstandig naamwoord in de Cmdlet-kenmerk wijzigen, wijzigt u de naam van de klasse in overeenstemming met de nieuwe werkwoord en een zelfstandig naamwoord en vervolgens de gewenste functionaliteit toevoegen aan de onderdrukking van de [System.Management.Automation.Cmdlet.Processrecord\* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.</span><span class="sxs-lookup"><span data-stu-id="4f58c-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="4f58c-119">Voor de onderdrukking van de methode EndProcessing</span><span class="sxs-lookup"><span data-stu-id="4f58c-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="4f58c-120">Declareer een beveiligde onderdrukking van de [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode.</span><span class="sxs-lookup"><span data-stu-id="4f58c-120">Declare a protected override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="4f58c-121">De volgende klasse worden afgedrukt een voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="4f58c-121">The following class prints a sample.</span></span> <span data-ttu-id="4f58c-122">Voor het gebruik van deze klasse het werkwoord en een zelfstandig naamwoord in de Cmdlet-kenmerk wijzigen, wijzigt u de naam van de klasse in overeenstemming met de nieuwe werkwoord en een zelfstandig naamwoord en vervolgens de gewenste functionaliteit toevoegen aan de onderdrukking van de [System.Management.Automation.Cmdlet.Endprocessing\* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode.</span><span class="sxs-lookup"><span data-stu-id="4f58c-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="4f58c-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4f58c-123">See Also</span></span>

[<span data-ttu-id="4f58c-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="4f58c-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="4f58c-125">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="4f58c-125">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="4f58c-126">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="4f58c-126">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="4f58c-127">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f58c-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)