---
title: Voorbeeld van Events01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229301"
---
# <a name="events01-sample"></a>Voorbeeld Events01

Dit voorbeeld laat zien over het maken van een cmdlet waarmee de gebruiker om u te registreren voor gebeurtenissen die worden gegenereerd door [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).
Met deze cmdlet, kunnen gebruikers zich registreren een actie om uit te voeren wanneer een bestand wordt gemaakt onder een specifieke map.
In dit voorbeeld is afgeleid van de [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) basisklasse.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Over het bouwen van het voorbeeld met behulp van Visual Studio.

1. Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map Events01.
   De standaardlocatie is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.

2. Dubbelklik op het pictogram voor het oplossingsbestand (.sln).
   Hiermee opent u het voorbeeldproject in Microsoft Visual Studio.

3. In de **bouwen** in het menu **Build Solution**.
   De bibliotheek voor het voorbeeld worden samengesteld uit de standaard `\bin` of `\bin\debug` mappen.

### <a name="how-to-run-the-sample"></a>Hoe u het voorbeeld uitvoeren

1. Maak de volgende modulemap:

    `[user]/documents/windowspowershell/modules/events01`

2. Kopieer het DLL-bestand voor het voorbeeld naar de modulemap.

3. Start Windows PowerShell.

4. Voer de volgende opdracht om het laden van de cmdlet in Windows PowerShell:

    ```powershell
    import-module events01
    ```

5. Gebruik de cmdlet Register-FileSystemEvent voor het registreren van een actie die een bericht wordt geschreven wanneer een bestand wordt gemaakt in de map TEMP.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Maak een bestand in de map TEMP en houd er rekening mee dat de actie wordt uitgevoerd (het bericht wordt weergegeven).

Dit is een voorbeeld van de uitvoer die het resultaat is door deze stappen te volgen.

```output
Id              Name            State      HasMoreData     Location             Command
--              ----            -----      -----------     --------             -------
1               26932870-d3b... NotStarted False                                 Write-Host "A f...

```

```powershell
Set-Content $env:temp\test.txt "This is a test file"
```

```output
A file was created in the TEMP directory
```

## <a name="requirements"></a>Vereisten

In dit voorbeeld is Windows PowerShell 2.0 vereist.

## <a name="demonstrates"></a>Ziet u

In dit voorbeeld ziet u het volgende.

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>Over het schrijven van een cmdlet voor gebeurtenisregistratie

De cmdlet is afgeleid van de [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) klasse, die ondersteuning biedt voor parameters voor de `Register-*Event` cmdlets.
Cmdlets die zijn afgeleid van [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) moet alleen de specifieke parameters definiëren en overschrijven de `GetSourceObject` en `GetSourceObjectEventName` abstracte methoden.

## <a name="example"></a>Voorbeeld

In dit voorbeeld laat zien hoe u zich registreren voor gebeurtenissen die worden gegenereerd door [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](writing-a-windows-powershell-cmdlet.md)