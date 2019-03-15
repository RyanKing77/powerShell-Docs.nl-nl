---
title: Windows PowerShell-programmeurs&#39;s handleiding | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 1f7b5b60b202f4de0cf3d44b65057f5edd41f2b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849642"
---
# <a name="windows-powershell-programmer39s-guide"></a><span data-ttu-id="94307-102">Windows PowerShell-programmeurs&#39;s-handleiding</span><span class="sxs-lookup"><span data-stu-id="94307-102">Windows PowerShell Programmer&#39;s Guide</span></span>

<span data-ttu-id="94307-103">Deze programmeergids is gericht op ontwikkelaars die geïnteresseerd zijn in een opdrachtregel beheeromgeving voor systeembeheerders te bieden.</span><span class="sxs-lookup"><span data-stu-id="94307-103">This programmer's guide is targeted at developers who are interested in providing a command-line management environment for system administrators.</span></span> <span data-ttu-id="94307-104">Windows PowerShell biedt een eenvoudige manier om u opdrachten voor het beheer die beschikbaar maken van .NET-objecten, terwijl u Windows PowerShell met het meeste werk voor u doen kunt maken.</span><span class="sxs-lookup"><span data-stu-id="94307-104">Windows PowerShell provides a simple way for you to build management commands that expose .NET objects, while allowing Windows PowerShell to do most of the work for you.</span></span>

<span data-ttu-id="94307-105">U moet bij de ontwikkeling van traditionele opdracht wordt een parameter-parser, een parameter binder, filters en alle andere functionaliteit die door elke opdracht schrijven.</span><span class="sxs-lookup"><span data-stu-id="94307-105">In traditional command development, you are required to write a parameter parser, a parameter binder, filters, and all other functionality exposed by each command.</span></span> <span data-ttu-id="94307-106">Windows PowerShell biedt het volgende om door te gemakkelijk voor u het schrijven van opdrachten:</span><span class="sxs-lookup"><span data-stu-id="94307-106">Windows PowerShell provides the following to make it easy for you to write commands:</span></span>

- <span data-ttu-id="94307-107">Een krachtige Windows PowerShell-runtime (uitvoeringsengine) met een eigen parser en een mechanisme voor automatisch opdrachtparameters-binding.</span><span class="sxs-lookup"><span data-stu-id="94307-107">A powerful Windows PowerShell runtime (execution engine) with its own parser and a mechanism for automatically binding command parameters.</span></span>

- <span data-ttu-id="94307-108">Hulpprogramma's voor het formatteren en weergeven van opdrachtresultaten met behulp van een opdrachtregel-interpreter (CLI).</span><span class="sxs-lookup"><span data-stu-id="94307-108">Utilities for formatting and displaying command results using a command line interpreter (CLI).</span></span>

- <span data-ttu-id="94307-109">Ondersteuning voor een hoge mate van de functionaliteit (via Windows PowerShell-providers), waarmee u eenvoudig toegang krijgen tot opgeslagen gegevens.</span><span class="sxs-lookup"><span data-stu-id="94307-109">Support for high levels of functionality  (through Windows PowerShell providers) that make it easy to access stored data.</span></span>

  <span data-ttu-id="94307-110">Weinig kosten, kunt u een .NET-object door een uitgebreide opdracht of een reeks opdrachten die een volledige opdrachtregelervaring wordt aangeboden door de beheerder vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="94307-110">At little cost, you can represent a .NET object by a rich command or set of commands that will offer a complete command-line experience to the administrator.</span></span>

  <span data-ttu-id="94307-111">De volgende sectie bevat informatie over de belangrijkste concepten van Windows PowerShell en de voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="94307-111">The next section covers the key Windows PowerShell concepts and terms.</span></span> <span data-ttu-id="94307-112">Maak uzelf bekend met deze concepten en termen voordat u begint met ontwikkelen.</span><span class="sxs-lookup"><span data-stu-id="94307-112">Familiarize yourself with these concepts and terms before starting development.</span></span>

## <a name="about-windows-powershell"></a><span data-ttu-id="94307-113">Over Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="94307-113">About Windows PowerShell</span></span>

<span data-ttu-id="94307-114">Windows PowerShell definieert verschillende soorten opdrachten die u kunt gebruiken in ontwikkeling.</span><span class="sxs-lookup"><span data-stu-id="94307-114">Windows PowerShell defines several types of commands that you can use in development.</span></span> <span data-ttu-id="94307-115">Deze opdrachten zijn: functies, filters, scripts, aliassen en uitvoerbare bestanden (toepassingen).</span><span class="sxs-lookup"><span data-stu-id="94307-115">These commands include: functions, filters, scripts, aliases, and executables (applications).</span></span> <span data-ttu-id="94307-116">Het belangrijkste opdrachttype besproken in deze handleiding is een eenvoudige, kleine opdracht met de naam van een 'cmdlet'.</span><span class="sxs-lookup"><span data-stu-id="94307-116">The main command type discussed in this guide is a simple, small command called a "cmdlet".</span></span> <span data-ttu-id="94307-117">Windows PowerShell het levert een set cmdlets en biedt volledige ondersteuning voor aanpassing van de cmdlet aan de behoeften van uw omgeving.</span><span class="sxs-lookup"><span data-stu-id="94307-117">Windows PowerShell furnishes a set of cmdlets and fully supports cmdlet customization to suit your environment.</span></span> <span data-ttu-id="94307-118">De Windows PowerShell-runtime verwerkt alle opdrachttypen net als cmdlets, met behulp van pijplijnen.</span><span class="sxs-lookup"><span data-stu-id="94307-118">The Windows PowerShell runtime processes all command types just as it does cmdlets, using pipelines.</span></span>

<span data-ttu-id="94307-119">Windows PowerShell biedt naast opdrachten ondersteuning voor verschillende aanpasbare providers van de Windows PowerShell die beschikbaar op specifieke sets met cmdlets.</span><span class="sxs-lookup"><span data-stu-id="94307-119">In addition to commands, Windows PowerShell supports various customizable Windows PowerShell providers that make available specific sets of cmdlets.</span></span> <span data-ttu-id="94307-120">De shell werkt in de Windows PowerShell-opgegeven hosttoepassing (Windows PowerShell.exe), maar het is even toegankelijk vanuit een aangepaste hosttoepassing die u ontwikkelen kunt om te voldoen aan specifieke vereisten.</span><span class="sxs-lookup"><span data-stu-id="94307-120">The shell operates within the Windows PowerShell-provided host application (Windows PowerShell.exe), but it is equally accessible from a custom host application that you can develop to meet specific requirements.</span></span> <span data-ttu-id="94307-121">Zie voor meer informatie, [hoe Windows PowerShell werkt](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="94307-121">For more information, see [How Windows PowerShell Works](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

### <a name="windows-powershell-cmdlets"></a><span data-ttu-id="94307-122">Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="94307-122">Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="94307-123">Een cmdlet is een lichtgewicht opdracht die wordt gebruikt in de Windows PowerShell-omgeving.</span><span class="sxs-lookup"><span data-stu-id="94307-123">A cmdlet is a lightweight command that is used in the Windows PowerShell environment.</span></span> <span data-ttu-id="94307-124">De Windows PowerShell-runtime roept deze cmdlets binnen de context van automatiseringsscripts die beschikbaar zijn op de opdrachtregel en de Windows PowerShell-runtime ook roept deze via een programma via Windows PowerShell-APIs.</span><span class="sxs-lookup"><span data-stu-id="94307-124">The Windows PowerShell runtime invokes these cmdlets within the context of automation scripts that are provided at the command line, and the Windows PowerShell runtime also invokes them programmatically through Windows PowerShell APIs.</span></span>

<span data-ttu-id="94307-125">Zie voor meer informatie over cmdlets, [schrijven van een Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="94307-125">For more information about cmdlets, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

### <a name="windows-powershell-providers"></a><span data-ttu-id="94307-126">Windows PowerShell Providers</span><span class="sxs-lookup"><span data-stu-id="94307-126">Windows PowerShell Providers</span></span>

<span data-ttu-id="94307-127">Bij het uitvoeren van beheertaken, moet de gebruiker mogelijk gegevens die zijn opgeslagen in een gegevensarchief (bijvoorbeeld, het bestandssysteem, het Windows-register of een certificaatarchief) te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="94307-127">In performing administrative tasks, the user may need to examine data stored in a data store (for example, the file system, the Windows Registry, or a certificate store).</span></span> <span data-ttu-id="94307-128">Windows PowerShell definieert om deze bewerkingen gemakkelijker te maken, een module met de naam van een Windows PowerShell-provider die kan worden gebruikt voor toegang tot een bepaald gegevensarchief, zoals het Windows-register.</span><span class="sxs-lookup"><span data-stu-id="94307-128">To make these operations easier, Windows PowerShell defines a module called a Windows PowerShell provider that can be used to access a specific data store, such as the Windows Registry.</span></span> <span data-ttu-id="94307-129">Elke provider ondersteunt een set gerelateerde cmdlets voor het geven van de gebruiker een symmetrisch weergave van de gegevens in de store.</span><span class="sxs-lookup"><span data-stu-id="94307-129">Each provider supports a set of related cmdlets to give the user a symmetrical view of the data in the store.</span></span>

<span data-ttu-id="94307-130">Windows PowerShell biedt verschillende standaard Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="94307-130">Windows PowerShell provides several default Windows PowerShell providers.</span></span> <span data-ttu-id="94307-131">De Register-provider ondersteunt bijvoorbeeld navigatie en manipuleren van het Windows-register.</span><span class="sxs-lookup"><span data-stu-id="94307-131">For example, the Registry provider supports navigation and manipulation of the Windows Registry.</span></span> <span data-ttu-id="94307-132">Registersleutels worden weergegeven als items en registerwaarden worden behandeld als eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="94307-132">Registry keys are represented as items, and registry values are treated as properties.</span></span>

<span data-ttu-id="94307-133">Als u beschikbaar maakt voor een gegevensopslag die de gebruiker toegang nodig hebben, moet u mogelijk het schrijven van uw eigen Windows PowerShell-provider, zoals beschreven in [het maken van Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="94307-133">If you expose a data store that the user will need to access, you might need to write your own Windows PowerShell provider, as described in [Creating Windows PowerShell Providers](./how-to-create-a-windows-powershell-provider.md).</span></span> <span data-ttu-id="94307-134">Zie voor meer informatie aboutWindows PowerShell-providers, [hoe Windows PowerShell werkt](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="94307-134">For more information aboutWindows PowerShell providers, see [How Windows PowerShell Works](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

### <a name="host-application"></a><span data-ttu-id="94307-135">Host-toepassing</span><span class="sxs-lookup"><span data-stu-id="94307-135">Host Application</span></span>

<span data-ttu-id="94307-136">Windows PowerShell bevat de standaard host toepassing powershell.exe, dit is een consoletoepassing die communiceert met de gebruiker en die als host fungeert voor de Windows PowerShell-runtime met behulp van een consolevenster.</span><span class="sxs-lookup"><span data-stu-id="94307-136">Windows PowerShell includes the default host application powershell.exe, which is a console application that interacts with the user and hosts the Windows PowerShell runtime using a console window.</span></span>

<span data-ttu-id="94307-137">Zelden moet u het schrijven van uw eigen hosttoepassing voor Windows PowerShell, hoewel aanpassing wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="94307-137">Only rarely will you need to write your own host application for Windows PowerShell, although customization is supported.</span></span> <span data-ttu-id="94307-138">Een situatie waarin u uw eigen toepassing mogelijk is wanneer er een vereiste voor een GUI-interface die uitgebreider dan de interface die is geleverd door de standaard-hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="94307-138">One case in which you might need your own application is when you have a requirement for a GUI interface that is richer than the interface provided by the default host application.</span></span> <span data-ttu-id="94307-139">U kunt ook een aangepaste toepassing wanneer u uw GUI zijn gebaseerd op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="94307-139">You might also want a custom application when you are basing your GUI on the command line.</span></span> <span data-ttu-id="94307-140">Zie voor meer informatie,[over het maken van een Windows PowerShell-hosttoepassing](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).</span><span class="sxs-lookup"><span data-stu-id="94307-140">For more information, see[How to Create a Windows PowerShell Host Application](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).</span></span>

### <a name="windows-powershell-runtime"></a><span data-ttu-id="94307-141">Windows PowerShell-Runtime</span><span class="sxs-lookup"><span data-stu-id="94307-141">Windows PowerShell Runtime</span></span>

<span data-ttu-id="94307-142">De Windows PowerShell-runtime is de engine voor het uitvoeren waarmee de verwerking van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="94307-142">The Windows PowerShell runtime is the execution engine that implements command processing.</span></span> <span data-ttu-id="94307-143">Het bevat de klassen die de interface tussen de host-toepassing en Windows PowerShell-opdrachten en -providers bieden.</span><span class="sxs-lookup"><span data-stu-id="94307-143">It includes the classes that provide the interface between the host application and Windows PowerShell commands and providers.</span></span> <span data-ttu-id="94307-144">De Windows PowerShell-runtime wordt geïmplementeerd als een runspace-object voor de huidige Windows PowerShell-sessie, dit is de operationele omgeving waarin de shell en de opdrachten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="94307-144">The Windows PowerShell runtime is implemented as a runspace object for the current Windows PowerShell session, which is the operational environment in which the shell and the commands execute.</span></span> <span data-ttu-id="94307-145">Zie voor operationele details [hoe Windows PowerShell werkt](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="94307-145">For operational details, see [How Windows PowerShell Works](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

### <a name="windows-powershell-language"></a><span data-ttu-id="94307-146">Windows PowerShell Language</span><span class="sxs-lookup"><span data-stu-id="94307-146">Windows PowerShell Language</span></span>

<span data-ttu-id="94307-147">De Windows PowerShell-taal biedt scripting functies en methoden om aan te roepen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="94307-147">The Windows PowerShell language provides scripting functions and mechanisms to invoke commands.</span></span> <span data-ttu-id="94307-148">Voor volledige scripting-informatie, Zie dat de Windows PowerShell-Naslaggids wordt geleverd met Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94307-148">For complete scripting information, see the Windows PowerShell Language Reference shipped with Windows PowerShell.</span></span>

### <a name="extended-type-system-ets"></a><span data-ttu-id="94307-149">Uitgebreid typesysteem (ETS)</span><span class="sxs-lookup"><span data-stu-id="94307-149">Extended Type System (ETS)</span></span>

<span data-ttu-id="94307-150">Windows PowerShell biedt toegang tot tal van andere objecten, zoals .NET en XML-objecten.</span><span class="sxs-lookup"><span data-stu-id="94307-150">Windows PowerShell provides access to a variety of different objects, such as .NET and XML objects.</span></span> <span data-ttu-id="94307-151">Als u wilt weergeven van een algemene abstractielaag voor alle objecttypen gebruikt de shell als gevolg hiervan zijn uitgebreid typesysteem (ETS).</span><span class="sxs-lookup"><span data-stu-id="94307-151">As a consequence, to present a common abstraction for all object types the shell uses its extended type system (ETS).</span></span> <span data-ttu-id="94307-152">De meeste ETS functionaliteit is transparant voor de gebruiker, maar het script of de .NET-ontwikkelaar gebruikt deze voor de volgende doeleinden:</span><span class="sxs-lookup"><span data-stu-id="94307-152">Most ETS functionality is transparent to the user, but the script or .NET developer uses it for the following purposes:</span></span>

- <span data-ttu-id="94307-153">Een subset van de leden van specifieke objecten bekijken.</span><span class="sxs-lookup"><span data-stu-id="94307-153">Viewing a subset of the members of specific objects.</span></span> <span data-ttu-id="94307-154">Windows PowerShell biedt een 'aangepast' overzicht van enkele specifieke objecttypen.</span><span class="sxs-lookup"><span data-stu-id="94307-154">Windows PowerShell provides an "adapted" view of several specific object types.</span></span>

- <span data-ttu-id="94307-155">Leden toevoegen aan de bestaande objecten.</span><span class="sxs-lookup"><span data-stu-id="94307-155">Adding members to existing objects.</span></span>

- <span data-ttu-id="94307-156">Toegang tot objecten geserialiseerd.</span><span class="sxs-lookup"><span data-stu-id="94307-156">Access to serialized objects.</span></span>

- <span data-ttu-id="94307-157">Schrijven aangepaste objecten.</span><span class="sxs-lookup"><span data-stu-id="94307-157">Writing customized objects.</span></span>

  <span data-ttu-id="94307-158">ETS gebruikt, kunt u nieuwe flexibele 'typen' die compatibel zijn met de Windows PowerShell-taal.</span><span class="sxs-lookup"><span data-stu-id="94307-158">Using ETS, you can create flexible new "types" that are compatible with the Windows PowerShell language.</span></span> <span data-ttu-id="94307-159">Als u een .NET-ontwikkelaar bent, u kunt werken met objecten met dezelfde semantiek als de Windows PowerShell-taal voor het uitvoeren van scripts, bijvoorbeeld geldt, om te bepalen als een object resultaat zijn `true`.</span><span class="sxs-lookup"><span data-stu-id="94307-159">If you are a .NET developer, you are able to work with objects using the same semantics as the Windows PowerShell language applies to scripting, for example, to determine if an object evaluates to `true`.</span></span>

  <span data-ttu-id="94307-160">Zie voor meer informatie over ETS en hoe objecten worden gebruikt door Windows PowerShell, [Windows PowerShell-Object concepten](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).</span><span class="sxs-lookup"><span data-stu-id="94307-160">For more information about ETS and how Windows PowerShell uses objects, see [Windows PowerShell Object Concepts](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).</span></span>

## <a name="programming-for-windows-powershell"></a><span data-ttu-id="94307-161">Programmeren voor Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="94307-161">Programming for Windows PowerShell</span></span>

<span data-ttu-id="94307-162">Windows PowerShell definieert de code voor opdrachten, providers en andere programmamodules met behulp van .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94307-162">Windows PowerShell defines its code for commands, providers, and other program modules using the .NET Framework.</span></span> <span data-ttu-id="94307-163">U bent niet beperkt tot het gebruik van Microsoft Visual Studio bij het maken van aangepaste modules voor Windows PowerShell, hoewel de voorbeelden in deze handleiding zijn genoemd om uit te voeren in dit hulpprogramma.</span><span class="sxs-lookup"><span data-stu-id="94307-163">You are not confined to the use of Microsoft Visual Studio in creating customized modules for Windows PowerShell, although the samples provided in this guide are known to run in this tool.</span></span> <span data-ttu-id="94307-164">U kunt een .NET-taal die ondersteuning biedt voor klassenovername van de en het gebruik van kenmerken.</span><span class="sxs-lookup"><span data-stu-id="94307-164">You can use any .NET language that supports class inheritance and the use of attributes.</span></span> <span data-ttu-id="94307-165">In sommige gevallen vereisen Windows PowerShell-APIs de programmeertaal te kunnen zijn voor toegang tot algemene typen.</span><span class="sxs-lookup"><span data-stu-id="94307-165">In some cases, Windows PowerShell APIs require the programming language to be able to access generic types.</span></span>

## <a name="programmers-reference"></a><span data-ttu-id="94307-166">Naslaggids</span><span class="sxs-lookup"><span data-stu-id="94307-166">Programmer's Reference</span></span>

<span data-ttu-id="94307-167">Ter referentie bij het ontwikkelen voor Windows PowerShell, Zie de [Windows PowerShell SDK](../windows-powershell-reference.md).</span><span class="sxs-lookup"><span data-stu-id="94307-167">For reference when developing for Windows PowerShell, see the [Windows PowerShell SDK](../windows-powershell-reference.md).</span></span>

## <a name="getting-started-using-windows-powershell"></a><span data-ttu-id="94307-168">Aan de slag met behulp van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="94307-168">Getting Started Using Windows PowerShell</span></span>

<span data-ttu-id="94307-169">Zie voor meer informatie over het starten van de Windows PowerShell-shell gebruiken de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) geleverd met Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94307-169">For more information about starting to use the Windows PowerShell shell, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) shipped with Windows PowerShell.</span></span> <span data-ttu-id="94307-170">Een document van de drie kolommen Naslaggids wordt ook een inleiding voor gebruik van de cmdlet geleverd.</span><span class="sxs-lookup"><span data-stu-id="94307-170">A Quick Reference tri-fold document is also supplied as a primer for cmdlet use.</span></span>

## <a name="contents-of-this-guide"></a><span data-ttu-id="94307-171">Inhoud van deze handleiding</span><span class="sxs-lookup"><span data-stu-id="94307-171">Contents of This Guide</span></span>

|<span data-ttu-id="94307-172">Onderwerp</span><span class="sxs-lookup"><span data-stu-id="94307-172">Topic</span></span>|<span data-ttu-id="94307-173">Definitie</span><span class="sxs-lookup"><span data-stu-id="94307-173">Definition</span></span>|
|-----------|----------------|
|[<span data-ttu-id="94307-174">Over het maken van een Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="94307-174">How to Create a Windows PowerShell Provider</span></span>](./how-to-create-a-windows-powershell-provider.md)|<span data-ttu-id="94307-175">Deze sectie wordt beschreven hoe u een Windows PowerShell-provider voor Windows PowerShell maakt.</span><span class="sxs-lookup"><span data-stu-id="94307-175">This section describes how to build a Windows PowerShell provider for Windows PowerShell.</span></span>|
|[<span data-ttu-id="94307-176">Over het maken van een Windows PowerShell-hosttoepassing</span><span class="sxs-lookup"><span data-stu-id="94307-176">How to Create a Windows PowerShell Host Application</span></span>](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|<span data-ttu-id="94307-177">Deze sectie wordt beschreven hoe u een hosttoepassing die wordt bewerkt een runspace schrijft en over het schrijven van een host-toepassing die een eigen aangepaste host implementeert.</span><span class="sxs-lookup"><span data-stu-id="94307-177">This section describes how to write a host application that manipulates a runspace and how to write a host application that implements its own custom host.</span></span>|
|[<span data-ttu-id="94307-178">Over het maken van een PowerShell-module Windows</span><span class="sxs-lookup"><span data-stu-id="94307-178">How to Create a Windows PowerShell Snap-in</span></span>](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|<span data-ttu-id="94307-179">Deze sectie beschrijft het maken van een module die wordt gebruikt voor het registreren van alle cmdlets en providers in een assembly en over het maken van een aangepaste module.</span><span class="sxs-lookup"><span data-stu-id="94307-179">This section describes how to create a snap-in that is used to register all cmdlets and providers in an assembly and how to create a custom snap-in.</span></span>|
|[<span data-ttu-id="94307-180">Over het maken van een Console-Shell</span><span class="sxs-lookup"><span data-stu-id="94307-180">How to Create a Console Shell</span></span>](./how-to-create-a-console-shell.md)|<span data-ttu-id="94307-181">Deze sectie beschrijft het maken van een console-shell die kan niet worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="94307-181">This section describes how to create a console shell that is not extensible.</span></span>|
|[<span data-ttu-id="94307-182">Windows PowerShell-concepten</span><span class="sxs-lookup"><span data-stu-id="94307-182">Windows PowerShell Concepts</span></span>](./windows-powershell-concepts.md)|<span data-ttu-id="94307-183">In deze sectie bevat algemene informatie waarmee u inzicht in de Windows PowerShell vanuit het oogpunt van een ontwikkelaar.</span><span class="sxs-lookup"><span data-stu-id="94307-183">This section contains conceptual information that will help you understand Windows PowerShell from the viewpoint of a developer.</span></span>|

## <a name="see-also"></a><span data-ttu-id="94307-184">Zie ook</span><span class="sxs-lookup"><span data-stu-id="94307-184">See Also</span></span>

[<span data-ttu-id="94307-185">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="94307-185">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)