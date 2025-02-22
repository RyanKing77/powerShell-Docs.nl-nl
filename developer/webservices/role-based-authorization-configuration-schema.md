---
title: Het Schema van autorisatie op basis van rollen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ba6d1d2-7055-4fef-b752-a5ae8b4eeb65
caps.latest.revision: 7
ms.openlocfilehash: 50a02e9a7522fc04b407329f513670215ad051cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080540"
---
# <a name="role-based-authorization-configuration-schema"></a>Configuratieschema voor autorisatie op basis van rollen

De [PswsRoleBasedPlugins](http://go.microsoft.com/fwlink/?LinkId=243041) voorbeeld maakt gebruik van XML-bestanden naar het verificatiebeleid configureren. De volgende XSD definieert het schema voor deze bestanden.

```
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
   <xs:element name="RbacConfiguration">
       <xs:complexType>
           <xs:all>
               <xs:element name="Groups">
                   <xs:complexType>
                       <xs:sequence>
                           <xs:element name="Group" type="GroupType" maxOccurs="unbounded"/>
                       </xs:sequence>
                   </xs:complexType>
       </xs:element>
               <xs:element name="Users">
                   <xs:complexType>
                       <xs:sequence>
                           <xs:element name="User" type="UserType" maxOccurs="unbounded"/>
                       </xs:sequence>
                   </xs:complexType>
       </xs:element>
           </xs:all>
       </xs:complexType>
   </xs:element>
   <xs:complexType name="GroupType">
       <xs:all>
           <xs:element name="Cmdlets" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Cmdlet" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
           <xs:element name="Scripts" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Script" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
           <xs:element name="Modules" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Module" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
       </xs:all>
       <xs:attribute name="Name" type="xs:string" use="required"/>
       <xs:attribute name="UserName" type="xs:string" use="optional"/>
       <xs:attribute name="Password" type="xs:string" use="optional"/>
       <xs:attribute name="DomainName" type="xs:string" use="optional"/>
       <xs:attribute name="MapIncomingUser" type="xs:boolean" use="optional"/>
   </xs:complexType>
   <xs:complexType name="UserType">
       <xs:all>
           <xs:element name="Quota" minOccurs="0">
               <xs:complexType>
                   <xs:attribute name="MaxConcurrentRequests" type="xs:string" use="optional"/>
                   <xs:attribute name="MaxRequestsPerTimeslot" type="xs:string" use="optional"/>
                   <xs:attribute name="Timeslot" type="xs:string" use="optional"/>
               </xs:complexType>
           </xs:element>
       </xs:all>
       <xs:attribute name="Name" type="xs:string" use="required"/>
       <xs:attribute name="DomainName" type="xs:string" use="optional"/>
       <xs:attribute name="AuthenticationType" type="xs:string" use="required"/>
       <xs:attribute name="GroupName" type="xs:string" use="required"/>
   </xs:complexType>
</xs:schema>
```