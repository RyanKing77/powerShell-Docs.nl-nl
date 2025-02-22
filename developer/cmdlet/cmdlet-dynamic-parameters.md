---
title: Cmdlet dynamische para meters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986243"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet dynamische para meters

Met cmdlets kunt u para meters definiëren die beschikbaar zijn voor de gebruiker onder speciale omstandigheden, zoals wanneer het argument van een andere para meter een specifieke waarde is. Deze para meters worden toegevoegd tijdens runtime en worden aangeduid als dynamische para meters, omdat ze alleen worden toegevoegd wanneer dit nodig is. U kunt bijvoorbeeld een cmdlet ontwerpen waarmee meerdere para meters worden toegevoegd wanneer een specifieke switch parameter wordt opgegeven.

> [!NOTE]
> Providers en Power shell-functies kunnen ook dynamische para meters definiëren.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>Dynamische para meters in Power shell-cmdlets

Power shell gebruikt dynamische para meters in verschillende provider-cmdlets. De `Get-Item` `Get-ChildItem` cmdlets en voegen bijvoorbeeld tijdens runtime een **CodeSigningCert** -para meter toe wanneer de para meter **Path** het pad naar de **certificaat** provider specificeert. Als met de para meter **Path** een pad voor een andere provider wordt opgegeven, is de para meter **CodeSigningCert** niet beschikbaar.

In de volgende voor beelden ziet u hoe de para meter **CodeSigningCert** wordt `Get-Item` toegevoegd tijdens runtime wanneer wordt uitgevoerd.

In dit voor beeld heeft de Power shell-runtime de para meter toegevoegd en is de cmdlet geslaagd.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

In dit voor beeld wordt een bestandssysteem station opgegeven en wordt er een fout geretourneerd. Het fout bericht geeft aan dat de para meter **CodeSigningCert** niet kan worden gevonden.

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Ondersteuning voor dynamische para meters

Voor het ondersteunen van dynamische para meters moeten de volgende elementen worden opgenomen in de cmdlet-code.

### <a name="interface"></a>Interface

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).
Deze interface biedt de methode waarmee de dynamische para meters worden opgehaald.

Bijvoorbeeld:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>Methode

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).
Deze methode haalt het object op dat de dynamische parameter definities bevat.

Bijvoorbeeld:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a>Klasse

Een klasse die de dynamische para meters definieert die moeten worden toegevoegd. Deze klasse moet een **parameter** kenmerk voor elke para meter en eventuele optionele **alias** -en **validatie** kenmerken bevatten die nodig zijn voor de cmdlet.

Bijvoorbeeld:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Zie [dynamische para meters declareren](./how-to-declare-dynamic-parameters.md)voor een volledig voor beeld van een cmdlet die dynamische para meters ondersteunt.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Dynamische para meters declareren](./how-to-declare-dynamic-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
