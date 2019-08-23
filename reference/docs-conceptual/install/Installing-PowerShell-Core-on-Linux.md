---
title: PowerShell Core in Linux installeren
description: Informatie over het installeren van Power shell Core op diverse Linux-distributies
ms.date: 07/19/2019
ms.openlocfilehash: be11a2a873af71c193730d0a9e723da2dc70a62d
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986733"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="083be-103">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="083be-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="083be-104">Ondersteunt [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE schrikkel 15][opensuse], [Fedora 27 ][fedora], [Fedora 28][fedora]en [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="083be-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="083be-105">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="083be-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="083be-106">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks [ `tar.gz` ][tar]te implementeren met behulp van het Linux-archief, maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="083be-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="083be-107">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="083be-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="083be-108">Nadat het pakket is geïnstalleerd, voert `pwsh` u uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="083be-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="083be-109">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="083be-109">Installing Preview Releases</span></span>

<span data-ttu-id="083be-110">Wanneer u een Power shell core preview-versie voor Linux installeert via een pakket opslagplaats, wordt de `powershell` naam `powershell-preview`van het pakket gewijzigd van in.</span><span class="sxs-lookup"><span data-stu-id="083be-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="083be-111">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="083be-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="083be-112">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="083be-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="083be-113">Distributie (s)</span><span class="sxs-lookup"><span data-stu-id="083be-113">Distribution(s)</span></span>|<span data-ttu-id="083be-114">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="083be-114">Stable Command</span></span> | <span data-ttu-id="083be-115">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="083be-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="083be-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="083be-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="083be-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="083be-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="083be-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="083be-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="083be-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="083be-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="083be-120">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="083be-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="083be-121">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="083be-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="083be-122">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="083be-122">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="083be-123">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="083be-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="083be-124">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="083be-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="083be-125">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="083be-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="083be-126">Down load het Debian `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` -pakket van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="083be-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="083be-127">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="083be-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="083be-128">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="083be-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="083be-129">Met de volgende opdracht `apt-get install -f` worden deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="083be-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="083be-130">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="083be-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="083be-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="083be-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="083be-132">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="083be-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="083be-133">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="083be-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="083be-134">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="083be-134">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="083be-135">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="083be-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="083be-136">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="083be-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="083be-137">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="083be-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="083be-138">Down load het Debian `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` -pakket van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="083be-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="083be-139">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="083be-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="083be-140">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="083be-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="083be-141">Met de volgende opdracht `apt-get install -f` worden deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="083be-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="083be-142">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="083be-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="083be-143">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="083be-143">Ubuntu 18.10</span></span>

<span data-ttu-id="083be-144">De installatie wordt ondersteund `snapd`via.</span><span class="sxs-lookup"><span data-stu-id="083be-144">Installation is supported via `snapd`.</span></span> <span data-ttu-id="083be-145">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="083be-145">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="083be-146">Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="083be-146">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="083be-147">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="083be-147">Ubuntu 19.04</span></span>

<span data-ttu-id="083be-148">De installatie wordt ondersteund `snapd`via.</span><span class="sxs-lookup"><span data-stu-id="083be-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="083be-149">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="083be-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="083be-150">Ubuntu 19,04 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="083be-150">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="083be-151">Debian 8</span><span class="sxs-lookup"><span data-stu-id="083be-151">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="083be-152">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="083be-152">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="083be-153">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="083be-153">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="083be-154">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="083be-154">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="083be-155">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="083be-155">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="083be-156">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="083be-156">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="083be-157">Debian 9</span><span class="sxs-lookup"><span data-stu-id="083be-157">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="083be-158">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="083be-158">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="083be-159">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="083be-159">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="083be-160">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="083be-160">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="083be-161">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="083be-161">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="083be-162">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="083be-162">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="083be-163">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="083be-163">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="083be-164">Down load het Debian `powershell_6.2.0-1.debian.9_amd64.deb` -pakket van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="083be-164">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="083be-165">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="083be-165">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="083be-166">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="083be-166">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="083be-167">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="083be-167">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="083be-168">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="083be-168">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="083be-169">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="083be-169">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="083be-170">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="083be-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="083be-171">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="083be-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="083be-172">Na de registratie kunt u Power shell bijwerken `sudo yum update powershell`met.</span><span class="sxs-lookup"><span data-stu-id="083be-172">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="083be-173">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="083be-173">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="083be-174">Gebruik [CentOS 7][]om het rpm-pakket `powershell-6.2.0-1.rhel.7.x86_64.rpm` te downloaden van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="083be-174">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="083be-175">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="083be-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="083be-176">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="083be-176">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="083be-177">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="083be-177">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="083be-179">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="083be-179">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="083be-180">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="083be-180">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="083be-181">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="083be-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="083be-182">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="083be-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="083be-183">Na de registratie kunt u Power shell bijwerken `sudo yum update powershell`met.</span><span class="sxs-lookup"><span data-stu-id="083be-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="083be-184">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="083be-184">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="083be-185">Down load het rpm `powershell-6.2.0-1.rhel.7.x86_64.rpm` -pakket van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="083be-185">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="083be-186">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="083be-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="083be-187">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="083be-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="083be-188">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="083be-188">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="083be-189">openSUSE</span><span class="sxs-lookup"><span data-stu-id="083be-189">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="083be-190">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="083be-190">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="083be-191">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="083be-191">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="083be-192">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="083be-192">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="083be-193">Fedora</span><span class="sxs-lookup"><span data-stu-id="083be-193">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="083be-194">Fedora 28 wordt alleen ondersteund in Power shell Core 6,1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="083be-194">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="083be-195">Installatie via pakket opslagplaats (voor keur)-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="083be-195">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="083be-196">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="083be-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="083be-197">Installatie via directe down load-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="083be-197">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="083be-198">Down load het rpm `powershell-6.2.0-1.rhel.7.x86_64.rpm` -pakket van de pagina [releases][] op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="083be-198">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="083be-199">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="083be-199">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="083be-200">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="083be-200">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="083be-201">Installatie ongedaan maken-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="083be-201">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="083be-202">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="083be-202">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="083be-203">Arch-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="083be-203">Arch support is experimental.</span></span>

<span data-ttu-id="083be-204">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="083be-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="083be-205">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="083be-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="083be-206">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="083be-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="083be-207">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="083be-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="083be-208">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="083be-208">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="083be-209">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="083be-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="083be-211">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="083be-211">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="083be-212">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="083be-212">Getting snapd</span></span>

<span data-ttu-id="083be-213">`snapd`is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="083be-213">`snapd` is required to run snaps.</span></span> <span data-ttu-id="083be-214">Volg [deze instructies](https://docs.snapcraft.io/core/install) om te controleren of u `snapd` hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="083be-214">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="083be-215">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="083be-215">Installation via Snap</span></span>

<span data-ttu-id="083be-216">Power shell core voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="083be-216">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="083be-217">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="083be-217">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="083be-218">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="083be-218">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="083be-219">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="083be-219">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="083be-220">U kunt een upgrade activeren met `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="083be-220">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="083be-221">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="083be-221">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="083be-222">of</span><span class="sxs-lookup"><span data-stu-id="083be-222">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="083be-223">Kali</span><span class="sxs-lookup"><span data-stu-id="083be-223">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="083be-224">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="083be-224">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="083be-225">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="083be-225">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="083be-226">Raspbian</span><span class="sxs-lookup"><span data-stu-id="083be-226">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="083be-227">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="083be-227">Raspbian support is experimental.</span></span>

<span data-ttu-id="083be-228">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="083be-228">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="083be-229">CoreCLR en Power shell core werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="083be-229">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="083be-230">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="083be-230">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="083be-231">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="083be-231">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="083be-232">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar het `pwsh` binaire bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="083be-232">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="083be-233">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="083be-233">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="083be-234">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="083be-234">Binary Archives</span></span>

<span data-ttu-id="083be-235">Er zijn `tar.gz` binaire Power shell-archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="083be-235">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="083be-236">Elkaar</span><span class="sxs-lookup"><span data-stu-id="083be-236">Dependencies</span></span>

<span data-ttu-id="083be-237">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="083be-237">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="083be-238">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="083be-238">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="083be-239">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="083be-239">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="083be-240">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="083be-240">OS</span></span>                 | <span data-ttu-id="083be-241">Elkaar</span><span class="sxs-lookup"><span data-stu-id="083be-241">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="083be-242">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="083be-242">Ubuntu 16.04</span></span>       | <span data-ttu-id="083be-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="083be-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="083be-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="083be-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="083be-245">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="083be-245">Ubuntu 17.10</span></span>       | <span data-ttu-id="083be-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="083be-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="083be-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="083be-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="083be-248">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="083be-248">Ubuntu 18.04</span></span>       | <span data-ttu-id="083be-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="083be-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="083be-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="083be-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="083be-251">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="083be-251">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="083be-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="083be-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="083be-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="083be-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="083be-254">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="083be-254">Debian 9 (Stretch)</span></span> | <span data-ttu-id="083be-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="083be-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="083be-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="083be-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="083be-257">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="083be-257">CentOS 7</span></span> <br> <span data-ttu-id="083be-258">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="083be-258">Oracle Linux 7</span></span> <br> <span data-ttu-id="083be-259">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="083be-259">RHEL 7</span></span> | <span data-ttu-id="083be-260">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="083be-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="083be-261">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="083be-261">openSUSE 42.3</span></span> | <span data-ttu-id="083be-262">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="083be-262">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="083be-263">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="083be-263">openSUSE Leap 15</span></span> | <span data-ttu-id="083be-264">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="083be-264">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="083be-265">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="083be-265">Fedora 27</span></span> <br> <span data-ttu-id="083be-266">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="083be-266">Fedora 28</span></span> | <span data-ttu-id="083be-267">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="083be-267">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="083be-268">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="083be-268">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="083be-269">Bijvoorbeeld, onze [Amazon Linux-dockerfile][amazon-dockerfile] installeert eerst afhankelijkheden en extraheert vervolgens het Linux `tar.gz` -archief.</span><span class="sxs-lookup"><span data-stu-id="083be-269">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="083be-270">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="083be-270">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="083be-271">Linux</span><span class="sxs-lookup"><span data-stu-id="083be-271">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="083be-272">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="083be-272">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="083be-273">Paden</span><span class="sxs-lookup"><span data-stu-id="083be-273">Paths</span></span>

* <span data-ttu-id="083be-274">`$PSHOME`ontbreekt`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="083be-274">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="083be-275">Gebruikers profielen worden gelezen van`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="083be-275">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="083be-276">Standaard profielen worden gelezen uit`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="083be-276">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="083be-277">Gebruikers modules worden gelezen uit`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="083be-277">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="083be-278">Gedeelde modules worden gelezen van`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="083be-278">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="083be-279">Standaard modules worden gelezen van`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="083be-279">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="083be-280">De PSReadline-geschiedenis wordt vastgelegd in`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="083be-280">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="083be-281">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` dezelfde locatie bestaan.</span><span class="sxs-lookup"><span data-stu-id="083be-281">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="083be-282">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="083be-282">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
