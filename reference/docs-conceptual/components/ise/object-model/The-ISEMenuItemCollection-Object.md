---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEMenuItemCollection-object
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030537"
---
# <a name="the-isemenuitemcollection-object"></a>Het ISEMenuItemCollection-object

Een **ISEMenuItemCollection** object is een verzameling van **ISEMenuItem** objecten. Het is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Een voorbeeld is de **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object dat wordt gebruikt om aan te passen de **invoegtoepassing** menu in Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Methode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Voeg\(DisplayName, System.Management.Automation.ScriptBlock actie System.Windows.Input.KeyGesture snelkoppeling tekenreeks \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Voegt een menu-item toe aan de verzameling.

**DisplayName** de weergavenaam van het menu om te worden toegevoegd.

**Actie** de **System.Management.Automation.ScriptBlock** -object dat Hiermee geeft u de actie die is gekoppeld aan dit menu-item.

**Snelkoppeling** de sneltoets voor de actie.

**Retourneert** het ISEMenuItem-object dat zojuist is toegevoegd.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Wissen\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee verwijdert u alle submenu's uit het menu-item.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Zie ook

- [Het ISEMenuItem-Object](The-ISEMenuItem-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
