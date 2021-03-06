---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft direkt die **Test**-Methode einer DSC-Ressource auf.

<a name="syntax"></a>Syntax
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a>Parameter
----------

*ResourceType* \[in\]  
Der Name der aufzurufenden Ressource.

*ModuleName* \[in\]  
Der Name des Moduls, das die aufzurufende Ressource enthält.

*resourceProperty* \[in\]  
Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an. Verwenden Sie das Cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) zum Ermitteln von Ressourceneigenschaften und deren Typen.

*InDesiredState* \[out\]  
Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn sich der Zielknoten im gewünschten Zustand befindet.

## <a name="return-value"></a>Rückgabewert
------------

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## <a name="remarks"></a>Hinweise

Dies ist eine statische Methode.

## <a name="requirements"></a>Anforderungen
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Siehe auch


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)


 

 



