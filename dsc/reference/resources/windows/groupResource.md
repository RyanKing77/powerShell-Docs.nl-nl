---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Groep van de DSC-Resource
ms.openlocfilehash: 9894150f6f749fc23efd4ce2b155b18788557d1d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048250"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="bacf5-103">Groep van de DSC-Resource</span><span class="sxs-lookup"><span data-stu-id="bacf5-103">DSC Group Resource</span></span>

> <span data-ttu-id="bacf5-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bacf5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bacf5-105">De bron van gebruikersgroep in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="bacf5-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="bacf5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bacf5-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="bacf5-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="bacf5-107">Properties</span></span>

|  <span data-ttu-id="bacf5-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="bacf5-108">Property</span></span>  |  <span data-ttu-id="bacf5-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bacf5-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="bacf5-110">Groepsnaam</span><span class="sxs-lookup"><span data-stu-id="bacf5-110">GroupName</span></span>| <span data-ttu-id="bacf5-111">De naam van de groep waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="bacf5-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="bacf5-112">Referentie</span><span class="sxs-lookup"><span data-stu-id="bacf5-112">Credential</span></span>| <span data-ttu-id="bacf5-113">De referenties die zijn vereist voor toegang tot externe bronnen.</span><span class="sxs-lookup"><span data-stu-id="bacf5-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="bacf5-114">**Houd er rekening mee**: Dit account moet hebben tot de juiste Active Directory-machtigingen voor alle niet-lokale accounts toevoegen aan de groep. anders treedt een fout op wanneer de configuratie wordt uitgevoerd op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="bacf5-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="bacf5-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bacf5-115">Description</span></span>| <span data-ttu-id="bacf5-116">De beschrijving van de groep.</span><span class="sxs-lookup"><span data-stu-id="bacf5-116">The description of the group.</span></span>|
| <span data-ttu-id="bacf5-117">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="bacf5-117">Ensure</span></span>| <span data-ttu-id="bacf5-118">Geeft aan of de groep bestaat.</span><span class="sxs-lookup"><span data-stu-id="bacf5-118">Indicates if the group exists.</span></span> <span data-ttu-id="bacf5-119">Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat de groep niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="bacf5-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="bacf5-120">Instellen om "" (de standaardwaarde), zorgt u ervoor dat de groep bestaat.</span><span class="sxs-lookup"><span data-stu-id="bacf5-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="bacf5-121">Leden</span><span class="sxs-lookup"><span data-stu-id="bacf5-121">Members</span></span>| <span data-ttu-id="bacf5-122">Gebruik deze eigenschap om het lidmaatschap van de huidige vervangen door de opgegeven leden.</span><span class="sxs-lookup"><span data-stu-id="bacf5-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="bacf5-123">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="bacf5-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bacf5-124">Als u deze eigenschap in een configuratie hebt ingesteld, mag niet een gebruiken de **MembersToExclude** of **MembersToInclude** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="bacf5-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="bacf5-125">In dat geval wordt een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bacf5-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="bacf5-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="bacf5-126">MembersToExclude</span></span>| <span data-ttu-id="bacf5-127">Gebruik deze eigenschap leden verwijderen uit het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="bacf5-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="bacf5-128">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="bacf5-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bacf5-129">Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="bacf5-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="bacf5-130">In dat geval wordt een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bacf5-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="bacf5-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="bacf5-131">MembersToInclude</span></span>| <span data-ttu-id="bacf5-132">Gebruik deze eigenschap leden toevoegen aan het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="bacf5-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="bacf5-133">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="bacf5-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bacf5-134">Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="bacf5-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="bacf5-135">In dat geval wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bacf5-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="bacf5-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bacf5-136">DependsOn</span></span> | <span data-ttu-id="bacf5-137">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="bacf5-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bacf5-138">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="bacf5-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="bacf5-139">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="bacf5-139">Example 1</span></span>

<span data-ttu-id="bacf5-140">Het volgende voorbeeld ziet hoe u om ervoor te zorgen dat een groep met de naam "Testgroep" afwezig is.</span><span class="sxs-lookup"><span data-stu-id="bacf5-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="bacf5-141">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="bacf5-141">Example 2</span></span>

<span data-ttu-id="bacf5-142">Het volgende voorbeeld laat zien hoe een Active Directory-gebruiker toevoegen aan de lokale groep administrators als onderdeel van een Machine met meerdere Lab-build waar u al een PSCredential worden gebruikt voor het lokale Administrator-account.</span><span class="sxs-lookup"><span data-stu-id="bacf5-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span>
<span data-ttu-id="bacf5-143">Als dit wordt ook gebruikt voor het beheeraccount van het domein (na de promotie van domein), moeten we vervolgens deze bestaande PSCredential omzetten in een domein beschrijvende referentie.</span><span class="sxs-lookup"><span data-stu-id="bacf5-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="bacf5-144">We kunnen vervolgens de gebruiker van een domein toevoegen aan de lokale groep Administrators op de lidserver.</span><span class="sxs-lookup"><span data-stu-id="bacf5-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="bacf5-145">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="bacf5-145">Example 3</span></span>

<span data-ttu-id="bacf5-146">Het volgende voorbeeld laat zien hoe om te controleren of een lokale groep, TigerTeamAdmins, op de server TigerTeamSource.Contoso.Com bevat niet de account van een bepaald domein, Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="bacf5-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSrouce {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```