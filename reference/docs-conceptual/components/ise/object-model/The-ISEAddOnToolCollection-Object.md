---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEAddOnToolCollection-object
ms.openlocfilehash: 28ab9747e573b7a76ee655289b341870b1728bc2
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030620"
---
# <a name="the-iseaddontoolcollection-object"></a>Het ISEAddOnToolCollection-object

De **ISEAddOnToolCollection** object is een verzameling van **ISEAddOnTool** objecten. Een voorbeeld is de **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.

## <a name="methods"></a>Methoden

### <a name="add-name-controltype-isvisible-"></a>Voeg\( naam, het besturingselementtype, \[IsVisible\] \)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Voegt een nieuw hulpprogramma voor de invoegtoepassing toe aan de verzameling. Retourneert het zojuist toegevoegde invoegtoepassing-hulpprogramma. Voordat u deze opdracht uitvoert, moet u het hulpprogramma invoegtoepassing installeren op de lokale computer en de assembly niet laden.

**Naam** -tekenreeks geeft de weergavenaam van het hulpprogramma invoegtoepassing die wordt toegevoegd aan Windows PowerShell ISE.

**Besturingselementtype** -Type wordt opgegeven in het besturingselement dat wordt toegevoegd.

**\[IsVisible\]**  -optionele Booleaanse als ingesteld op **$true**, het hulpprogramma invoegtoepassing is meteen zichtbaar in het deelvenster van de bijbehorende hulpprogramma.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Verwijder\( Item \)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee verwijdert u het hulpprogramma opgegeven invoegtoepassing uit de verzameling.

**Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Hiermee geeft u het object worden verwijderd uit de Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Selecteert het PowerShell-tabblad die de **psTab** parameter specificeert.

**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab de PowerShell-tabblad om te selecteren.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Verwijder\( psTab \)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee verwijdert u de PowerShell-tabblad die de **psTab** parameter specificeert.

**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab de PowerShell-tabblad om te verwijderen.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Zie ook

- [The PowerShellTab Object](The-PowerShellTab-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
