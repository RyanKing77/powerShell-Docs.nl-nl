---
title: Het maken van een werkstroom met Windows PowerShell-activiteiten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845036"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="b920e-102">Een werkstroom maken met Windows PowerShell-activiteiten</span><span class="sxs-lookup"><span data-stu-id="b920e-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="b920e-103">U kunt een Windows PowerShell-werkstroom maken door te selecteren van activiteiten in de Visual Studio-werkset en ze naar de Workflow Designer-venster te slepen.</span><span class="sxs-lookup"><span data-stu-id="b920e-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="b920e-104">Zie voor meer informatie over het toevoegen van Windows PowerShell-activiteiten naar de Visual Studio-werkset [Windows PowerShell-activiteiten toe te voegen aan de Visual Studio-werkset](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="b920e-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="b920e-105">De volgende procedures wordt beschreven hoe u een werkstroom maken die controleert de domeinstatus van een groep computers door gebruiker opgegeven, maakt u ze lid aan een domein als ze niet al zijn gekoppeld, en de status vervolgens opnieuw controleert.</span><span class="sxs-lookup"><span data-stu-id="b920e-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="b920e-106">Instellen van het Project</span><span class="sxs-lookup"><span data-stu-id="b920e-106">Setting up the Project</span></span>

1. <span data-ttu-id="b920e-107">Volg de procedure in [Windows PowerShell-activiteiten toe te voegen aan de Visual Studio-werkset](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) een werkstroom-project maken en toevoegen van de activiteiten van de [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) en [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assembly's aan de werkset.</span><span class="sxs-lookup"><span data-stu-id="b920e-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="b920e-108">System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities en Microsoft.PowerShell.Commands.Management garantie voor het project als verwijzing assembly's toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b920e-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="b920e-109">Activiteiten toe te voegen aan de werkstroom</span><span class="sxs-lookup"><span data-stu-id="b920e-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="b920e-110">Voeg een **reeks** activiteit naar de werkstroom.</span><span class="sxs-lookup"><span data-stu-id="b920e-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="b920e-111">Maken van een argument met de naam `ComputerName` met een argumenttype van `String[]`.</span><span class="sxs-lookup"><span data-stu-id="b920e-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="b920e-112">Dit argument geeft de namen van de computers om te controleren en te koppelen.</span><span class="sxs-lookup"><span data-stu-id="b920e-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="b920e-113">Maken van een argument met de naam `DomainCred` van het type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="b920e-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="b920e-114">Dit argument vertegenwoordigt de domeinreferenties van een domeinaccount dat gemachtigd is op een computer toevoegen aan het domein.</span><span class="sxs-lookup"><span data-stu-id="b920e-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="b920e-115">Maken van een argument met de naam `MachineCred` van het type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="b920e-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="b920e-116">Dit argument geeft de referenties van een beheerder op de computers om te controleren en te koppelen.</span><span class="sxs-lookup"><span data-stu-id="b920e-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="b920e-117">Voeg een **ParallelForEach** activiteit binnen de **reeks** activiteit.</span><span class="sxs-lookup"><span data-stu-id="b920e-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="b920e-118">Voer `comp` en `ComputerName` in de tekstvakken zodat de lus de elementen van doorloopt de `ComputerName` matrix.</span><span class="sxs-lookup"><span data-stu-id="b920e-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="b920e-119">Voeg een **reeks** activiteit aan de hoofdtekst van de **ParallelForEach** activiteit.</span><span class="sxs-lookup"><span data-stu-id="b920e-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="b920e-120">Stel de **DisplayName** eigenschap van de reeks aan `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="b920e-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="b920e-121">Voeg een **GetWmiObject** activiteit in op de **JoinDomain** volgorde.</span><span class="sxs-lookup"><span data-stu-id="b920e-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="b920e-122">Bewerk de eigenschappen van de **GetWmiObject** activiteit als volgt te werk.</span><span class="sxs-lookup"><span data-stu-id="b920e-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="b920e-123">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b920e-123">Property</span></span>|<span data-ttu-id="b920e-124">Waarde</span><span class="sxs-lookup"><span data-stu-id="b920e-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="b920e-125">**Klasse**</span><span class="sxs-lookup"><span data-stu-id="b920e-125">**Class**</span></span>|<span data-ttu-id="b920e-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="b920e-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="b920e-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="b920e-127">**PSComputerName**</span></span>|<span data-ttu-id="b920e-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="b920e-128">{comp}</span></span>|
   |<span data-ttu-id="b920e-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="b920e-129">**PSCredential**</span></span>|<span data-ttu-id="b920e-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="b920e-130">MachineCred</span></span>|

9. <span data-ttu-id="b920e-131">Toevoegen een **AddComputer** activiteit naar de **JoinDomain** volgorde na de **GetWmiObject** activiteit.</span><span class="sxs-lookup"><span data-stu-id="b920e-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="b920e-132">Bewerk de eigenschappen van de **AddComputer** activiteit als volgt te werk.</span><span class="sxs-lookup"><span data-stu-id="b920e-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="b920e-133">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b920e-133">Property</span></span>|<span data-ttu-id="b920e-134">Waarde</span><span class="sxs-lookup"><span data-stu-id="b920e-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="b920e-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="b920e-135">**ComputerName**</span></span>|<span data-ttu-id="b920e-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="b920e-136">{comp}</span></span>|
    |<span data-ttu-id="b920e-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="b920e-137">**DomainCredential**</span></span>|<span data-ttu-id="b920e-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="b920e-138">DomainCred</span></span>|

11. <span data-ttu-id="b920e-139">Toevoegen een **RestartComputer** activiteit naar de **JoinDomain** volgorde na de **AddComputer** activiteit.</span><span class="sxs-lookup"><span data-stu-id="b920e-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="b920e-140">Bewerk de eigenschappen van de **RestartComputer** activiteit als volgt te werk.</span><span class="sxs-lookup"><span data-stu-id="b920e-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="b920e-141">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b920e-141">Property</span></span>|<span data-ttu-id="b920e-142">Waarde</span><span class="sxs-lookup"><span data-stu-id="b920e-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="b920e-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="b920e-143">**ComputerName**</span></span>|<span data-ttu-id="b920e-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="b920e-144">{comp}</span></span>|
    |<span data-ttu-id="b920e-145">**Referentie**</span><span class="sxs-lookup"><span data-stu-id="b920e-145">**Credential**</span></span>|<span data-ttu-id="b920e-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="b920e-146">MachineCred</span></span>|
    |<span data-ttu-id="b920e-147">**voor**</span><span class="sxs-lookup"><span data-stu-id="b920e-147">**For**</span></span>|<span data-ttu-id="b920e-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="b920e-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="b920e-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="b920e-149">**Force**</span></span>|<span data-ttu-id="b920e-150">True</span><span class="sxs-lookup"><span data-stu-id="b920e-150">True</span></span>|
    |<span data-ttu-id="b920e-151">Wacht</span><span class="sxs-lookup"><span data-stu-id="b920e-151">Wait</span></span>|<span data-ttu-id="b920e-152">True</span><span class="sxs-lookup"><span data-stu-id="b920e-152">True</span></span>|
    |<span data-ttu-id="b920e-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="b920e-153">PSComputerName</span></span>|<span data-ttu-id="b920e-154">{""}</span><span class="sxs-lookup"><span data-stu-id="b920e-154">{""}</span></span>|

13. <span data-ttu-id="b920e-155">Toevoegen een **GetWmiObject** activiteit naar de **JoinDomain** volgorde na de **RestartComputer** activiteit.</span><span class="sxs-lookup"><span data-stu-id="b920e-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="b920e-156">Bewerk de eigenschappen niet dezelfde zijn als de vorige **GetWmiObject** activiteit.</span><span class="sxs-lookup"><span data-stu-id="b920e-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="b920e-157">Wanneer u klaar bent met de procedures, de werkstroom ontwerpen-venster als volgt uitzien.</span><span class="sxs-lookup"><span data-stu-id="b920e-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="b920e-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
    ![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="b920e-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>