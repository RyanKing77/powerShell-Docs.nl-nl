---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Samengestelde bronnen--met een DSC-configuratie als een bron
ms.openlocfilehash: 4a9574081d3579ffa910bf2ee595ba2550f40a15
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="4f57a-103">Samengestelde bronnen: met een DSC-configuratie als een bron</span><span class="sxs-lookup"><span data-stu-id="4f57a-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="4f57a-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4f57a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="4f57a-105">In de praktijk situaties worden configuraties lange en complexe, aanroepen van veel verschillende bronnen en het instellen van een groot aantal eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="4f57a-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="4f57a-106">Om te helpen met het adres van deze complexiteit, kunt u de configuratie van een Windows PowerShell Desired State Configuration (DSC) als een resource voor andere configuraties.</span><span class="sxs-lookup"><span data-stu-id="4f57a-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="4f57a-107">We noemen dit een samengestelde bron.</span><span class="sxs-lookup"><span data-stu-id="4f57a-107">We call this a composite resource.</span></span> <span data-ttu-id="4f57a-108">Een samengestelde bron is een DSC-configuratie die parameters zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="4f57a-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="4f57a-109">De parameters van de configuratie fungeren als de eigenschappen van de resource.</span><span class="sxs-lookup"><span data-stu-id="4f57a-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="4f57a-110">De configuratie wordt opgeslagen als een bestand met een **. schema.psm1** extensie en wordt de plaats van zowel het MOF-schema en de resource een script in een typische DSC-resource (Zie voor meer informatie over DSC-resources [Windows PowerShell Desired State Configuration Resources](resources.md).</span><span class="sxs-lookup"><span data-stu-id="4f57a-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="4f57a-111">Maken van de samengestelde resource</span><span class="sxs-lookup"><span data-stu-id="4f57a-111">Creating the composite resource</span></span>

<span data-ttu-id="4f57a-112">In ons voorbeeld maken we een configuratie met een aantal bestaande resources voor het configureren van virtuele machines wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="4f57a-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="4f57a-113">In plaats van de waarden worden ingesteld in configuratie blokken opgeeft, wordt de configuratie een aantal parameters die worden gebruikt in de configuratie-blokken.</span><span class="sxs-lookup"><span data-stu-id="4f57a-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="4f57a-114">De configuratie op te slaan als een samengestelde bron</span><span class="sxs-lookup"><span data-stu-id="4f57a-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="4f57a-115">Opslaan in een mapstructuur net als elke andere MOF op basis van een bron voor het gebruik van de configuratie van de parameters als een DSC-resource, en de naam met een **. schema.psm1** extensie.</span><span class="sxs-lookup"><span data-stu-id="4f57a-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="4f57a-116">In dit voorbeeld Noem we het bestand **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="4f57a-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="4f57a-117">U moet ook een manifest met de naam maken **xVirtualMachine.psd1** die de volgende regel bevat.</span><span class="sxs-lookup"><span data-stu-id="4f57a-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="4f57a-118">Dit is in aanvulling op **MyDscResources.psd1**, de module-manifest voor alle resources onder de **MyDscResources** map.</span><span class="sxs-lookup"><span data-stu-id="4f57a-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="4f57a-119">Wanneer u klaar bent, moeten de mapstructuur als volgt.</span><span class="sxs-lookup"><span data-stu-id="4f57a-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="4f57a-120">De resource kan nu worden gedetecteerd met de cmdlet Get-DscResource en bijbehorende eigenschappen kunnen worden gevonden door beide die cmdlet of via **Ctrl + spatiebalk** automatisch aanvullen in de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4f57a-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="4f57a-121">Met behulp van de samengestelde bron</span><span class="sxs-lookup"><span data-stu-id="4f57a-121">Using the composite resource</span></span>

<span data-ttu-id="4f57a-122">Vervolgens maken we een configuratie die de samengestelde bron aanroept.</span><span class="sxs-lookup"><span data-stu-id="4f57a-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="4f57a-123">Deze configuratie roept de xVirtualMachine samengestelde bron voor het maken van een virtuele machine en roept vervolgens de **xComputer** resource te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="4f57a-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="4f57a-124">Ondersteunende PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4f57a-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="4f57a-125">**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="4f57a-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="4f57a-126">De **PsDscRunAsCredential** eigenschap kan worden gebruikt [DSC-configuraties](configurations.md) resource blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="4f57a-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="4f57a-127">Zie voor meer informatie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="4f57a-127">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="4f57a-128">Voor toegang tot de gebruikerscontext van binnen een aangepaste bron, kunt u de automatische variabele `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="4f57a-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="4f57a-129">De volgende code zou bijvoorbeeld de gebruikerscontext waaronder de bron wordt uitgevoerd naar de uitgebreide uitvoerstroom schrijven:</span><span class="sxs-lookup"><span data-stu-id="4f57a-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="4f57a-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4f57a-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="4f57a-131">Concepten</span><span class="sxs-lookup"><span data-stu-id="4f57a-131">Concepts</span></span>
* [<span data-ttu-id="4f57a-132">Schrijven van een aangepaste DSC-resource met MOF</span><span class="sxs-lookup"><span data-stu-id="4f57a-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="4f57a-133">Aan de slag met Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="4f57a-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](overview.md)

