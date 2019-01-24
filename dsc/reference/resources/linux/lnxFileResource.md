---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxFile-Resource
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048338"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="447e3-103">DSC voor Linux nxFile-Resource</span><span class="sxs-lookup"><span data-stu-id="447e3-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="447e3-104">De **nxFile** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="447e3-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="447e3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="447e3-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="447e3-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="447e3-106">Properties</span></span>

|  <span data-ttu-id="447e3-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="447e3-107">Property</span></span> |  <span data-ttu-id="447e3-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="447e3-108">Description</span></span> |
|---|---|
| <span data-ttu-id="447e3-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="447e3-109">DestinationPath</span></span>| <span data-ttu-id="447e3-110">Hiermee geeft u de locatie waar u om te controleren of de status van een bestand of map.</span><span class="sxs-lookup"><span data-stu-id="447e3-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="447e3-111">Bronpad</span><span class="sxs-lookup"><span data-stu-id="447e3-111">SourcePath</span></span>| <span data-ttu-id="447e3-112">Hiermee geeft u het pad van waaruit de resource van het bestand of map kopiëren.</span><span class="sxs-lookup"><span data-stu-id="447e3-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="447e3-113">Dit pad is mogelijk een lokaal pad of een `http/https/ftp` URL.</span><span class="sxs-lookup"><span data-stu-id="447e3-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="447e3-114">Externe `http/https/ftp` URL's worden alleen ondersteund wanneer de waarde van de **Type** eigenschap bestand is.</span><span class="sxs-lookup"><span data-stu-id="447e3-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="447e3-115">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="447e3-115">Ensure</span></span>| <span data-ttu-id="447e3-116">Hiermee bepaalt u of om te controleren of het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="447e3-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="447e3-117">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="447e3-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="447e3-118">Stel deze in op 'Ontbreekt' om te controleren of dat het bestand bestaat niet.</span><span class="sxs-lookup"><span data-stu-id="447e3-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="447e3-119">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="447e3-119">The default value is "Present".</span></span>|
| <span data-ttu-id="447e3-120">Type</span><span class="sxs-lookup"><span data-stu-id="447e3-120">Type</span></span>| <span data-ttu-id="447e3-121">Hiermee geeft u op of de resource wordt geconfigureerd een map of een bestand is.</span><span class="sxs-lookup"><span data-stu-id="447e3-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="447e3-122">Deze eigenschap instellen op 'directory' om aan te geven dat de resource een map is.</span><span class="sxs-lookup"><span data-stu-id="447e3-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="447e3-123">Stelt u deze naar het 'bestand' om aan te geven dat de resource een bestand is.</span><span class="sxs-lookup"><span data-stu-id="447e3-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="447e3-124">De standaardwaarde is 'file'</span><span class="sxs-lookup"><span data-stu-id="447e3-124">The default value is "file"</span></span>|
| <span data-ttu-id="447e3-125">Inhoud</span><span class="sxs-lookup"><span data-stu-id="447e3-125">Contents</span></span>| <span data-ttu-id="447e3-126">Hiermee geeft u de inhoud van een bestand, zoals een bepaalde tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="447e3-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="447e3-127">Controlesom</span><span class="sxs-lookup"><span data-stu-id="447e3-127">Checksum</span></span>| <span data-ttu-id="447e3-128">Definieert het type te gebruiken bij het bepalen of twee bestanden hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="447e3-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="447e3-129">Als **controlesom** niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="447e3-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="447e3-130">Waarden zijn: 'ctime","mtime"of 'md5'.</span><span class="sxs-lookup"><span data-stu-id="447e3-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="447e3-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="447e3-131">Recurse</span></span>| <span data-ttu-id="447e3-132">Hiermee wordt aangegeven als submappen opgenomen worden.</span><span class="sxs-lookup"><span data-stu-id="447e3-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="447e3-133">Deze eigenschap instellen op **$true** om aan te geven dat u wilt dat de submappen moeten worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="447e3-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="447e3-134">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="447e3-134">The default is **$false**.</span></span> <span data-ttu-id="447e3-135">**Opmerking:** Deze eigenschap is alleen geldig wanneer de **Type** eigenschap is ingesteld op de directory.</span><span class="sxs-lookup"><span data-stu-id="447e3-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="447e3-136">Force</span><span class="sxs-lookup"><span data-stu-id="447e3-136">Force</span></span>| <span data-ttu-id="447e3-137">Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg), een fout leidt.</span><span class="sxs-lookup"><span data-stu-id="447e3-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="447e3-138">Met behulp van de **Force** eigenschap heeft voorrang op dergelijke fouten.</span><span class="sxs-lookup"><span data-stu-id="447e3-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="447e3-139">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="447e3-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="447e3-140">Koppelingen</span><span class="sxs-lookup"><span data-stu-id="447e3-140">Links</span></span>| <span data-ttu-id="447e3-141">Hiermee geeft u het gewenste gedrag voor symbolische koppelingen.</span><span class="sxs-lookup"><span data-stu-id="447e3-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="447e3-142">Deze eigenschap instellen op 'volgen' symbolische koppelingen volgen en reageren op de doel-koppelingen (bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="447e3-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="447e3-143">Kopieer het bestand in plaats van de koppeling).</span><span class="sxs-lookup"><span data-stu-id="447e3-143">copy the file instead of the link).</span></span> <span data-ttu-id="447e3-144">Deze eigenschap instellen op 'beheren' om te reageren op de koppeling (bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="447e3-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="447e3-145">Kopieer de koppeling zelf).</span><span class="sxs-lookup"><span data-stu-id="447e3-145">copy the link itself).</span></span> <span data-ttu-id="447e3-146">Deze eigenschap instellen op 'negeren' symbolische koppelingen worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="447e3-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="447e3-147">Groep</span><span class="sxs-lookup"><span data-stu-id="447e3-147">Group</span></span>| <span data-ttu-id="447e3-148">De naam van de **groep** eigenaar van het bestand of map.</span><span class="sxs-lookup"><span data-stu-id="447e3-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="447e3-149">Modus</span><span class="sxs-lookup"><span data-stu-id="447e3-149">Mode</span></span>| <span data-ttu-id="447e3-150">Hiermee geeft u de gewenste machtigingen voor de resource in de octale of symbolische-notatie.</span><span class="sxs-lookup"><span data-stu-id="447e3-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="447e3-151">(bijvoorbeeld 777 of rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="447e3-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="447e3-152">Als u de symbolische notatie, bieden het eerste teken waarmee wordt aangegeven van de map of het bestand.</span><span class="sxs-lookup"><span data-stu-id="447e3-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="447e3-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="447e3-153">DependsOn</span></span> | <span data-ttu-id="447e3-154">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="447e3-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="447e3-155">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="447e3-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="447e3-156">Als u meer informatie</span><span class="sxs-lookup"><span data-stu-id="447e3-156">Additional Information</span></span>


<span data-ttu-id="447e3-157">Linux- en Windows gebruik van verschillende regeleindetekens in tekstbestanden standaard en dit kan leiden tot onverwachte resultaten bij het configureren van bepaalde bestanden op een Linux-computer met __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="447e3-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="447e3-158">Er zijn meerdere manieren voor het beheren van de inhoud van een Linux-bestand zonder problemen veroorzaakt door onverwachte regeleindetekens:</span><span class="sxs-lookup"><span data-stu-id="447e3-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="447e3-159">Stap 1: Kopieer het bestand vanaf een externe bron (http, https of ftp): Maak een bestand op Linux met de gewenste inhoud, en de knooppunten die u configureert Faseren op een webserver of FTP-server toegankelijk is.</span><span class="sxs-lookup"><span data-stu-id="447e3-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="447e3-160">Definieer de __bronpad__ eigenschap in de __nxFile__ resource met de web- of FTP-URL naar het bestand.</span><span class="sxs-lookup"><span data-stu-id="447e3-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


<span data-ttu-id="447e3-161">Stap 2: Lezen van de inhoud van het bestand in het PowerShell-script met [Get-inhoud](https://technet.microsoft.com/library/hh849787.aspx) nadat u de __$OFS__ eigenschap om de Linux-regeleinde teken te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="447e3-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="447e3-162">Stap 3: Een PowerShell-functie gebruiken om te vervangen door Windows met Linux regeleinde tekens regeleinden.</span><span class="sxs-lookup"><span data-stu-id="447e3-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a><span data-ttu-id="447e3-163">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="447e3-163">Example</span></span>

<span data-ttu-id="447e3-164">Het volgende voorbeeld zorgt ervoor dat de map `/opt/mydir` bestaat, en dat een bestand met de opgegeven inhoud deze map bestaat.</span><span class="sxs-lookup"><span data-stu-id="447e3-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```