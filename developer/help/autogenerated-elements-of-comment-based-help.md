---
title: Automatisch gegenereerde elementen van de Help op basis van een opmerking | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a7098fe-0854-4fbb-83e9-073c20b299c7
caps.latest.revision: 4
ms.openlocfilehash: 0b8a32b5588e29148800daff8e104abba548eaf6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083549"
---
# <a name="autogenerated-elements-of-comment-based-help"></a>Automatisch gegenereerde elementen van de Help op basis van opmerkingen

De `Get-Help` cmdlet genereert automatisch verschillende elementen van een onderwerp op basis van een opmerking. Deze elementen automatisch gegenereerde maken op basis van een opmerking help zoeken erg veel lijkt op het Help-informatie die is gegenereerd op basis van XML-bestanden.

## <a name="autogenerated-elements"></a>Automatisch gegenereerde elementen

De `Get-Help` cmdlet genereert automatisch de volgende elementen van een help-onderwerp. U kunt deze elementen niet rechtstreeks bewerken, maar in veel gevallen kunt u de resultaten wijzigen door het wijzigen van de bron van het element.

### <a name="name"></a>Naam

De sectie van een functie Help-onderwerp is afkomstig uit de naam van de functie in het functiedefinitie van de. De naam van een Help-onderwerp van het script is afkomstig uit de naam van het scriptbestand. De naam of het hoofdlettergebruik wilt wijzigen, de functiedefinitie van de of de naam van het scriptbestand te wijzigen.

### <a name="syntax"></a>Syntaxis

De sectie syntaxis van het Help-onderwerp is gegenereerd op basis van de lijst met parameters in de parameter-instructie van de functie of het script. Details toevoegen aan het Help-onderwerp toevoegen syntaxissen, zoals het .NET Framework-type van een parameter, de details aan de lijst met parameters. Als u een parametertype niet opgeeft, wordt het type "Object" ingevoegd als de standaardwaarde.

### <a name="parameter-list"></a>Lijst met parameters

De sectie Parameters van het Help-onderwerp wordt gegenereerd uit de lijst met parameters in de functie of het script en uit de beschrijvingen die u met behulp van toevoegt de `.Parameters` trefwoord of opmerkingen in de lijst met parameters.

Parameters worden weergegeven in de sectie Parameters in dezelfde volgorde als waarin ze worden weergegeven in de lijst met parameters. De spelling en het hoofdlettergebruik van de namen van parameters is ook afkomstig uit de lijst met parameters; het wordt niet beïnvloed door de parameternaam van de opgegeven door de `.Parameter` trefwoord.

### <a name="common-parameters"></a>Algemene Parameters

De algemene parameters worden toegevoegd aan de lijst met syntaxis en parameters van het Help-onderwerp, zelfs als ze geen effect hebben. Zie voor meer informatie over de algemene parameters, [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

### <a name="parameter-attribute-table"></a>Parameter-kenmerkentabel

`Get-Help` de tabel van de parameterkenmerken die wordt weergegeven wanneer u de volledige of de Parameter-parameter van genereert `Get-Help`. De waarde van de vereiste, de positie en de standaard waardekenmerken is genomen van de syntaxis van de functie of script.

### <a name="remarks"></a>Opmerkingen

De sectie met opmerkingen van het Help-onderwerp is automatisch gegenereerd op basis van de naam van de functie of script. U kan wijzigen of invloed hebben op de inhoud ervan.
