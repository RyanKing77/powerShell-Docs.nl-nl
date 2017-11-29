---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

Hiermee verwijdert u de configuratiebestanden.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parameters
----------

*Fase* \[in\]  
Hiermee geeft u op welke configuratie-document te verwijderen. De volgende waarden zijn geldig:

|Value |Beschrijving |
|:--- |:---|
|**1** | De **huidige** configuratie document (current.mof). |
|**2** | De **in behandeling** configuratie document (pending.mof).  |
|**4** | De **vorige** configuratie document (previous.mof). |

*Force* \[in\]  
**de waarde True** om af te dwingen van het verwijderen van de configuratie.

## <a name="return-value"></a>Retourwaarde
------------

Retourneert nul geslaagd; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Zie ook


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 


