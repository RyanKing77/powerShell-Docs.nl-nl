---
ms.date: 08/23/2018
keywords: PowerShell-cmdlet
title: Informatie over belangrijke concepten van PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403884"
---
# <a name="understanding-important-powershell-concepts"></a><span data-ttu-id="c9081-103">Informatie over belangrijke concepten van PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9081-103">Understanding important PowerShell concepts</span></span>

<span data-ttu-id="c9081-104">Het ontwerp van de PowerShell kan worden geïntegreerd met de concepten van veel verschillende omgevingen.</span><span class="sxs-lookup"><span data-stu-id="c9081-104">The PowerShell design integrates concepts from many different environments.</span></span> <span data-ttu-id="c9081-105">Aantal van de concepten bekend zijn voor mensen met ervaring in de houders of programmeeromgevingen worden.</span><span class="sxs-lookup"><span data-stu-id="c9081-105">Several of the concepts will be familiar to people with experience in shells or programming environments.</span></span> <span data-ttu-id="c9081-106">Maar weet weinig mensen over al deze.</span><span class="sxs-lookup"><span data-stu-id="c9081-106">However, few people will know about all of them.</span></span> <span data-ttu-id="c9081-107">Kijken naar enkele van deze concepten biedt een handig overzicht van de shell.</span><span class="sxs-lookup"><span data-stu-id="c9081-107">Looking at some of these concepts provides a useful overview of the shell.</span></span>

## <a name="output-is-object-based"></a><span data-ttu-id="c9081-108">Uitvoer is gebaseerd op objecten</span><span class="sxs-lookup"><span data-stu-id="c9081-108">Output is object-based</span></span>

<span data-ttu-id="c9081-109">PowerShell-cmdlets zijn in tegenstelling tot traditionele opdrachtregelinterfaces ontworpen om op te lossen met objecten.</span><span class="sxs-lookup"><span data-stu-id="c9081-109">Unlike traditional command-line interfaces, PowerShell cmdlets are designed to deal with objects.</span></span>
<span data-ttu-id="c9081-110">Een object is gestructureerde gegevens dat is meer dan alleen de reeks tekens op het scherm wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c9081-110">An object is structured information that is more than just the string of characters appearing on the screen.</span></span> <span data-ttu-id="c9081-111">Opdrachtuitvoer altijd bevat extra informatie die u gebruiken kunt als u deze nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="c9081-111">Command output always carries extra information that you can use if you need it.</span></span>

<span data-ttu-id="c9081-112">Als u hulpprogramma's voor tekst-de verwerking hebt gebruikt voor het verwerken van gegevens in het verleden, zult u merken dat ze zich anders gedragen bij gebruik in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9081-112">If you've used text-processing tools to process data in the past, you'll find that they behave differently when used in PowerShell.</span></span> <span data-ttu-id="c9081-113">In de meeste gevallen hoeft u geen tekst-de verwerking hulpprogramma's om specifieke informatie te extraheren.</span><span class="sxs-lookup"><span data-stu-id="c9081-113">In most cases, you don't need text-processing tools to extract specific information.</span></span> <span data-ttu-id="c9081-114">U rechtstreeks toegang tot gedeelten van de gegevens met behulp van standaard-object PowerShell-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="c9081-114">You directly access portions of the data using standard PowerShell object syntax.</span></span>

## <a name="the-command-family-is-extensible"></a><span data-ttu-id="c9081-115">De opdracht serie worden uitgebreid</span><span class="sxs-lookup"><span data-stu-id="c9081-115">The command family is extensible</span></span>

<span data-ttu-id="c9081-116">Interfaces, zoals **cmd.exe** niet bieden een manier waarop u kunt rechtstreeks uitbreiden van de ingebouwde opdrachtenset.</span><span class="sxs-lookup"><span data-stu-id="c9081-116">Interfaces such as **cmd.exe** don't provide a way for you to directly extend the built-in command set.</span></span> <span data-ttu-id="c9081-117">U kunt externe opdrachtregelprogramma's die worden uitgevoerd in maken **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="c9081-117">You can create external command-line tools that run in **cmd.exe**.</span></span> <span data-ttu-id="c9081-118">Maar deze hulpprogramma's voor externe services, zoals Help-integratie niet hebt.</span><span class="sxs-lookup"><span data-stu-id="c9081-118">But these external tools don't have services, such as Help integration.</span></span> <span data-ttu-id="c9081-119">**cmd.exe** niet automatisch zeker weet dat deze externe hulpprogramma's geldige opdrachten zijn.</span><span class="sxs-lookup"><span data-stu-id="c9081-119">**cmd.exe** doesn't automatically know that these external tools are valid commands.</span></span>

<span data-ttu-id="c9081-120">De systeemeigen in PowerShell-opdrachten worden aangeduid als *cmdlets* (uitgesproken als opdracht kunt).</span><span class="sxs-lookup"><span data-stu-id="c9081-120">The native commands in PowerShell are known as *cmdlets* (pronounced command-lets).</span></span> <span data-ttu-id="c9081-121">U kunt uw eigen modules cmdlets maken en functies met gecompileerde code of scripts.</span><span class="sxs-lookup"><span data-stu-id="c9081-121">You can create your own cmdlets modules and functions using compiled code or scripts.</span></span> <span data-ttu-id="c9081-122">Modules kunnen cmdlets en providers toevoegen aan de shell.</span><span class="sxs-lookup"><span data-stu-id="c9081-122">Modules can add cmdlets and providers to the shell.</span></span> <span data-ttu-id="c9081-123">PowerShell biedt ook ondersteuning voor scripts die vergelijkbaar met UNIX-shell-scripts zijn en **cmd.exe** batch-bestanden.</span><span class="sxs-lookup"><span data-stu-id="c9081-123">PowerShell also supports scripts that are analogous to UNIX shell scripts and **cmd.exe** batch files.</span></span>

## <a name="powershell-handles-console-input-and-display"></a><span data-ttu-id="c9081-124">PowerShell wordt gebruikt voor console-invoer en weergave</span><span class="sxs-lookup"><span data-stu-id="c9081-124">PowerShell handles console input and display</span></span>

<span data-ttu-id="c9081-125">Wanneer u een opdracht hebt getypt, verwerkt PowerShell altijd de opdrachtregel invoer rechtstreeks.</span><span class="sxs-lookup"><span data-stu-id="c9081-125">When you type a command, PowerShell always processes the command-line input directly.</span></span> <span data-ttu-id="c9081-126">De uitvoer die u op het scherm ziet ook de opmaak van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9081-126">PowerShell also formats the output that you see on the screen.</span></span> <span data-ttu-id="c9081-127">Dit verschil is van belang omdat deze het werk dat nodig van elke cmdlet vermindert.</span><span class="sxs-lookup"><span data-stu-id="c9081-127">This difference is significant because it reduces the work required of each cmdlet.</span></span> <span data-ttu-id="c9081-128">Het zorgt ervoor dat u altijd dingen dezelfde manier als met een cmdlet doen kunt.</span><span class="sxs-lookup"><span data-stu-id="c9081-128">It ensures that you can always do things the same way with any cmdlet.</span></span> <span data-ttu-id="c9081-129">Cmdlet ontwikkelaars hoeft te schrijven van code voor het parseren van de argumenten voor de opdrachtregel of de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9081-129">Cmdlet developers don't need to write code to parse the command-line arguments or format the output.</span></span>

<span data-ttu-id="c9081-130">Traditionele opdrachtregelprogramma's hebben hun eigen schema's voor het aanvragen en Help-informatie weergeven.</span><span class="sxs-lookup"><span data-stu-id="c9081-130">Traditional command-line tools have their own schemes for requesting and displaying Help.</span></span> <span data-ttu-id="c9081-131">Bepaalde opdrachtregelprogramma's gebruiken **/?**</span><span class="sxs-lookup"><span data-stu-id="c9081-131">Some command-line tools use **/?**</span></span> <span data-ttu-id="c9081-132">voor het activeren van de Help-informatie weergeven; anderen gebruiken **-?**, **/H**, of zelfs **//**.</span><span class="sxs-lookup"><span data-stu-id="c9081-132">to trigger the Help display; others use **-?**, **/H**, or even **//**.</span></span> <span data-ttu-id="c9081-133">Sommige wordt Help weergegeven in het venster van een GUI, in plaats van in de console weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c9081-133">Some will display Help in a GUI window, rather than in the console display.</span></span> <span data-ttu-id="c9081-134">Als u de verkeerde parameter gebruikt, kan het hulpprogramma voor wat u hebt getypt en beginnen met het uitvoeren van een taak automatisch negeren.</span><span class="sxs-lookup"><span data-stu-id="c9081-134">If you use the wrong parameter, the tool might ignore what you typed and begin executing a task automatically.</span></span>
<span data-ttu-id="c9081-135">Omdat PowerShell automatisch parseert en de opdrachtregel, verwerkt de **-?**</span><span class="sxs-lookup"><span data-stu-id="c9081-135">Since PowerShell automatically parses and processes the command line, the **-?**</span></span> <span data-ttu-id="c9081-136">parameter betekent altijd 'Toon Help voor deze opdracht'.</span><span class="sxs-lookup"><span data-stu-id="c9081-136">parameter always means "show me Help for this command".</span></span>

> [!NOTE]
> <span data-ttu-id="c9081-137">Als u een grafische toepassing in PowerShell uitvoert, wordt het venster voor de toepassing wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="c9081-137">If you run a graphic application in PowerShell, the window for the application opens.</span></span>
> <span data-ttu-id="c9081-138">PowerShell is opgetreden alleen bij verwerking van de opdrachtregel invoer u levering of de uitvoer van de toepassing die wordt geretourneerd naar het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="c9081-138">PowerShell intervenes only when processing the command-line input you supply or the application output returned to the console window.</span></span> <span data-ttu-id="c9081-139">Dit heeft geen invloed op hoe de toepassing intern werkt.</span><span class="sxs-lookup"><span data-stu-id="c9081-139">It does not affect how the application works internally.</span></span>

## <a name="powershell-uses-some-c-syntax"></a><span data-ttu-id="c9081-140">Sommige syntaxissen C# maakt gebruik van PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9081-140">PowerShell uses some C# syntax</span></span>

<span data-ttu-id="c9081-141">PowerShell is gebouwd op het .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9081-141">PowerShell is built on the .NET Framework.</span></span> <span data-ttu-id="c9081-142">Deze deelt sommige functies van de syntaxis en trefwoorden met de C#-programmeertaal.</span><span class="sxs-lookup"><span data-stu-id="c9081-142">It shares some syntax features and keywords with the C# programming language.</span></span> <span data-ttu-id="c9081-143">Leren werken met PowerShell kan veel gemakkelijker voor meer informatie over C#.</span><span class="sxs-lookup"><span data-stu-id="c9081-143">Learning PowerShell can make it much easier to learn C#.</span></span> <span data-ttu-id="c9081-144">Als u al bekend met C# bent, maken deze overeenkomsten kunnen leren werken met PowerShell gemakkelijker.</span><span class="sxs-lookup"><span data-stu-id="c9081-144">If you're already familiar with C#, these similarities can make learning PowerShell easier.</span></span>