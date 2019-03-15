---
title: Lijstweergave (basis) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794158"
---
# <a name="list-view-basic"></a><span data-ttu-id="1e6e5-102">Lijstweergave (Basis)</span><span class="sxs-lookup"><span data-stu-id="1e6e5-102">List View (Basic)</span></span>

<span data-ttu-id="1e6e5-103">In dit voorbeeld laat zien hoe voor het implementeren van een eenvoudige lijstweergave waarop de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="1e6e5-104">Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1e6e5-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="1e6e5-105">Deze opmaak bestand laden</span><span class="sxs-lookup"><span data-stu-id="1e6e5-105">To load this formatting file</span></span>

1. <span data-ttu-id="1e6e5-106">Kopieer het XML-bestand van de voorbeeld-sectie van dit onderwerp in een tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="1e6e5-107">Bewaar het tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-107">Save the text file.</span></span> <span data-ttu-id="1e6e5-108">Zorg ervoor dat om toe te voegen de `format.ps1xml` uitbreiding van het bestand om het te identificeren als een opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="1e6e5-109">Open Windows PowerShell en voer de volgende opdracht om de opmaak bestand laden in de huidige sessie: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="1e6e5-110">Deze opmaak bestand definieert de weergave van een object dat al is gedefinieerd door een bestand van Windows PowerShell-opmaak.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="1e6e5-111">Moet u de `prependPath` parameter wanneer u de cmdlet uitvoert, en deze opmaak kan niet worden geladen als een module-bestand.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1e6e5-112">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="1e6e5-112">Demonstrates</span></span>

<span data-ttu-id="1e6e5-113">Deze opmaak bestand ziet u de volgende XML-elementen:</span><span class="sxs-lookup"><span data-stu-id="1e6e5-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="1e6e5-114">De [naam](./name-element-for-view-format.md) -element voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="1e6e5-115">De [ViewSelectedBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd welke objecten worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="1e6e5-116">De [ListControl](./listcontrol-element-format.md) element waarmee wordt gedefinieerd welke eigenschap van de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="1e6e5-117">De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element die definieert wat wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="1e6e5-118">De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="1e6e5-119">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1e6e5-119">Example</span></span>

<span data-ttu-id="1e6e5-120">Het volgende XML-bestand definieert een lijst weergeven met vier eigenschappen van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="1e6e5-121">In elke rij, wordt de naam van de eigenschap weergegeven, gevolgd door de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <View>
    <Name>System.ServiceProcess.ServiceController</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <ListControl>
      <ListEntries>
        <ListEntry>
          <ListItems>
            <ListItem>
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="1e6e5-122">Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling.</span><span class="sxs-lookup"><span data-stu-id="1e6e5-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="1e6e5-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1e6e5-123">See Also</span></span>

[<span data-ttu-id="1e6e5-124">Voorbeelden van opmaak bestanden</span><span class="sxs-lookup"><span data-stu-id="1e6e5-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="1e6e5-125">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e6e5-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)