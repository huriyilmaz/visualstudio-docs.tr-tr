---
title: IDebugSourceServerModule | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719918"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
PDB dosyasında bulunan kaynak sunucu bilgilerini temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim hata ayıklama motorları tarafından uygulanır ve hata ayıklama aracı tarafından tüketilir.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugSourceServerModule`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Bir dizi kaynak sunucu bilgisini alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
