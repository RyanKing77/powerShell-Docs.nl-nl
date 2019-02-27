---
title: Codevoorbeeld RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845442"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="2b4a2-102">Runspace09-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="2b4a2-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="2b4a2-103">Hier volgt de broncode voor het voorbeeld Runspace09 die zijn beschreven [het maken van een Console-toepassing die roept een pijplijn asynchroon](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="2b4a2-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="2b4a2-104">Deze voorbeeldtoepassing maakt en een runspace wordt geopend, maakt en een pijplijn asynchroon aanroept, en vervolgens maakt gebruik van pipeline-gebeurtenissen voor het asynchroon verwerken van het script.</span><span class="sxs-lookup"><span data-stu-id="2b4a2-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="2b4a2-105">Het script dat wordt uitgevoerd door deze toepassing maakt de getallen 1 t/m 10 0,5 seconde intervallen (500 ms).</span><span class="sxs-lookup"><span data-stu-id="2b4a2-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="2b4a2-106">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="2b4a2-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="2b4a2-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2b4a2-107">See Also</span></span>

[<span data-ttu-id="2b4a2-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2b4a2-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)