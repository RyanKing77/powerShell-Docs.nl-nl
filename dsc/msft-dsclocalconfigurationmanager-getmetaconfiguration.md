---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

Hiermee haalt u de lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a>Parameters
----------

*Metaconfiguratie* \[uit\]  
Op return bevat een ingesloten exemplaar van de **MSFT_DSCMetaConfiguration** klasse die de instellingen definieert.

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


 

 



