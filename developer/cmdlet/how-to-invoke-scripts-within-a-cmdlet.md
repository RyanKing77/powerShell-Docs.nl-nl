---
title: Het aanroepen van Scripts in een Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846695"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="f9bce-102">Scripts in een cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="f9bce-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="f9bce-103">In dit voorbeeld laat zien hoe een script dat wordt doorgegeven aan een cmdlet aanroepen.</span><span class="sxs-lookup"><span data-stu-id="f9bce-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="f9bce-104">Het script is uitgevoerd door de cmdlet en de resultaten worden geretourneerd aan de cmdlet als een verzameling van [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objecten.</span><span class="sxs-lookup"><span data-stu-id="f9bce-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="f9bce-105">Om aan te roepen, een scriptblok</span><span class="sxs-lookup"><span data-stu-id="f9bce-105">To invoke a script block</span></span>

1. <span data-ttu-id="f9bce-106">De opdracht wordt gecontroleerd of een scriptblok is opgegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9bce-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="f9bce-107">Als een scriptblok is opgegeven, roept de opdracht in het scriptblok met de vereiste parameters.</span><span class="sxs-lookup"><span data-stu-id="f9bce-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="f9bce-108">Vervolgens de resulterende verzameling van het script doorloopt [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objecten en de noodzakelijke bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f9bce-108">Then, the script iterates through the returned collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="f9bce-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f9bce-109">See Also</span></span>

[<span data-ttu-id="f9bce-110">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f9bce-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)