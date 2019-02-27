---
title: Codevoorbeeld AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845134"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDBProviderSample04-codevoorbeeld

De volgende code toont de uitvoering van de Windows PowerShell-provider wordt beschreven in [het maken van een Windows PowerShell-Provider Container](./creating-a-windows-powershell-container-provider.md). Deze provider werkt op meerdere lagen gegevensarchieven. Het hoogste niveau van de store bevat de items van de hoofdmap voor dit type gegevensarchief, en elke latere niveau wordt aangeduid als een knooppunt van het onderliggende items. Een gebruiker kan door de gebruiker om te werken op deze onderliggende knooppunten, hiërarchisch communiceren via het gegevensarchief.

## <a name="code-sample"></a>Voorbeeld van code

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)