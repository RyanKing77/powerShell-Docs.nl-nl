---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 7817769c3fc060a51c833b7469f7b556b9b40e87
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-method"></a><span data-ttu-id="26b8d-102">Basisklassenmethode aanroepen</span><span class="sxs-lookup"><span data-stu-id="26b8d-102">Call Base Class Method</span></span>

<span data-ttu-id="26b8d-103">U kunt bestaande methoden in subklassen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="26b8d-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="26b8d-104">U doet dit door methoden met behulp van dezelfde naam en handtekening te declareren:</span><span class="sxs-lookup"><span data-stu-id="26b8d-104">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="26b8d-105">Voor het aanroepen van methoden van de basisklasse van overschreven implementaties, geconverteerd naar de basisklasse ([baseClass] $dit) op aanroepen:</span><span class="sxs-lookup"><span data-stu-id="26b8d-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="26b8d-106">Alle methoden van PowerShell zijn virtueel.</span><span class="sxs-lookup"><span data-stu-id="26b8d-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="26b8d-107">U kunt niet-virtuele .NET-methoden in een subklasse verbergen met behulp van dezelfde syntaxis als voor een onderdrukking: alleen methoden met dezelfde naam en handtekening declareren.</span><span class="sxs-lookup"><span data-stu-id="26b8d-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

