---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Schrijven van een single instance DSC-resource (aanbevolen)
ms.openlocfilehash: 4510bec5b4600334b845831ec6700da01e1a110c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="491f4-103">Schrijven van een single instance DSC-resource (aanbevolen)</span><span class="sxs-lookup"><span data-stu-id="491f4-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="491f4-104">**Opmerking:** in dit onderwerp beschrijft aanbevolen procedure voor het definiëren van een DSC-resource waarmee slechts één exemplaar in een configuratie.</span><span class="sxs-lookup"><span data-stu-id="491f4-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="491f4-105">Er is momenteel geen ingebouwde DSC-functie om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="491f4-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="491f4-106">Dat kan worden gewijzigd in de toekomst.</span><span class="sxs-lookup"><span data-stu-id="491f4-106">That might change in the future.</span></span>

<span data-ttu-id="491f4-107">Zijn er situaties waarin u niet wilt toestaan dat een resource toe aan meerdere keren worden gebruikt in een configuratie.</span><span class="sxs-lookup"><span data-stu-id="491f4-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="491f4-108">Bijvoorbeeld in een eerdere implementatie van de [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, een configuratie kan aanroepen de resource meerdere keren als u de tijdzone op een andere instelling in elk blok resource:</span><span class="sxs-lookup"><span data-stu-id="491f4-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone 
{ 
    Param 
    ( 
        [String[]]$NodeName = $env:COMPUTERNAME 

    ) 

    Import-DSCResource -ModuleName xTimeZone 
 
 
    Node $NodeName 
    { 
         xTimeZone TimeZoneExample 
         { 
        
            TimeZone = 'Eastern Standard Time' 
         } 

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }        

    } 
} 
```

<span data-ttu-id="491f4-109">Dit is vanwege de manier waarop DSC-resource sleutels werkt.</span><span class="sxs-lookup"><span data-stu-id="491f4-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="491f4-110">Een bron moet ten minste één sleuteleigenschap hebben.</span><span class="sxs-lookup"><span data-stu-id="491f4-110">A resource must have at least one key property.</span></span> <span data-ttu-id="491f4-111">Een resource-instantie wordt beschouwd als uniek zijn als de combinatie van de waarden van alle van de sleuteleigenschappen uniek is.</span><span class="sxs-lookup"><span data-stu-id="491f4-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="491f4-112">In de vorige implementatie de [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had u slechts één eigenschap--**tijdzone**, wat een sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="491f4-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="491f4-113">Als gevolg hiervan, zou een configuratie zoals hierboven compileren en uitvoeren zonder waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="491f4-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="491f4-114">Elk van de **xTimeZone** resource blokken wordt beschouwd als uniek.</span><span class="sxs-lookup"><span data-stu-id="491f4-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="491f4-115">Hierdoor zou de configuratie van meerdere malen worden toegepast op het knooppunt, functioneert de tijdzone heen en weer.</span><span class="sxs-lookup"><span data-stu-id="491f4-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="491f4-116">Om ervoor te zorgen dat een configuratie kan de tijdzone instellen voor een doelknooppunt slechts een keer de resource is bijgewerkt voor het toevoegen van een tweede eigenschap **IsSingleInstance**, die de sleuteleigenschap is geworden.</span><span class="sxs-lookup"><span data-stu-id="491f4-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span> <span data-ttu-id="491f4-117">De **IsSingleInstance** is beperkt tot een enkele waarde 'Ja' met behulp van een **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="491f4-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="491f4-118">Het oude MOF-schema voor de resource is:</span><span class="sxs-lookup"><span data-stu-id="491f4-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="491f4-119">Het bijgewerkte MOF-schema voor de resource is:</span><span class="sxs-lookup"><span data-stu-id="491f4-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="491f4-120">De resource-script is ook bijgewerkt voor het gebruik van de nieuwe parameter.</span><span class="sxs-lookup"><span data-stu-id="491f4-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="491f4-121">Dit is de oude resource-script:</span><span class="sxs-lookup"><span data-stu-id="491f4-121">Here is the old resource script:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}


function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )
    
    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone
    
    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
            else
            {
                Write-Verbose -Verbose "TimeZone already set to $TimeZone"
            }
        }
        catch
        {
            $ErrorMsg = $_.Exception.Message
            Write-Verbose -Verbose $ErrorMsg
        }
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance, 

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="491f4-122">U ziet dat de **tijdzone** eigenschap is niet langer een sleutel.</span><span class="sxs-lookup"><span data-stu-id="491f4-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="491f4-123">Nu als een configuratie probeert in te stellen de tijdzone tweemaal (met behulp van twee verschillende **xTimeZone** blokken met verschillende **tijdzone** waarden), een fout opgetreden bij het compileren van de configuratie wordt:</span><span class="sxs-lookup"><span data-stu-id="491f4-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and 
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the 
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property 
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
   
