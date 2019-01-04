---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Doel van het scriptobjectmodel van Windows PowerShell ISE
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404594"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="c240d-103">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c240d-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>

<span data-ttu-id="c240d-104">Objecten zijn gekoppeld aan het formulier en de functie van Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="c240d-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="c240d-105">De naslaginformatie over objectmodel bevat informatie over het lid van de eigenschappen en methoden die deze objecten beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="c240d-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="c240d-106">Voorbeelden zijn bedoeld om weer te geven hoe u scripts kunt gebruiken voor rechtstreekse toegang tot deze eigenschappen en methoden.</span><span class="sxs-lookup"><span data-stu-id="c240d-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="c240d-107">Het Scriptobjectmodel vergemakkelijkt het volgende bereik van taken.</span><span class="sxs-lookup"><span data-stu-id="c240d-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="c240d-108">Aanpassen van het uiterlijk van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c240d-108">Customizing the appearance of Windows PowerShell ISE</span></span>

<span data-ttu-id="c240d-109">Het objectmodel kunt u de toepassings- en opties wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c240d-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="c240d-110">Bijvoorbeeld, kunt u ze als volgt:</span><span class="sxs-lookup"><span data-stu-id="c240d-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="c240d-111">U kunt de kleur van fouten, waarschuwingen, uitgebreide uitvoer wijzigen en foutopsporing weergeeft.</span><span class="sxs-lookup"><span data-stu-id="c240d-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>
- <span data-ttu-id="c240d-112">U kunt ophalen of instellen van de achtergrondkleuren voor het opdrachtvenster, het deelvenster Uitvoer en het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="c240d-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>
- <span data-ttu-id="c240d-113">U kunt de voorgrondkleur van het deelvenster Uitvoer instellen.</span><span class="sxs-lookup"><span data-stu-id="c240d-113">You can set the foreground color for the Output pane.</span></span>
- <span data-ttu-id="c240d-114">U kunt het lettertype en de tekengrootte instellen voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c240d-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>
- <span data-ttu-id="c240d-115">U kunt waarschuwingen configureren.</span><span class="sxs-lookup"><span data-stu-id="c240d-115">You can configure warnings.</span></span> <span data-ttu-id="c240d-116">Deze instelling bevat waarschuwingen die zijn uitgegeven wanneer een bestand wordt geopend in meerdere tabbladen met PowerShell of wanneer een script in het bestand wordt uitgevoerd voordat het bestand is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c240d-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>
- <span data-ttu-id="c240d-117">U kunt schakelen tussen een weergave waarbij het scriptvenster en het deelvenster Uitvoer side-by-side zijn en een weergave waarbij het scriptvenster is boven op het deelvenster Uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c240d-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="c240d-118">U kunt het deelvenster opdracht verankeren aan de onderkant of aan de bovenkant van het deelvenster Uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c240d-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="c240d-119">Verbetering van de functionaliteit van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c240d-119">Enhancing the functionality of Windows PowerShell ISE</span></span>

<span data-ttu-id="c240d-120">U kunt het objectmodel gebruiken voor het verbeteren van de functionaliteit van Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c240d-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="c240d-121">U kunt bijvoorbeeld het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="c240d-121">For example, you can:</span></span>

- <span data-ttu-id="c240d-122">Toevoegen en wijzigen van het exemplaar van Windows PowerShell ISE zelf.</span><span class="sxs-lookup"><span data-stu-id="c240d-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="c240d-123">Bijvoorbeeld, als u wilt wijzigen van de menu's, kunt u nieuwe menu-items toevoegen en het nieuwe menu-items worden toegewezen aan de scripts.</span><span class="sxs-lookup"><span data-stu-id="c240d-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>
- <span data-ttu-id="c240d-124">Scripts maken die enkele van de taken die u uitvoeren kunt met behulp van de opdrachten in het menu en knoppen in Windows PowerShell ISE uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c240d-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="c240d-125">Bijvoorbeeld, u kunt toevoegen, verwijderen of Selecteer een PowerShell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="c240d-125">For example, you can add, remove, or select a PowerShell tab.</span></span>
- <span data-ttu-id="c240d-126">Aanvullende taken die kunnen worden uitgevoerd met behulp van opdrachten in het menu en knoppen.</span><span class="sxs-lookup"><span data-stu-id="c240d-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="c240d-127">U kunt bijvoorbeeld een PowerShell-tabblad wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c240d-127">For example, you can rename a PowerShell tab.</span></span>
- <span data-ttu-id="c240d-128">Tekst buffers voor het opdrachtvenster, het deelvenster Uitvoer en het scriptvenster die gekoppeld aan een bestand zijn te manipuleren.</span><span class="sxs-lookup"><span data-stu-id="c240d-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="c240d-129">U kunt bijvoorbeeld het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="c240d-129">For example, you can:</span></span>
  - <span data-ttu-id="c240d-130">Ophalen of instellen van alle tekst.</span><span class="sxs-lookup"><span data-stu-id="c240d-130">Get or set all text.</span></span>
  - <span data-ttu-id="c240d-131">Ophalen of instellen van een selectie van tekst.</span><span class="sxs-lookup"><span data-stu-id="c240d-131">Get or set a text selection.</span></span>
  - <span data-ttu-id="c240d-132">Uitvoeren van een script of een geselecteerd gedeelte van een script uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c240d-132">Run a script or run a selected portion of a script.</span></span>
  - <span data-ttu-id="c240d-133">Een regel in beeld schuiven.</span><span class="sxs-lookup"><span data-stu-id="c240d-133">Scroll a line into view.</span></span>
  - <span data-ttu-id="c240d-134">Tekst invoegen op de positie van een caret-teken.</span><span class="sxs-lookup"><span data-stu-id="c240d-134">Insert text at a caret position.</span></span>
  - <span data-ttu-id="c240d-135">Selecteer een blok tekst.</span><span class="sxs-lookup"><span data-stu-id="c240d-135">Select a block of text.</span></span>
  - <span data-ttu-id="c240d-136">De laatste regel getal ophalen.</span><span class="sxs-lookup"><span data-stu-id="c240d-136">Get the last line number.</span></span>
- <span data-ttu-id="c240d-137">Bestandsbewerkingen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c240d-137">Perform file operations.</span></span> <span data-ttu-id="c240d-138">U kunt bijvoorbeeld het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="c240d-138">For example, you can:</span></span>
  - <span data-ttu-id="c240d-139">Openen van een bestand, een bestand opslaat of een bestand opslaan met behulp van een andere naam.</span><span class="sxs-lookup"><span data-stu-id="c240d-139">Open a file, save a file, or save a file by using a different name.</span></span>
  - <span data-ttu-id="c240d-140">Bepalen of een bestand is gewijzigd nadat het laatst is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c240d-140">Determine whether a file has been changed after it was last saved.</span></span>
  - <span data-ttu-id="c240d-141">Naam van het bestand ophalen.</span><span class="sxs-lookup"><span data-stu-id="c240d-141">Get the file name.</span></span>
  - <span data-ttu-id="c240d-142">Selecteer een bestand.</span><span class="sxs-lookup"><span data-stu-id="c240d-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="c240d-143">Het automatiseren van taken</span><span class="sxs-lookup"><span data-stu-id="c240d-143">Automating tasks</span></span>

<span data-ttu-id="c240d-144">U kunt het Scriptobjectmodel sneltoetsen voor frequente activiteiten maken.</span><span class="sxs-lookup"><span data-stu-id="c240d-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="c240d-145">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c240d-145">See also</span></span>

- [<span data-ttu-id="c240d-146">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="c240d-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)