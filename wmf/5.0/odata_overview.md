---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057805"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="6081f-102">PowerShell-cmdlets genereren op basis van OData-eindpunt</span><span class="sxs-lookup"><span data-stu-id="6081f-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="6081f-103">Windows PowerShell-cmdlets op basis van een OData-eindpunt genereren</span><span class="sxs-lookup"><span data-stu-id="6081f-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>

<span data-ttu-id="6081f-104">**Exporteren-ODataEndpointProxy** is een cmdlet die een set van Windows PowerShell-cmdlets op basis van de functionaliteit die door een opgegeven OData-eindpunt genereert.</span><span class="sxs-lookup"><span data-stu-id="6081f-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="6081f-105">Het volgende voorbeeld laat zien hoe het gebruik van deze nieuwe cmdlet:</span><span class="sxs-lookup"><span data-stu-id="6081f-105">The following example shows how to use this new cmdlet:</span></span>

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

<span data-ttu-id="6081f-106">Er zijn nog steeds delen met belangrijke use cases in de ontwikkeling van deze functionaliteit wilt gebruiken, met inbegrip van, maar niet beperkt tot:</span><span class="sxs-lookup"><span data-stu-id="6081f-106">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="6081f-107">Koppelingen</span><span class="sxs-lookup"><span data-stu-id="6081f-107">Associations</span></span>
-   <span data-ttu-id="6081f-108">Doorgeven van stromen</span><span class="sxs-lookup"><span data-stu-id="6081f-108">Passing streams</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="6081f-109">Windows PowerShell-cmdlets op basis van een OData-eindpunt met ODataUtils genereren</span><span class="sxs-lookup"><span data-stu-id="6081f-109">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="6081f-110">De module ODataUtils kunt genereren van Windows PowerShell-cmdlets van REST-eindpunten die ondersteuning bieden voor OData.</span><span class="sxs-lookup"><span data-stu-id="6081f-110">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="6081f-111">De volgende incrementele verbeteringen zijn in de Microsoft.PowerShell.ODataUtils Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="6081f-111">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="6081f-112">Aanvullende informatie van server-side-eindpunt voor client-side-Channel.</span><span class="sxs-lookup"><span data-stu-id="6081f-112">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="6081f-113">Client-side-ondersteuning voor paginering</span><span class="sxs-lookup"><span data-stu-id="6081f-113">Client-side paging support</span></span>
-   <span data-ttu-id="6081f-114">Serverzijde filteren met behulp van de - Select-parameters</span><span class="sxs-lookup"><span data-stu-id="6081f-114">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="6081f-115">Ondersteuning voor web-aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="6081f-115">Support for web request headers</span></span>

<span data-ttu-id="6081f-116">De proxy-cmdlets die worden gegenereerd door de cmdlet Export-ODataEndPointProxy bevatten aanvullende informatie (niet in de $metadata gebruikt tijdens het genereren van de client-side-proxy genoemd) van de server side OData-eindpunt op de gegevensstroom (een nieuwe Windows PowerShell 5.0-functie).</span><span class="sxs-lookup"><span data-stu-id="6081f-116">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="6081f-117">Hier volgt een voorbeeld van hoe u die informatie.</span><span class="sxs-lookup"><span data-stu-id="6081f-117">Here is an example of how to get that information.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

<span data-ttu-id="6081f-118">De records krijgt u vanaf de server in batches met behulp van de client-side-ondersteuning voor paginering.</span><span class="sxs-lookup"><span data-stu-id="6081f-118">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="6081f-119">Dit is handig als u een grote hoeveelheid gegevens uit de server via het netwerk ophalen moet.</span><span class="sxs-lookup"><span data-stu-id="6081f-119">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

<span data-ttu-id="6081f-120">De gegenereerde proxy-cmdlets bieden ondersteuning voor de Select-parameters die u als een filter gebruiken kunt voor het ontvangen van de recordeigenschappen die de client nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="6081f-120">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="6081f-121">Dit vermindert de hoeveelheid gegevens die worden overgedragen via het netwerk, omdat het filteren op de server wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6081f-121">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="6081f-122">De cmdlet Export-ODataEndpointProxy en de webtoepassingsproxy-cmdlets die worden gegenereerd door, bieden nu ondersteuning voor de parameter Headers (supply waarden als een hash-tabel), die u gebruiken kunt voor aanvullende informatie die wordt verwacht door het OData-eindpunt voor server-side-channel.</span><span class="sxs-lookup"><span data-stu-id="6081f-122">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="6081f-123">In het volgende voorbeeld, kunt u een abonnementssleutel via Headers voor services die een abonnementssleutel voor verificatie verwacht kanaal.</span><span class="sxs-lookup"><span data-stu-id="6081f-123">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
