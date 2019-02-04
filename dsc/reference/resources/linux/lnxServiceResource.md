---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxService-Resource
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684246"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="c16c3-103">DSC voor Linux nxService-Resource</span><span class="sxs-lookup"><span data-stu-id="c16c3-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="c16c3-104">De **nxService** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van services op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="c16c3-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c16c3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c16c3-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="c16c3-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c16c3-106">Properties</span></span>

| <span data-ttu-id="c16c3-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="c16c3-107">Property</span></span> | <span data-ttu-id="c16c3-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c16c3-108">Description</span></span> |
|---|---|
| <span data-ttu-id="c16c3-109">Naam</span><span class="sxs-lookup"><span data-stu-id="c16c3-109">Name</span></span>| <span data-ttu-id="c16c3-110">De naam van de service/daemon te configureren.</span><span class="sxs-lookup"><span data-stu-id="c16c3-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="c16c3-111">Controller</span><span class="sxs-lookup"><span data-stu-id="c16c3-111">Controller</span></span>| <span data-ttu-id="c16c3-112">Het type servicecontroller te gebruiken bij het configureren van de service.</span><span class="sxs-lookup"><span data-stu-id="c16c3-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="c16c3-113">Ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="c16c3-113">Enabled</span></span>| <span data-ttu-id="c16c3-114">Geeft aan of de service wordt gestart bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="c16c3-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="c16c3-115">Status</span><span class="sxs-lookup"><span data-stu-id="c16c3-115">State</span></span>| <span data-ttu-id="c16c3-116">Geeft aan of de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c16c3-116">Indicates whether the service is running.</span></span> <span data-ttu-id="c16c3-117">Deze eigenschap instellen op 'Stopped' om ervoor te zorgen dat de service niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c16c3-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="c16c3-118">Stel deze in op "Uitvoeren" om ervoor te zorgen dat de service niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c16c3-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="c16c3-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c16c3-119">DependsOn</span></span> | <span data-ttu-id="c16c3-120">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="c16c3-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c16c3-121">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c16c3-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="c16c3-122">Als u meer informatie</span><span class="sxs-lookup"><span data-stu-id="c16c3-122">Additional Information</span></span>

<span data-ttu-id="c16c3-123">De **nxService** resource niet maakt u een servicedefinitie of het script voor de service als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="c16c3-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="c16c3-124">U kunt de PowerShell Desired State Configuration **nxFile** Resource resource voor het beheren van de aanwezigheid of de inhoud van het servicedefinitiebestand of script.</span><span class="sxs-lookup"><span data-stu-id="c16c3-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="c16c3-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c16c3-125">Example</span></span>

<span data-ttu-id="c16c3-126">Het volgende voorbeeld ziet u configuratie van de service 'httpd' (voor Apache HTTP Server), geregistreerd bij de **SystemD** servicecontroller.</span><span class="sxs-lookup"><span data-stu-id="c16c3-126">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```