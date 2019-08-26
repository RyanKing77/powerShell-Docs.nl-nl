---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: Overzicht van net voldoende beheer
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017858"
---
# <a name="just-enough-administration"></a><span data-ttu-id="e3b33-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="e3b33-103">Just Enough Administration</span></span>

<span data-ttu-id="e3b33-104">Net genoeg beheer (JEA) is een beveiligings technologie waarmee gedelegeerd beheer kan worden ingeschakeld voor alles dat wordt beheerd door Power shell.</span><span class="sxs-lookup"><span data-stu-id="e3b33-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything managed by PowerShell.</span></span> <span data-ttu-id="e3b33-105">Met JEA kunt u het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="e3b33-105">With JEA, you can:</span></span>

- <span data-ttu-id="e3b33-106">**Verminder het aantal beheerders op uw computers** door gebruik te maken van virtuele accounts of door groep beheerde service accounts om geprivilegieerde acties uit te voeren namens normale gebruikers.</span><span class="sxs-lookup"><span data-stu-id="e3b33-106">**Reduce the number of administrators on your machines** using virtual accounts or group-managed service accounts to perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="e3b33-107">**Beperk wat gebruikers kunnen doen** door op te geven welke cmdlets, functies en externe opdrachten ze kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e3b33-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="e3b33-108">**Beter inzicht in wat uw gebruikers doen** met transcripten en logboeken waarin u precies kunt zien welke opdrachten een gebruiker heeft uitgevoerd tijdens de sessie.</span><span class="sxs-lookup"><span data-stu-id="e3b33-108">**Better understand what your users are doing** with transcripts and logs that show you exactly which commands a user executed during their session.</span></span>

<span data-ttu-id="e3b33-109">**Waarom is JEA belang rijk?**</span><span class="sxs-lookup"><span data-stu-id="e3b33-109">**Why is JEA important?**</span></span>

<span data-ttu-id="e3b33-110">Accounts met zeer privileges die worden gebruikt voor het beheer van uw servers vormen een ernstig beveiligings risico.</span><span class="sxs-lookup"><span data-stu-id="e3b33-110">Highly privileged accounts used to administer your servers pose a serious security risk.</span></span> <span data-ttu-id="e3b33-111">Als een kwaadwillende persoon een van deze accounts zou misbruiken, kunnen ze [zijdelingse aanvallen](https://aka.ms/pth) in uw organisatie starten.</span><span class="sxs-lookup"><span data-stu-id="e3b33-111">Should an attacker compromise one of these accounts, they could launch [lateral attacks](https://aka.ms/pth) across your organization.</span></span> <span data-ttu-id="e3b33-112">Elk aangetast account geeft een aanvaller toegang tot nog meer accounts en resources, en plaatst ze één stap dichter om bedrijfs geheimen te stelen, een denial-of-service-aanval te starten, en meer.</span><span class="sxs-lookup"><span data-stu-id="e3b33-112">Each compromised account gives an attacker access to even more accounts and resources, and puts them one step closer to stealing company secrets, launching a denial-of-service attack, and more.</span></span>

<span data-ttu-id="e3b33-113">Het is niet altijd eenvoudig om beheerders bevoegdheden te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e3b33-113">It's not always easy to remove administrative privileges, either.</span></span> <span data-ttu-id="e3b33-114">Houd rekening met het algemene scenario waarbij de DNS-rol is geïnstalleerd op dezelfde computer als uw Active Directory-domein controller.</span><span class="sxs-lookup"><span data-stu-id="e3b33-114">Consider the common scenario where the DNS role is installed on the same machine as your Active Directory Domain Controller.</span></span> <span data-ttu-id="e3b33-115">Uw DNS-beheerders hebben lokale beheerders bevoegdheden nodig om problemen met de DNS-server op te lossen.</span><span class="sxs-lookup"><span data-stu-id="e3b33-115">Your DNS administrators require local administrator privileges to fix issues with the DNS server.</span></span> <span data-ttu-id="e3b33-116">Maar hiervoor moet u de leden van de beveiligings groep **domein Administrators** met zeer privileged maken.</span><span class="sxs-lookup"><span data-stu-id="e3b33-116">But to do so, you must make them members of the highly privileged **Domain Admins** security group.</span></span> <span data-ttu-id="e3b33-117">Deze aanpak zorgt ervoor dat DNS-beheerders de controle over het hele domein en toegang tot alle resources op die computer hebben.</span><span class="sxs-lookup"><span data-stu-id="e3b33-117">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="e3b33-118">JEA lost dit probleem op door middel van het principe van **minimale bevoegdheden**.</span><span class="sxs-lookup"><span data-stu-id="e3b33-118">JEA addresses this problem through the principle of **Least Privilege**.</span></span> <span data-ttu-id="e3b33-119">Met JEA kunt u een beheer eindpunt configureren voor DNS-beheerders waarmee ze toegang hebben tot de Power shell-opdrachten die ze nodig hebben om hun werk te doen.</span><span class="sxs-lookup"><span data-stu-id="e3b33-119">With JEA, you can configure a management endpoint for DNS administrators that gives them access only to the PowerShell commands they need to get their job done.</span></span> <span data-ttu-id="e3b33-120">Dit betekent dat u de juiste toegang kunt bieden om een verontreinigde DNS-cache te herstellen of de DNS-server opnieuw op te starten zonder per ongeluk toestemming te geven aan Active Directory, of door het bestands systeem te bladeren of potentieel gevaarlijke scripts uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e3b33-120">This means you can provide the appropriate access to repair a poisoned DNS cache or restart the DNS server without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span> <span data-ttu-id="e3b33-121">Wanneer de JEA-sessie nog beter is geconfigureerd voor het gebruik van tijdelijke privileged Virtual accounts, kunnen uw DNS-beheerders verbinding maken met de server met behulp van **niet-beheerders** referenties en blijven opdrachten uitvoeren die doorgaans beheerders bevoegdheden nodig hebben.</span><span class="sxs-lookup"><span data-stu-id="e3b33-121">Better yet, when the JEA session is configured to use temporary privileged virtual accounts, your DNS administrators can connect to the server using **non-admin** credentials and still run commands that typically require admin privileges.</span></span> <span data-ttu-id="e3b33-122">Met JEA kunt u gebruikers verwijderen uit beheerders rollen van algemeen privileged en zorgvuldig bepalen wat ze op elke computer kunnen doen.</span><span class="sxs-lookup"><span data-stu-id="e3b33-122">JEA enables you to remove users from widely privileged local/domain administrator roles and carefully control what they can do on each machine.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e3b33-123">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="e3b33-123">Next steps</span></span>

<span data-ttu-id="e3b33-124">Meer informatie over de vereisten voor het gebruik van JEA vindt u [](prerequisites.md) in het artikel vereisten.</span><span class="sxs-lookup"><span data-stu-id="e3b33-124">To learn more about the requirements to use JEA, see the [Prerequisites](prerequisites.md) article.</span></span>

## <a name="samples-and-dsc-resource"></a><span data-ttu-id="e3b33-125">Voor beelden en DSC-resource</span><span class="sxs-lookup"><span data-stu-id="e3b33-125">Samples and DSC resource</span></span>

<span data-ttu-id="e3b33-126">Voor beelden van JEA-configuraties en de DSC-resource van JEA vindt u in de [JEA github-opslag plaats](https://github.com/PowerShell/JEA).</span><span class="sxs-lookup"><span data-stu-id="e3b33-126">Sample JEA configurations and the JEA DSC resource can be found in the [JEA GitHub repository](https://github.com/PowerShell/JEA).</span></span>