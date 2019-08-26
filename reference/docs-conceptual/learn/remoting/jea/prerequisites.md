---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: Vereisten voor JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017935"
---
# <a name="prerequisites"></a><span data-ttu-id="a3d5a-103">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a3d5a-103">Prerequisites</span></span>

<span data-ttu-id="a3d5a-104">Net genoeg beheer is een functie die is opgenomen in Power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="a3d5a-105">In dit artikel worden de vereisten beschreven waaraan moet worden voldaan om JEA te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="a3d5a-106">Controleren welke versie van Power shell is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="a3d5a-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="a3d5a-107">Als u wilt controleren welke versie van Power shell op uw systeem is geïnstalleerd `$PSVersionTable` , controleert u de variabele in een Windows Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="a3d5a-108">JEA is beschikbaar met Power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="a3d5a-109">Voor volledige functionaliteit is het raadzaam om de meest recente versie van Power shell te installeren die beschikbaar is voor uw systeem.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="a3d5a-110">In de volgende tabel wordt de beschik baarheid van JEA op Windows Server beschreven:</span><span class="sxs-lookup"><span data-stu-id="a3d5a-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="a3d5a-111">Server-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="a3d5a-111">Server Operating System</span></span> |                <span data-ttu-id="a3d5a-112">JEA-Beschik baarheid</span><span class="sxs-lookup"><span data-stu-id="a3d5a-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="a3d5a-113">Windows Server 2016 +</span><span class="sxs-lookup"><span data-stu-id="a3d5a-113">Windows Server 2016+</span></span>    | <span data-ttu-id="a3d5a-114">Vooraf geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="a3d5a-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="a3d5a-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a3d5a-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="a3d5a-116">Volledige functionaliteit met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="a3d5a-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="a3d5a-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a3d5a-117">Windows Server 2012</span></span>     | <span data-ttu-id="a3d5a-118">Volledige functionaliteit met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="a3d5a-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="a3d5a-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a3d5a-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="a3d5a-120">Verminderde functionaliteit<sup>1</sup> met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="a3d5a-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="a3d5a-121">U kunt JEA ook gebruiken op uw computer thuis of op het werk:</span><span class="sxs-lookup"><span data-stu-id="a3d5a-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="a3d5a-122">Besturings systeem van client</span><span class="sxs-lookup"><span data-stu-id="a3d5a-122">Client Operating System</span></span> |                   <span data-ttu-id="a3d5a-123">JEA-Beschik baarheid</span><span class="sxs-lookup"><span data-stu-id="a3d5a-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="a3d5a-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="a3d5a-124">Windows 10 1607+</span></span>        | <span data-ttu-id="a3d5a-125">Vooraf geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="a3d5a-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="a3d5a-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="a3d5a-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="a3d5a-127">Vooraf geïnstalleerd, met beperkte functionaliteit<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="a3d5a-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="a3d5a-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="a3d5a-128">Windows 10 1507</span></span>         | <span data-ttu-id="a3d5a-129">Niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="a3d5a-129">Not available</span></span>                                        |
| <span data-ttu-id="a3d5a-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="a3d5a-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="a3d5a-131">Volledige functionaliteit met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="a3d5a-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="a3d5a-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="a3d5a-132">Windows 7</span></span>               | <span data-ttu-id="a3d5a-133">Verminderde functionaliteit<sup>1</sup> met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="a3d5a-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="a3d5a-134"><sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van door groepen beheerde service accounts in windows server 2008 R2 of Windows 7.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="a3d5a-135">Virtuele accounts en andere JEA-functies *worden* ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="a3d5a-136"><sup>2</sup> de volgende JEA-functies worden niet ondersteund in Windows 10 versie 1511 en 1603:</span><span class="sxs-lookup"><span data-stu-id="a3d5a-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="a3d5a-137">Uitvoeren als een door een groep beheerd service account</span><span class="sxs-lookup"><span data-stu-id="a3d5a-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="a3d5a-138">Regels voor voorwaardelijke toegang in sessie configuraties</span><span class="sxs-lookup"><span data-stu-id="a3d5a-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="a3d5a-139">Het gebruikers station</span><span class="sxs-lookup"><span data-stu-id="a3d5a-139">The user drive</span></span>
  - <span data-ttu-id="a3d5a-140">Toegang verlenen tot lokale gebruikers accounts</span><span class="sxs-lookup"><span data-stu-id="a3d5a-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="a3d5a-141">Als u ondersteuning voor deze functies wilt, werkt u Windows bij naar versie 1607 (jubileum update) of hoger.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="a3d5a-142">Windows Management Framework installeren</span><span class="sxs-lookup"><span data-stu-id="a3d5a-142">Install Windows Management Framework</span></span>

<span data-ttu-id="a3d5a-143">Als u een oudere versie van Power shell gebruikt, moet u mogelijk uw systeem bijwerken met de meest recente Windows Management Framework (WMF)-update.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="a3d5a-144">Raadpleeg de [WMF-documentatie](/powershell/wmf/overview)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="a3d5a-145">Het is raadzaam om de compatibiliteit van uw werk belasting met WMF te testen voordat u de upgrade van alle servers uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="a3d5a-146">Windows 10-gebruikers moeten de nieuwste functie-updates installeren om de huidige versie van Windows Power shell te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="a3d5a-147">Externe communicatie met Power shell inschakelen</span><span class="sxs-lookup"><span data-stu-id="a3d5a-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="a3d5a-148">Externe communicatie met Power shell biedt de basis waarop JEA is gebouwd.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="a3d5a-149">Het is nood zakelijk om ervoor te zorgen dat externe communicatie van Power shell is ingeschakeld en goed wordt beveiligd voordat u JEA kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="a3d5a-150">Zie [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="a3d5a-151">Externe communicatie van Power shell is standaard ingeschakeld op Windows Server 2012, 2012 R2 en 2016.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="a3d5a-152">U kunt externe communicatie van Power shell inschakelen door de volgende opdracht uit te voeren in een Power shell-venster met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="a3d5a-153">Power shell-module en logboek registratie van script blokken inschakelen (optioneel)</span><span class="sxs-lookup"><span data-stu-id="a3d5a-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="a3d5a-154">Met de volgende stappen kunt u logboek registratie inschakelen voor alle Power shell-acties op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="a3d5a-155">Logboek registratie van de Power shell-module is niet vereist voor JEA, maar het is raadzaam om logboek registratie in te scha kelen om ervoor te zorgen dat de opdrachten die gebruikers uitvoeren, worden geregistreerd op een centrale locatie.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="a3d5a-156">U kunt het beleid voor logboek registratie van Power shell-modules configureren met behulp van groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="a3d5a-157">Open de Lokale groepsbeleidsobjecteditor op een werk station of een groepsbeleid-object in de console Groepsbeleidbeheer op een Active Directory-domein controller</span><span class="sxs-lookup"><span data-stu-id="a3d5a-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="a3d5a-158">Navigeren naar **computer configuratie\\Beheersjablonen\\Windows-\\onderdelen Windows Power shell**</span><span class="sxs-lookup"><span data-stu-id="a3d5a-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="a3d5a-159">Dubbel klik op **inschakelen logboek registratie** van de module</span><span class="sxs-lookup"><span data-stu-id="a3d5a-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="a3d5a-160">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="a3d5a-160">Click **Enabled**</span></span>
5. <span data-ttu-id="a3d5a-161">Klik in de sectie opties op **weer geven** naast module namen</span><span class="sxs-lookup"><span data-stu-id="a3d5a-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="a3d5a-162">Typ `*` in het pop-upvenster om opdrachten van alle modules te registreren.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="a3d5a-163">Klik op **OK** om het beleid in te stellen</span><span class="sxs-lookup"><span data-stu-id="a3d5a-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="a3d5a-164">Dubbel klik op **inschakelen logboek registratie van Power shell-script blokken**</span><span class="sxs-lookup"><span data-stu-id="a3d5a-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="a3d5a-165">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="a3d5a-165">Click **Enabled**</span></span>
10. <span data-ttu-id="a3d5a-166">Klik op **OK** om het beleid in te stellen</span><span class="sxs-lookup"><span data-stu-id="a3d5a-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="a3d5a-167">(Alleen op computers die lid zijn van een domein) Uitvoeren `gpupdate` of wachten tot Groepsbeleid het bijgewerkte beleid verwerkt en de instellingen toepast</span><span class="sxs-lookup"><span data-stu-id="a3d5a-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="a3d5a-168">U kunt ook de systeembrede Power shell-transcriptie inschakelen via groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="a3d5a-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a3d5a-169">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="a3d5a-169">Next steps</span></span>

[<span data-ttu-id="a3d5a-170">Een functie-mogelijkheidsprofiel maken</span><span class="sxs-lookup"><span data-stu-id="a3d5a-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="a3d5a-171">Een configuratie bestand voor de sessie maken</span><span class="sxs-lookup"><span data-stu-id="a3d5a-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="a3d5a-172">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a3d5a-172">See also</span></span>

[<span data-ttu-id="a3d5a-173">WinRM-beveiliging</span><span class="sxs-lookup"><span data-stu-id="a3d5a-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="a3d5a-174">Power shell ♥ het blauwe team</span><span class="sxs-lookup"><span data-stu-id="a3d5a-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)