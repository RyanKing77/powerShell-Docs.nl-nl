---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: PowerShell-scripts
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451027"
---
# <a name="powershell"></a><span data-ttu-id="7c88c-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c88c-103">PowerShell</span></span>

<span data-ttu-id="7c88c-104">PowerShell is een taakgebaseerde opdrachtregel-shell en scripttaal die is gebouwd op .NET.</span><span class="sxs-lookup"><span data-stu-id="7c88c-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="7c88c-105">PowerShell helpt beheerders en Hoofdgebruikers snel automatiseren van taken die besturingssystemen (Linux, macOS en Windows) en processen te beheren.</span><span class="sxs-lookup"><span data-stu-id="7c88c-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="7c88c-106">PowerShell-opdrachten kunnen u computers beheren vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="7c88c-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="7c88c-107">PowerShell-providers, kunt u toegang tot gegevensarchieven, zoals het register en het certificaatarchief, net zo gemakkelijk als u toegang het bestandssysteem tot.</span><span class="sxs-lookup"><span data-stu-id="7c88c-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="7c88c-108">PowerShell bevat een parser voor uitgebreide expressies en een volledig ontwikkelde scripttaal.</span><span class="sxs-lookup"><span data-stu-id="7c88c-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="7c88c-109">PowerShell is open source</span><span class="sxs-lookup"><span data-stu-id="7c88c-109">PowerShell is open-source</span></span>

<span data-ttu-id="7c88c-110">PowerShell-basis broncode is nu beschikbaar is in GitHub en geopend zodat u kunt bijdragen van de community.</span><span class="sxs-lookup"><span data-stu-id="7c88c-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="7c88c-111">Zie [PowerShell source op GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="7c88c-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="7c88c-112">U kunt beginnen met de bits die u nodig hebt in [ophalen PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="7c88c-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="7c88c-113">Of misschien met een korte Tour langs op [aan de slag](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="7c88c-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="7c88c-114">Ontwerpdoelstellingen van PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c88c-114">PowerShell design goals</span></span>

<span data-ttu-id="7c88c-115">PowerShell is ontworpen voor het verbeteren van de opdrachtregel en scripting-omgeving door langdurige problemen en nieuwe functies toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="7c88c-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="7c88c-116">Zichtbaarheid</span><span class="sxs-lookup"><span data-stu-id="7c88c-116">Discoverability</span></span>

<span data-ttu-id="7c88c-117">PowerShell kunt gemakkelijk detecteren van de functies ervan.</span><span class="sxs-lookup"><span data-stu-id="7c88c-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="7c88c-118">Bijvoorbeeld, als u zoekt een lijst met cmdlets die bekijken en wijzigen van de Windows-services, typt u:</span><span class="sxs-lookup"><span data-stu-id="7c88c-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="7c88c-119">Nadat u ontdekte welke cmdlet voert een taak, u kunt meer informatie over de cmdlet met behulp van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c88c-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="7c88c-120">Als u bijvoorbeeld op het Help-informatie weergeven over de `Get-Service` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="7c88c-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="7c88c-121">De meeste cmdlets geretourneerde objecten die kunnen worden bewerkt en vervolgens weergegeven als tekst om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7c88c-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="7c88c-122">Voor volledig inzicht in de uitvoer van een cmdlet, de uitvoer doorsluizen naar de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c88c-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="7c88c-123">Bijvoorbeeld, de volgende opdracht geeft informatie weer over de leden van de uitvoer van object met de `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c88c-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="7c88c-124">Consistency</span><span class="sxs-lookup"><span data-stu-id="7c88c-124">Consistency</span></span>

<span data-ttu-id="7c88c-125">Systemen beheren, kan een complexe taak zijn.</span><span class="sxs-lookup"><span data-stu-id="7c88c-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="7c88c-126">Hulpprogramma's die een consistente interface Help-informatie voor het beheren van de inherente complexiteit.</span><span class="sxs-lookup"><span data-stu-id="7c88c-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="7c88c-127">Helaas worden niet opdrachtregelprogramma's en scripts COM-objecten bekend zijn voor hun consistentie.</span><span class="sxs-lookup"><span data-stu-id="7c88c-127">Unfortunately, command-line tools and scriptable COM objects aren't known for their consistency.</span></span>

<span data-ttu-id="7c88c-128">De consistentie van PowerShell is een van de primaire activa.</span><span class="sxs-lookup"><span data-stu-id="7c88c-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="7c88c-129">Als u informatie over het gebruik bijvoorbeeld de `Sort-Object` cmdlet, kunt u deze kennis gebruiken om te sorteren van de uitvoer van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c88c-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="7c88c-130">U hebt geen voor meer informatie over de verschillende sorteren routines van elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c88c-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="7c88c-131">Bovendien hoeft cmdlet ontwikkelaars te ontwerpen sorteren functies voor de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7c88c-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="7c88c-132">PowerShell biedt een raamwerk met de belangrijkste functies die ervoor zorgt consistentie dat.</span><span class="sxs-lookup"><span data-stu-id="7c88c-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="7c88c-133">Het framework wordt voorkomen dat bepaalde opties die voor de ontwikkelaar worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="7c88c-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="7c88c-134">Maar hierna wordt de ontwikkeling van cmdlets veel eenvoudiger.</span><span class="sxs-lookup"><span data-stu-id="7c88c-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="7c88c-135">Interactieve en scripting-omgevingen</span><span class="sxs-lookup"><span data-stu-id="7c88c-135">Interactive and scripting environments</span></span>

<span data-ttu-id="7c88c-136">De opdrachtprompt van Windows biedt een interactieve shell met toegang tot de opdrachtregelprogramma's en eenvoudige scripts worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7c88c-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="7c88c-137">Windows Script Host (WSH) scriptbare opdrachtregelprogramma's en COM automation-objecten heeft, maar biedt geen een interactieve shell.</span><span class="sxs-lookup"><span data-stu-id="7c88c-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="7c88c-138">PowerShell combineert een interactieve shell en scripts.</span><span class="sxs-lookup"><span data-stu-id="7c88c-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="7c88c-139">PowerShell kan toegang krijgen tot de opdrachtregelprogramma's, COM-objecten en .NET-klassebibliotheken.</span><span class="sxs-lookup"><span data-stu-id="7c88c-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="7c88c-140">Dankzij deze combinatie van functies breidt de mogelijkheden van de interactieve gebruiker schrijver van het script en de systeembeheerder.</span><span class="sxs-lookup"><span data-stu-id="7c88c-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="7c88c-141">Object-richting</span><span class="sxs-lookup"><span data-stu-id="7c88c-141">Object orientation</span></span>

<span data-ttu-id="7c88c-142">PowerShell is gebaseerd op het object niet als tekst.</span><span class="sxs-lookup"><span data-stu-id="7c88c-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="7c88c-143">De uitvoer van een opdracht is een object.</span><span class="sxs-lookup"><span data-stu-id="7c88c-143">The output of a command is an object.</span></span> <span data-ttu-id="7c88c-144">U kunt de uitvoerobject via de pijplijn verzenden naar een andere opdracht als invoer.</span><span class="sxs-lookup"><span data-stu-id="7c88c-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="7c88c-145">Deze pijplijn biedt een vertrouwde-interface voor mensen met andere shells ervaren.</span><span class="sxs-lookup"><span data-stu-id="7c88c-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="7c88c-146">Dit concept uitbreidt PowerShell door te sturen van objecten in plaats van tekst.</span><span class="sxs-lookup"><span data-stu-id="7c88c-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="7c88c-147">Eenvoudig overgang naar het uitvoeren van scripts</span><span class="sxs-lookup"><span data-stu-id="7c88c-147">Easy transition to scripting</span></span>

<span data-ttu-id="7c88c-148">PowerShell van opdracht vindbaarheid maakt eenvoudig overgang van het typen van opdrachten interactief te maken en uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="7c88c-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="7c88c-149">Transcripten van PowerShell en de geschiedenis van eenvoudig opdrachten kopiëren naar een bestand voor gebruik als een script.</span><span class="sxs-lookup"><span data-stu-id="7c88c-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
