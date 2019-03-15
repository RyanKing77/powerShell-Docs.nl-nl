---
title: Activiteitsparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251214"
---
# <a name="activity-parameters"></a><span data-ttu-id="9123b-102">Activiteitsparameters</span><span class="sxs-lookup"><span data-stu-id="9123b-102">Activity Parameters</span></span>

<span data-ttu-id="9123b-103">De volgende tabel bevat de aanbevolen namen en de functionaliteit voor de activiteitsparameters.</span><span class="sxs-lookup"><span data-stu-id="9123b-103">The following table lists the recommended names and functionality for activity parameters.</span></span>

|<span data-ttu-id="9123b-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="9123b-104">Parameter</span></span>|<span data-ttu-id="9123b-105">Functionaliteit</span><span class="sxs-lookup"><span data-stu-id="9123b-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="9123b-106">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9123b-106">**Append**</span></span><br><span data-ttu-id="9123b-107">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-107">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-108">Implementeer deze parameter zodat de gebruikers inhoud aan het einde van een resource toevoegen kunnen als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-108">Implement this parameter so that the user can add content to the end of a resource when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-109">**CaseSensitive**</span><span class="sxs-lookup"><span data-stu-id="9123b-109">**CaseSensitive**</span></span><br><span data-ttu-id="9123b-110">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-110">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-111">Deze parameter implementeren, zodat de gebruiker hoofdlettergevoeligheid vereisen kunt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-111">Implement this parameter so the user can require case sensitivity when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-112">**Opdracht**</span><span class="sxs-lookup"><span data-stu-id="9123b-112">**Command**</span></span><br><span data-ttu-id="9123b-113">Gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9123b-113">Data type: String</span></span>|<span data-ttu-id="9123b-114">Deze parameter implementeren, zodat de gebruiker een opdrachttekenreeks om uit te voeren kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-114">Implement this parameter so the user can specify a command string to run.</span></span>|
|<span data-ttu-id="9123b-115">**CompatibleVersion**</span><span class="sxs-lookup"><span data-stu-id="9123b-115">**CompatibleVersion**</span></span><br><span data-ttu-id="9123b-116">Gegevenstype: System.Version object</span><span class="sxs-lookup"><span data-stu-id="9123b-116">Data type: System.Version object</span></span>|<span data-ttu-id="9123b-117">Deze parameter implementeren, zodat de gebruiker de semantiek voor dat de cmdlet compatibel met voor compatibiliteit met eerdere versies zijn moet kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-117">Implement this parameter so the user can specify the semantics that the cmdlet must be compatible with for compatibility with previous versions.</span></span>|
|<span data-ttu-id="9123b-118">**comprimeren**</span><span class="sxs-lookup"><span data-stu-id="9123b-118">**Compress**</span></span><br><span data-ttu-id="9123b-119">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-119">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-120">Implementeer deze parameter zodat de compressie van gegevens wordt gebruikt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-120">Implement this parameter so that data compression is used when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-121">**comprimeren**</span><span class="sxs-lookup"><span data-stu-id="9123b-121">**Compress**</span></span><br><span data-ttu-id="9123b-122">Gegevenstype: Trefwoord</span><span class="sxs-lookup"><span data-stu-id="9123b-122">Data type: Keyword</span></span>|<span data-ttu-id="9123b-123">Deze parameter implementeren zodat de gebruiker het algoritme moet worden gebruikt voor de compressie van gegevens kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-123">Implement this parameter so that the user can specify the algorithm to use for data compression.</span></span>|
|<span data-ttu-id="9123b-124">**Continue**</span><span class="sxs-lookup"><span data-stu-id="9123b-124">**Continuous**</span></span><br><span data-ttu-id="9123b-125">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-125">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-126">Implementeer deze parameter zodat de gegevens worden verwerkt totdat de gebruiker de cmdlet wordt gesloten wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-126">Implement this parameter so that data is processed until the user terminates the cmdlet when the parameter is specified.</span></span> <span data-ttu-id="9123b-127">Als de parameter niet opgegeven is, wordt de cmdlet verwerkt een vooraf gedefinieerde hoeveelheid gegevens en vervolgens de bewerking beëindigd.</span><span class="sxs-lookup"><span data-stu-id="9123b-127">If the parameter is not specified, the cmdlet processes a predefined amount of data and then terminates the operation.</span></span>|
|<span data-ttu-id="9123b-128">**Maken**</span><span class="sxs-lookup"><span data-stu-id="9123b-128">**Create**</span></span><br><span data-ttu-id="9123b-129">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-129">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-130">Implementeer deze parameter om aan te geven dat een resource wordt gemaakt als deze niet al bestaat als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-130">Implement this parameter to indicate that a resource is created if one does not already exist when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-131">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="9123b-131">**Delete**</span></span><br><span data-ttu-id="9123b-132">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-132">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-133">Implementeer deze parameter zodat resources worden verwijderd wanneer de cmdlet kan de bewerking is voltooid wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-133">Implement this parameter so that resources are deleted when the cmdlet has completed its operation when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-134">**Clusterbesturingssysteem**</span><span class="sxs-lookup"><span data-stu-id="9123b-134">**Drain**</span></span><br><span data-ttu-id="9123b-135">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-135">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-136">Implementeer deze parameter om aan te geven dat er een uitstaande werkitems worden verwerkt voordat nieuwe gegevens in de cmdlet worden verwerkt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-136">Implement this parameter to indicate that outstanding work items are processed before the cmdlet processes new data when the parameter is specified.</span></span> <span data-ttu-id="9123b-137">Als de parameter niet opgegeven is, worden de werkitems onmiddellijk verwerkt.</span><span class="sxs-lookup"><span data-stu-id="9123b-137">If the parameter is not specified, the work items are processed immediately.</span></span>|
|<span data-ttu-id="9123b-138">**Wissen**</span><span class="sxs-lookup"><span data-stu-id="9123b-138">**Erase**</span></span><br><span data-ttu-id="9123b-139">Gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="9123b-139">Data type: Int32</span></span>|<span data-ttu-id="9123b-140">Deze parameter implementeren zodat de gebruiker het aantal keren dat die een resource worden gewist opgeven kan voordat deze wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9123b-140">Implement this parameter so that the user can specify the number of times a resource is erased before it is deleted.</span></span>|
|<span data-ttu-id="9123b-141">**ErrorLevel**</span><span class="sxs-lookup"><span data-stu-id="9123b-141">**ErrorLevel**</span></span><br><span data-ttu-id="9123b-142">Gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="9123b-142">Data type: Int32</span></span>|<span data-ttu-id="9123b-143">Implementeer deze parameter zodat de gebruiker kan het niveau van fouten naar het rapport opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-143">Implement this parameter so that the user can specify the level of errors to report.</span></span>|
|<span data-ttu-id="9123b-144">**Uitsluiten**</span><span class="sxs-lookup"><span data-stu-id="9123b-144">**Exclude**</span></span><br><span data-ttu-id="9123b-145">Gegevenstype: String[]</span><span class="sxs-lookup"><span data-stu-id="9123b-145">Data type: String[]</span></span>|<span data-ttu-id="9123b-146">Implementeer deze parameter zodat de gebruiker iets van een activiteit uitsluiten kunt.</span><span class="sxs-lookup"><span data-stu-id="9123b-146">Implement this parameter so that the user can exclude something from an activity.</span></span> <span data-ttu-id="9123b-147">Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9123b-147">For more information about how to use input filters, see [Input Filter Parameters](input-filter-parameters.md).</span></span>|
|<span data-ttu-id="9123b-148">**Filter**</span><span class="sxs-lookup"><span data-stu-id="9123b-148">**Filter**</span></span><br><span data-ttu-id="9123b-149">Gegevenstype: Trefwoord</span><span class="sxs-lookup"><span data-stu-id="9123b-149">Data type: Keyword</span></span>|<span data-ttu-id="9123b-150">Deze parameter implementeren zodat de gebruiker kan een filter dat de resources waarop de actie van de cmdlet uit te voeren selecteert opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-150">Implement this parameter so that the user can specify a filter that selects the resources upon which to perform the cmdlet action.</span></span> <span data-ttu-id="9123b-151">Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9123b-151">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>|
|<span data-ttu-id="9123b-152">**Ga als volgt**</span><span class="sxs-lookup"><span data-stu-id="9123b-152">**Follow**</span></span><br><span data-ttu-id="9123b-153">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-153">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-154">Implementeer deze parameter zodat de voortgang wordt bijgehouden wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-154">Implement this parameter so that progress is tracked when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-155">**Force**</span><span class="sxs-lookup"><span data-stu-id="9123b-155">**Force**</span></span><br><span data-ttu-id="9123b-156">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-156">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-157">Implementeer deze parameter om aan te geven dat de gebruiker een actie uitvoeren kan, zelfs als er beperkingen optreden als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-157">Implement this parameter to indicate that the user can perform an action even if restrictions are encountered when the parameter is specified.</span></span> <span data-ttu-id="9123b-158">De beveiliging is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9123b-158">The parameter does not allow security to be compromised.</span></span> <span data-ttu-id="9123b-159">Deze parameter kunt bijvoorbeeld een gebruiker een alleen-lezenbestand overschrijven.</span><span class="sxs-lookup"><span data-stu-id="9123b-159">For example, this parameter lets a user overwrite a read-only file.</span></span>|
|<span data-ttu-id="9123b-160">**Opnemen**</span><span class="sxs-lookup"><span data-stu-id="9123b-160">**Include**</span></span><br><span data-ttu-id="9123b-161">Gegevenstype: String[]</span><span class="sxs-lookup"><span data-stu-id="9123b-161">Data type: String[]</span></span>|<span data-ttu-id="9123b-162">Implementeer deze parameter zodat de gebruiker iets in een activiteit opnemen kunt.</span><span class="sxs-lookup"><span data-stu-id="9123b-162">Implement this parameter so that the user can include something in an activity.</span></span> <span data-ttu-id="9123b-163">Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9123b-163">For more information about how to use input filters, see [Input Filter Parameters](input-filter-parameters.md).</span></span>|
|<span data-ttu-id="9123b-164">**Incrementele**</span><span class="sxs-lookup"><span data-stu-id="9123b-164">**Incremental**</span></span><br><span data-ttu-id="9123b-165">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-165">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-166">Implementeer deze parameter om aan te geven dat de verwerking stapsgewijs wordt uitgevoerd wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-166">Implement this parameter to indicate that processing is performed incrementally when the parameter is specified.</span></span> <span data-ttu-id="9123b-167">Met deze parameter kunt bijvoorbeeld het uitvoeren van incrementele back-ups die back-up van bestanden alleen sinds de laatste back-up van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9123b-167">For example, this parameter lets a user perform incremental backups that back up files only since the last backup.</span></span>|
|<span data-ttu-id="9123b-168">**InputObject**</span><span class="sxs-lookup"><span data-stu-id="9123b-168">**InputObject**</span></span><br><span data-ttu-id="9123b-169">Gegevenstype: Object</span><span class="sxs-lookup"><span data-stu-id="9123b-169">Data type: Object</span></span>|<span data-ttu-id="9123b-170">Deze parameter implementeren wanneer de cmdlet wordt de invoer uit andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9123b-170">Implement this parameter when the cmdlet takes input from other cmdlets.</span></span> <span data-ttu-id="9123b-171">Als u definieert een **InputObject** parameter altijd opgeven om de **ValueFromPipeline** sleutelwoord wanneer u declareert de **Parameter** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="9123b-171">When you define an **InputObject** parameter, always specify the **ValueFromPipeline** keyword when you declare the **Parameter** attribute.</span></span> <span data-ttu-id="9123b-172">Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9123b-172">For more information about using input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>|
|<span data-ttu-id="9123b-173">**Invoegen**</span><span class="sxs-lookup"><span data-stu-id="9123b-173">**Insert**</span></span><br><span data-ttu-id="9123b-174">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-174">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-175">Implementeer deze parameter zodat de cmdlet wordt een item ingevoegd als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-175">Implement this parameter so that the cmdlet inserts an item when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-176">**Interactief**</span><span class="sxs-lookup"><span data-stu-id="9123b-176">**Interactive**</span></span><br><span data-ttu-id="9123b-177">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-177">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-178">Implementeer deze parameter zodat de cmdlet interactief met de gebruiker werkt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-178">Implement this parameter so that the cmdlet works interactively with the user when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-179">**Interval**</span><span class="sxs-lookup"><span data-stu-id="9123b-179">**Interval**</span></span><br><span data-ttu-id="9123b-180">Gegevenstype: Hash-tabel</span><span class="sxs-lookup"><span data-stu-id="9123b-180">Data type: HashTable</span></span>|<span data-ttu-id="9123b-181">Implementeer deze parameter zodat de gebruiker kan een hash-tabel met trefwoorden die de waarden bevat opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-181">Implement this parameter so that the user can specify a hash table of keywords that contains the values.</span></span> <span data-ttu-id="9123b-182">Het volgende voorbeeld toont voorbeeldwaarden voor de **Interval** parameter: `-interval @{ResumeScan=15; Retry=3}`.</span><span class="sxs-lookup"><span data-stu-id="9123b-182">The following example shows sample values for the **Interval** parameter: `-interval @{ResumeScan=15; Retry=3}`.</span></span>|
|<span data-ttu-id="9123b-183">**Log**</span><span class="sxs-lookup"><span data-stu-id="9123b-183">**Log**</span></span><br><span data-ttu-id="9123b-184">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-184">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-185">Implementeer de controle voor deze parameter de acties van de cmdlet wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-185">Implement this parameter audit the actions of the cmdlet when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-186">**NoClobber**</span><span class="sxs-lookup"><span data-stu-id="9123b-186">**NoClobber**</span></span><br><span data-ttu-id="9123b-187">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-187">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-188">Implementeer deze parameter zodat de bron niet worden overschreven wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-188">Implement this parameter so that the resource will not be overwritten when the parameter is specified.</span></span> <span data-ttu-id="9123b-189">Deze parameter is algemeen van toepassing op de cmdlets die nieuwe objecten maken, zodat ze kunnen worden voorkomen van het overschrijven van bestaande objecten met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="9123b-189">This parameter generally applies to cmdlets that create new objects so that they can be prevented from overwriting existing objects with the same name.</span></span>|
|<span data-ttu-id="9123b-190">**Op de hoogte stellen**</span><span class="sxs-lookup"><span data-stu-id="9123b-190">**Notify**</span></span><br><span data-ttu-id="9123b-191">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-191">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-192">Implementeer deze parameter zodat de gebruiker ontvangt een melding dat de activiteit voltooid is wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-192">Implement this parameter so that the user will be notified that the activity is complete when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-193">**NotifyAddress**</span><span class="sxs-lookup"><span data-stu-id="9123b-193">**NotifyAddress**</span></span><br><span data-ttu-id="9123b-194">Gegevenstype: E-mailadres</span><span class="sxs-lookup"><span data-stu-id="9123b-194">Data type: Email address</span></span>|<span data-ttu-id="9123b-195">Deze parameter implementeren zodat de gebruiker kan het e-mailadres te gebruiken voor het verzenden van een melding opgeven wanneer de **waarschuwen** parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-195">Implement this parameter so that the user can specify the e-mail address to use to send a notification when the **Notify** parameter is specified.</span></span>|
|<span data-ttu-id="9123b-196">**Overschrijven**</span><span class="sxs-lookup"><span data-stu-id="9123b-196">**Overwrite**</span></span><br><span data-ttu-id="9123b-197">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-197">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-198">Implementeer deze parameter zodat de cmdlet worden alle bestaande gegevens overschreven wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-198">Implement this parameter so that the cmdlet overwrites any existing data when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-199">**prompt**</span><span class="sxs-lookup"><span data-stu-id="9123b-199">**Prompt**</span></span><br><span data-ttu-id="9123b-200">Gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9123b-200">Data type: String</span></span>|<span data-ttu-id="9123b-201">Deze parameter implementeren zodat de gebruiker kan een prompt voor de cmdlet opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-201">Implement this parameter so that the user can specify a prompt for the cmdlet.</span></span>|
|<span data-ttu-id="9123b-202">**stille**</span><span class="sxs-lookup"><span data-stu-id="9123b-202">**Quiet**</span></span><br><span data-ttu-id="9123b-203">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-203">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-204">Implementeer deze parameter zodat de cmdlet feedback van gebruikers tijdens de acties onderdrukt als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-204">Implement this parameter so that the cmdlet suppresses user feedback during its actions when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-205">**Recurse**</span><span class="sxs-lookup"><span data-stu-id="9123b-205">**Recurse**</span></span><br><span data-ttu-id="9123b-206">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-206">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-207">Implementeer deze parameter zodat de recursief cmdlet worden de acties uitgevoerd op resources als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-207">Implement this parameter so that the cmdlet recursively performs its actions on resources when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-208">**Herstellen**</span><span class="sxs-lookup"><span data-stu-id="9123b-208">**Repair**</span></span><br><span data-ttu-id="9123b-209">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-209">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-210">Implementeer deze parameter zodat de cmdlet probeert op te lossen iets uit een beschadigde status als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-210">Implement this parameter so that the cmdlet will attempt to correct something from a broken state when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-211">**RepairString**</span><span class="sxs-lookup"><span data-stu-id="9123b-211">**RepairString**</span></span><br><span data-ttu-id="9123b-212">Gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9123b-212">Data type: String</span></span>|<span data-ttu-id="9123b-213">Deze parameter implementeren zodat de gebruiker van een tekenreeks opgeven kan voor het gebruik van wanneer de **herstellen** parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-213">Implement this parameter so that the user can specify a string to use when the **Repair** parameter is specified.</span></span>|
|<span data-ttu-id="9123b-214">**Probeer het opnieuw**</span><span class="sxs-lookup"><span data-stu-id="9123b-214">**Retry**</span></span><br><span data-ttu-id="9123b-215">Gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="9123b-215">Data type: Int32</span></span>|<span data-ttu-id="9123b-216">Deze parameter implementeren, zodat de gebruiker kan het aantal keren dat de cmdlet een actie probeert opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-216">Implement this parameter so the user can specify the number of times the cmdlet will attempt an action.</span></span>|
|<span data-ttu-id="9123b-217">**Selecteer**</span><span class="sxs-lookup"><span data-stu-id="9123b-217">**Select**</span></span><br><span data-ttu-id="9123b-218">Gegevenstype: Sleutelwoord matrix</span><span class="sxs-lookup"><span data-stu-id="9123b-218">Data type: Keyword array</span></span>|<span data-ttu-id="9123b-219">Implementeer deze parameter zodat de gebruiker kan een matrix van de typen objecten opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-219">Implement this parameter so that the user can specify an array of the types of items.</span></span>|
|<span data-ttu-id="9123b-220">**Stream**</span><span class="sxs-lookup"><span data-stu-id="9123b-220">**Stream**</span></span><br><span data-ttu-id="9123b-221">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-221">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-222">Deze parameter implementeren, zodat de gebruiker meerdere uitvoer objecten via de pijplijn streamen kan wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-222">Implement this parameter so the user can stream multiple output objects through the pipeline when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-223">**Strikte**</span><span class="sxs-lookup"><span data-stu-id="9123b-223">**Strict**</span></span><br><span data-ttu-id="9123b-224">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-224">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-225">Implementeer deze parameter zodat alle fouten worden verwerkt als fouten wordt beëindigd wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-225">Implement this parameter so that all errors are handled as terminating errors when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-226">**TempLocation**</span><span class="sxs-lookup"><span data-stu-id="9123b-226">**TempLocation**</span></span><br><span data-ttu-id="9123b-227">Gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9123b-227">Data type: String</span></span>|<span data-ttu-id="9123b-228">Deze parameter implementeren, zodat de gebruiker de locatie van tijdelijke gegevens die worden gebruikt tijdens de bewerking van de cmdlet kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-228">Implement this parameter so the user can specify the location of temporary data that is used during the operation of the cmdlet.</span></span>|
|<span data-ttu-id="9123b-229">**Timeout**</span><span class="sxs-lookup"><span data-stu-id="9123b-229">**Timeout**</span></span><br><span data-ttu-id="9123b-230">Gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="9123b-230">Data type: Int32</span></span>|<span data-ttu-id="9123b-231">Implementeer deze parameter zodat de gebruiker kan de time-outinterval (in milliseconden) opgeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-231">Implement this parameter so that the user can specify the timeout interval (in milliseconds).</span></span>|
|<span data-ttu-id="9123b-232">**Truncate**</span><span class="sxs-lookup"><span data-stu-id="9123b-232">**Truncate**</span></span><br><span data-ttu-id="9123b-233">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-233">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-234">Implementeer deze parameter zodat de cmdlet worden de acties worden afgekapt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-234">Implement this parameter so that the cmdlet will truncate its actions when the parameter is specified.</span></span> <span data-ttu-id="9123b-235">Als de parameter niet opgegeven is, wordt door de cmdlet een andere actie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9123b-235">If the parameter is not specified, the cmdlet performs another action.</span></span>|
|<span data-ttu-id="9123b-236">**Controleer of**</span><span class="sxs-lookup"><span data-stu-id="9123b-236">**Verify**</span></span><br><span data-ttu-id="9123b-237">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-237">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-238">Implementeer deze parameter zodat de cmdlet test om te bepalen of een actie is opgetreden bij de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-238">Implement this parameter so that the cmdlet will test to determine whether an action has occurred when the parameter is specified.</span></span>|
|<span data-ttu-id="9123b-239">**Wacht**</span><span class="sxs-lookup"><span data-stu-id="9123b-239">**Wait**</span></span><br><span data-ttu-id="9123b-240">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9123b-240">Data type: SwitchParameter</span></span>|<span data-ttu-id="9123b-241">Implementeer deze parameter zodat de cmdlet op invoer van de gebruiker wacht voordat u doorgaat als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-241">Implement this parameter so that the cmdlet will wait for user input before continuing when the parameter is specified.</span></span>
|<span data-ttu-id="9123b-242">**Wachttijd**</span><span class="sxs-lookup"><span data-stu-id="9123b-242">**WaitTime**</span></span><br><span data-ttu-id="9123b-243">Gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="9123b-243">Data type: Int32</span></span>|<span data-ttu-id="9123b-244">Deze parameter implementeren zodat de gebruiker kan de duur (in seconden) opgeven dat de cmdlet wordt gewacht op gebruiker invoer wanneer de **wacht** parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9123b-244">Implement this parameter so that the user can specify the duration (in seconds) that the cmdlet will wait for user input when the **Wait** parameter is specified.</span></span>|

## <a name="see-also"></a><span data-ttu-id="9123b-245">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9123b-245">See Also</span></span>

[<span data-ttu-id="9123b-246">Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="9123b-246">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="9123b-247">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9123b-247">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="9123b-248">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9123b-248">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)