---
title: Lijstweergave (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065288"
---
# <a name="list-view-groupby"></a><span data-ttu-id="dd628-102">Lijstweergave (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="dd628-102">List View (GroupBy)</span></span>

<span data-ttu-id="dd628-103">In dit voorbeeld laat zien hoe voor het implementeren van een lijst weergeven die worden gescheiden van de rijen van de lijst in groepen.</span><span class="sxs-lookup"><span data-stu-id="dd628-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="dd628-104">In deze lijstweergave geeft de eigenschappen van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd628-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="dd628-105">Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dd628-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="dd628-106">Deze opmaak bestand laden</span><span class="sxs-lookup"><span data-stu-id="dd628-106">To load this formatting file</span></span>

1. <span data-ttu-id="dd628-107">Kopieer het XML-bestand van de voorbeeld-sectie van dit onderwerp in een tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="dd628-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="dd628-108">Bewaar het tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="dd628-108">Save the text file.</span></span> <span data-ttu-id="dd628-109">Zorg ervoor dat om toe te voegen de `format.ps1xml` uitbreiding van het bestand om het te identificeren als een opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="dd628-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="dd628-110">Open Windows PowerShell en voer de volgende opdracht om de opmaak bestand laden in de huidige sessie: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="dd628-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="dd628-111">Deze opmaak bestand definieert de weergave van een object dat al is gedefinieerd door een bestand van Windows PowerShell-opmaak.</span><span class="sxs-lookup"><span data-stu-id="dd628-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="dd628-112">Moet u de `prependPath` parameter wanneer u de cmdlet uitvoert, en deze opmaak kan niet worden geladen als een module-bestand.</span><span class="sxs-lookup"><span data-stu-id="dd628-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="dd628-113">Ziet u</span><span class="sxs-lookup"><span data-stu-id="dd628-113">Demonstrates</span></span>

<span data-ttu-id="dd628-114">Deze opmaak bestand ziet u de volgende XML-elementen:</span><span class="sxs-lookup"><span data-stu-id="dd628-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="dd628-115">De [naam](./name-element-for-view-format.md) -element voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="dd628-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="dd628-116">De [ViewSelectedBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd welke objecten worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="dd628-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="dd628-117">De [GroupBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="dd628-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="dd628-118">De [ListControl](./listcontrol-element-format.md) element waarmee wordt gedefinieerd welke eigenschap van de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="dd628-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="dd628-119">De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element die definieert wat wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="dd628-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="dd628-120">De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="dd628-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="dd628-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="dd628-121">Example</span></span>

<span data-ttu-id="dd628-122">Het volgende XML-bestand definieert een lijstweergave met een nieuwe start groep wanneer de waarde van de [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) wijzigingen in de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="dd628-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="dd628-123">Wanneer elke groep wordt gestart, wordt een aangepast label met de nieuwe waarde van de eigenschap weergegeven.</span><span class="sxs-lookup"><span data-stu-id="dd628-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
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
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="dd628-124">Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling.</span><span class="sxs-lookup"><span data-stu-id="dd628-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="dd628-125">De lege regels voor en na het Groepslabel toegevoegd worden automatisch toegevoegd door Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd628-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="dd628-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dd628-126">See Also</span></span>

[<span data-ttu-id="dd628-127">Voorbeelden van opmaak bestanden</span><span class="sxs-lookup"><span data-stu-id="dd628-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="dd628-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd628-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
