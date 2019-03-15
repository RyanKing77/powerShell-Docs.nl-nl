---
title: Een PowerShell-Module installeren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: f7899713dd273b793017adfa0a20b3ff3352b62a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851126"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="94378-102">Een PowerShell-module installeren</span><span class="sxs-lookup"><span data-stu-id="94378-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="94378-103">Nadat u uw PowerShell-module hebt gemaakt, wordt u waarschijnlijk wilt voor het installeren van de module op een systeem, zodat u of anderen kunnen deze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="94378-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="94378-104">In het algemeen, bestaat deze gewoon van het kopiëren van de module-bestanden (ie, de .psm1 of de binaire assembly, het module-manifest en andere gekoppelde bestanden) naar een map op die computer.</span><span class="sxs-lookup"><span data-stu-id="94378-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="94378-105">Voor een zeer klein project, kan dit net zo eenvoudig als kopiëren en plakken van de bestanden met Windows Explorer naar een externe computer; echter, voor grotere oplossingen kunt u een meer geavanceerde installatieproces gebruiken.</span><span class="sxs-lookup"><span data-stu-id="94378-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="94378-106">Ongeacht hoe u uw module bij het systeem ophalen, kunt PowerShell een aantal technieken waarmee gebruikers vinden en gebruiken van uw modules kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="94378-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="94378-107">(Zie voor meer informatie, [importeren van een PowerShell-Module](./importing-a-powershell-module.md).) Daarom het belangrijkste probleem voor de installatie is ervoor te zorgen dat PowerShell zal kunnen vinden van uw module.</span><span class="sxs-lookup"><span data-stu-id="94378-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="94378-108">In dit onderwerp bevat de volgende secties:</span><span class="sxs-lookup"><span data-stu-id="94378-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="94378-109">Regels voor het installeren van Modules</span><span class="sxs-lookup"><span data-stu-id="94378-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="94378-110">WHERE-Modules installeren</span><span class="sxs-lookup"><span data-stu-id="94378-110">Where to Install Modules</span></span>

- <span data-ttu-id="94378-111">De installatie van meerdere versies van een Module</span><span class="sxs-lookup"><span data-stu-id="94378-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="94378-112">Opdrachtnaamconflicten verwerken</span><span class="sxs-lookup"><span data-stu-id="94378-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="94378-113">Regels voor het installeren van Modules</span><span class="sxs-lookup"><span data-stu-id="94378-113">Rules for Installing Modules</span></span>

<span data-ttu-id="94378-114">De volgende informatie heeft betrekking op alle modules, met inbegrip van modules die u maakt voor uw eigen gebruik, de modules die u via andere partijen en de modules die u naar anderen distribueert.</span><span class="sxs-lookup"><span data-stu-id="94378-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="94378-115">Modules installeren in PSModulePath</span><span class="sxs-lookup"><span data-stu-id="94378-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="94378-116">Indien mogelijk alle modules installeren in een pad dat wordt weergegeven in de **PSModulePath** omgevingsvariabele of toevoegen van de modulepad naar de **PSModulePath** omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="94378-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="94378-117">De **PSModulePath** omgevingsvariabele ($Env: PSModulePath) bevat de locaties van Windows PowerShell-modules.</span><span class="sxs-lookup"><span data-stu-id="94378-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="94378-118">Cmdlets zijn afhankelijk van de waarde van deze omgevingsvariabele modules vinden.</span><span class="sxs-lookup"><span data-stu-id="94378-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="94378-119">Standaard de **PSModulePath** omgevingsvariabele bevat de volgende systeem en directory's van gebruiker-module, maar u kunt toevoegen aan en bewerkt u de waarde.</span><span class="sxs-lookup"><span data-stu-id="94378-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="94378-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="94378-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="94378-121">Deze locatie is gereserveerd voor modules die worden geleverd met Windows.</span><span class="sxs-lookup"><span data-stu-id="94378-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="94378-122">Installeer de modules niet naar deze locatie.</span><span class="sxs-lookup"><span data-stu-id="94378-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="94378-123">$Home\Documents\WindowsPowerShell\Modules (% UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="94378-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="94378-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="94378-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="94378-125">Om de waarde van de **PSModulePath** omgevingsvariabele, een van de volgende opdrachten gebruiken.</span><span class="sxs-lookup"><span data-stu-id="94378-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="94378-126">Een modulepad toevoegen aan de waarde van de **PSModulePath** omgevingsvariabele waarde, gebruikt u de volgende opdrachtindeling.</span><span class="sxs-lookup"><span data-stu-id="94378-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="94378-127">Deze indeling maakt gebruik van de **SetEnvironmentVariable** -methode van de **System.Environment** klasse voor het maken van een sessie-onafhankelijke wijziging in de **PSModulePath** omgeving variabele.</span><span class="sxs-lookup"><span data-stu-id="94378-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="94378-128">Nadat u het pad naar hebt toegevoegd **PSModulePath**, moet u een bericht van de omgeving van de wijziging uitzenden.</span><span class="sxs-lookup"><span data-stu-id="94378-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="94378-129">De wijziging Broadcasting, kunt andere toepassingen, zoals de shell om op te halen de wijziging.</span><span class="sxs-lookup"><span data-stu-id="94378-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="94378-130">Als u wilt de wijziging uitzenden, hebt u uw installatie-productcode verzenden een **WM_SETTINGCHANGE** message met `lParam` ingesteld op de tekenreeks 'Omgeving'.</span><span class="sxs-lookup"><span data-stu-id="94378-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="94378-131">Zorg ervoor dat het bericht te verzenden nadat de installatie van module code heeft bijgewerkt **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="94378-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="94378-132">Gebruik de naam van de juiste Module-map</span><span class="sxs-lookup"><span data-stu-id="94378-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="94378-133">Een 'opgemaakte' is een module die is opgeslagen in een map met dezelfde naam als de naam op van ten minste één bestand in de modulemap.</span><span class="sxs-lookup"><span data-stu-id="94378-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="94378-134">Als een module niet grammaticaal correct is, Windows PowerShell niet wordt herkend als een module.</span><span class="sxs-lookup"><span data-stu-id="94378-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="94378-135">De 'algemene naam' van een bestand is de naam zonder de extensie.</span><span class="sxs-lookup"><span data-stu-id="94378-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="94378-136">De naam van de map waarin de bestanden van de module moet overeenkomen met de naam op van ten minste één bestand in de module in een goed ingedeelde module.</span><span class="sxs-lookup"><span data-stu-id="94378-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="94378-137">Bijvoorbeeld de map waarin de bestanden van de module met de naam "Fabrikam" in de Fabrikam voorbeeldmodule en ten minste één bestand heeft de naam van de "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="94378-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="94378-138">Zowel Fabrikam.psd1 en Fabrikam.dll hebben in dit geval de naam van de "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="94378-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="94378-139">Effect van onjuiste installatie</span><span class="sxs-lookup"><span data-stu-id="94378-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="94378-140">Als de module niet grammaticaal correct is en de locatie niet in de waarde van opgenomen is de **PSModulePath** omgevingsvariabele, eenvoudige detectie nieuwe functies van Windows PowerShell, zoals het volgende, werken niet.</span><span class="sxs-lookup"><span data-stu-id="94378-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="94378-141">De functie voor het laden van de Module automatisch kan niet automatisch de module importeren.</span><span class="sxs-lookup"><span data-stu-id="94378-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="94378-142">De `ListAvailable` parameter van de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet kan de module niet vinden.</span><span class="sxs-lookup"><span data-stu-id="94378-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="94378-143">De [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet kan de module niet vinden.</span><span class="sxs-lookup"><span data-stu-id="94378-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="94378-144">Voor het importeren van de module, moet u het volledige pad naar het root-modulebestand of de module-manifest-bestand opgeven.</span><span class="sxs-lookup"><span data-stu-id="94378-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="94378-145">Extra functies, zoals de volgende, werken niet, tenzij de module wordt geïmporteerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="94378-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="94378-146">In opgemaakte modules in de **PSModulePath** omgevingsvariabele, deze functies werken, zelfs wanneer de module is niet geïmporteerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="94378-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="94378-147">De [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet opdrachten in de module kan niet vinden.</span><span class="sxs-lookup"><span data-stu-id="94378-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="94378-148">De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets kan bijwerken of opslaan van de help voor de module.</span><span class="sxs-lookup"><span data-stu-id="94378-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="94378-149">De [opdracht weergeven](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet niet kan vinden en weergeven van de opdrachten in de module.</span><span class="sxs-lookup"><span data-stu-id="94378-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="94378-150">De opdrachten in de module niet aanwezig zijn in de `Show-Command` venster in Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="94378-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="94378-151">WHERE-Modules installeren</span><span class="sxs-lookup"><span data-stu-id="94378-151">Where to Install Modules</span></span>

<span data-ttu-id="94378-152">Deze sectie wordt uitgelegd waar u in het bestandssysteem voor het installeren van Windows PowerShell-modules.</span><span class="sxs-lookup"><span data-stu-id="94378-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="94378-153">De locatie, is afhankelijk van hoe de module wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="94378-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="94378-154">Modules installeren voor een specifieke gebruiker</span><span class="sxs-lookup"><span data-stu-id="94378-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="94378-155">Als u uw eigen module maken of een module ophalen uit een andere partij, zoals de website van een Windows PowerShell-community en u wilt dat de module moet beschikbaar zijn voor uw gebruikersaccount gebruikt, moet u de module installeren in uw directory gebruikersspecifieke-Modules.</span><span class="sxs-lookup"><span data-stu-id="94378-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="94378-156">De gebruiker-specifieke Modules-map wordt toegevoegd aan de waarde van de **PSModulePath** omgevingsvariabele standaard.</span><span class="sxs-lookup"><span data-stu-id="94378-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="94378-157">Modules installeren voor alle gebruikers in Program Files</span><span class="sxs-lookup"><span data-stu-id="94378-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="94378-158">Als u een module beschikbaar voor alle gebruikersaccounts op de computer, installeert u de module op de locatie voor programmabestanden.</span><span class="sxs-lookup"><span data-stu-id="94378-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="94378-159">De locatie voor programmabestanden wordt toegevoegd aan de waarde van de omgevingsvariabele PSModulePath standaard in Windows PowerShell 4.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="94378-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="94378-160">Voor eerdere versies van Windows PowerShell kunt u handmatig de locatie programmabestanden ((%ProgramFiles%\WindowsPowerShell\Modules) maken en dit pad toevoegen aan de omgevingsvariabele PSModulePath zoals hierboven is beschreven.</span><span class="sxs-lookup"><span data-stu-id="94378-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="94378-161">Modules installeren in een Product-Directory</span><span class="sxs-lookup"><span data-stu-id="94378-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="94378-162">Als u de module aan de andere partijen distribueert, gebruikt u de standaardlocatie voor programmabestanden die hierboven worden beschreven of maak uw eigen bedrijf of product-specifieke submap van de map % ProgramFiles %.</span><span class="sxs-lookup"><span data-stu-id="94378-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="94378-163">Fabrikam-technologieën, een fictief bedrijf, levert bijvoorbeeld een Windows PowerShell-module voor hun product Manager voor Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="94378-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="94378-164">De module-installatieprogramma maakt een submap Modules in de submap van de product Manager voor Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="94378-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="94378-165">Het installatieprogramma van de module Fabrikam voegt om in te schakelen van de functies van Windows PowerShell-module detectie te vinden van de module Fabrikam, de locatie van de module toe aan de waarde van de **PSModulePath** omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="94378-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technolgies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="94378-166">Modules installeren in de map voor algemene</span><span class="sxs-lookup"><span data-stu-id="94378-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="94378-167">Als een module wordt gebruikt door meerdere onderdelen van een product of meerdere versies van een product, moet u de module installeren in een module-specifieke submap van de %ProgramFiles%\Common Files\Modules submap.</span><span class="sxs-lookup"><span data-stu-id="94378-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="94378-168">In het volgende voorbeeld wordt is de Fabrikam-module geïnstalleerd in een submap Fabrikam van de %ProgramFiles%\Common Files\Modules submap.</span><span class="sxs-lookup"><span data-stu-id="94378-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="94378-169">Houd er rekening mee dat elke module bevindt zich in een eigen submap in de submap Modules.</span><span class="sxs-lookup"><span data-stu-id="94378-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="94378-170">Vervolgens het installatieprogramma zorgen voor de waarde van de **PSModulePath** omgevingsvariabele bevat het pad van de algemene bestanden modules submap.</span><span class="sxs-lookup"><span data-stu-id="94378-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="94378-171">De installatie van meerdere versies van een Module</span><span class="sxs-lookup"><span data-stu-id="94378-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="94378-172">Gebruik de volgende procedure voor het installeren van meerdere versies van dezelfde module.</span><span class="sxs-lookup"><span data-stu-id="94378-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="94378-173">Maak een map voor elke versie van de module.</span><span class="sxs-lookup"><span data-stu-id="94378-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="94378-174">Neem het versienummer in naam van de map.</span><span class="sxs-lookup"><span data-stu-id="94378-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="94378-175">Maak een module-manifest voor elke versie van de module.</span><span class="sxs-lookup"><span data-stu-id="94378-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="94378-176">In de waarde van de **ModuleVersion** sleutel in het manifest, geef het versienummer van de module.</span><span class="sxs-lookup"><span data-stu-id="94378-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="94378-177">Sla het manifestbestand (.psd1) in de map specifieke versies voor de module.</span><span class="sxs-lookup"><span data-stu-id="94378-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="94378-178">Pad naar de map van de module hoofdmap toevoegen aan de waarde van de **PSModulePath** omgevingsvariabele, zoals wordt weergegeven in de volgende voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="94378-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="94378-179">Als u wilt importeren in een bepaalde versie van de module, de eindgebruiker kan gebruiken de `MinimumVersion` of `RequiredVersion` parameters van de [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94378-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="94378-180">Bijvoorbeeld, als de Fabrikam-module beschikbaar in versie 8.0 en 9.0 is, de mapstructuur van de Fabrikam-module kan lijken op de volgende.</span><span class="sxs-lookup"><span data-stu-id="94378-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="94378-181">Het installatieprogramma voegt beide van de modulepaden naar de **PSModulePath** omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="94378-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="94378-182">Wanneer deze stappen voltooid zijn, de **ListAvailable** parameter van de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -cmdlet krijgt u beide modules voor Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="94378-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="94378-183">Als u wilt importeren in een bepaalde module, gebruikt u de `MiminumVersion` of `RequiredVersion` parameters van de [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94378-183">To import a particular module, use the `MiminumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="94378-184">Als beide modules zijn geïmporteerd in dezelfde sessie en de modules cmdlets met dezelfde namen bevatten, gelden de cmdlets die laatste worden geïmporteerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="94378-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="94378-185">Opdrachtnaamconflicten verwerken</span><span class="sxs-lookup"><span data-stu-id="94378-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="94378-186">Opdrachtnaamconflicten kunnen optreden wanneer de opdrachten die Hiermee exporteert u een module dezelfde naam als de opdrachten in de sessie van de gebruiker hebben.</span><span class="sxs-lookup"><span data-stu-id="94378-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="94378-187">Wanneer een sessie twee opdrachten die dezelfde naam hebben bevat, wordt het opdrachttype voorrang heeft uitgevoerd in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94378-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="94378-188">Wanneer een sessie twee opdrachten met dezelfde naam en hetzelfde type bevat, wordt de opdracht die is toegevoegd aan de sessie meest recent uitgevoerd in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94378-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="94378-189">Voor het uitvoeren van een opdracht die niet standaard wordt uitgevoerd, kunnen gebruikers in aanmerking de naam van de opdracht met de naam van de module.</span><span class="sxs-lookup"><span data-stu-id="94378-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="94378-190">Bijvoorbeeld, als de sessie bevat een `Get-Date` functie en de `Get-Date` Windows PowerShell-cmdlet voert u de functie standaard.</span><span class="sxs-lookup"><span data-stu-id="94378-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="94378-191">Voor het uitvoeren van de cmdlet, geeft u de opdracht met de naam van de module, zoals:</span><span class="sxs-lookup"><span data-stu-id="94378-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="94378-192">Gebruik ter voorkoming van naamconflicten auteurs kunnen de **DefaultCommandPrefix** sleutel in de module-manifest om op te geven van een zelfstandig naamwoord voorvoegsel voor alle opdrachten die zijn geëxporteerd uit de module.</span><span class="sxs-lookup"><span data-stu-id="94378-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="94378-193">Gebruikers kunnen gebruiken de **voorvoegsel** parameter van de `Import-Module` cmdlet naar een alternatieve voorvoegsel gebruiken.</span><span class="sxs-lookup"><span data-stu-id="94378-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="94378-194">De waarde van de **voorvoegsel** parameter voorrang boven de waarde van de **DefaultCommandPrefix** sleutel.</span><span class="sxs-lookup"><span data-stu-id="94378-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="94378-195">Zie ook</span><span class="sxs-lookup"><span data-stu-id="94378-195">See Also</span></span>

[<span data-ttu-id="94378-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="94378-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="94378-197">Een Windows PowerShell-Module schrijven</span><span class="sxs-lookup"><span data-stu-id="94378-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)