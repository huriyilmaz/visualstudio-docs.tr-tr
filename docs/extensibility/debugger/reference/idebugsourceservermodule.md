---
description: PDB dosyasında bulunan kaynak sunucu bilgisini temsil eder.
title: Idebugsourceservermodule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74fa5f3aafea5f709777bbead81743c7c5aef358
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164649"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
PDB dosyasında bulunan kaynak sunucu bilgisini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, hata ayıklayıcı motorları tarafından uygulanır ve hata ayıklayıcı kullanıcı arabirimi tarafından kullanılır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugSourceServerModule` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Kaynak sunucu bilgileri dizisini alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
