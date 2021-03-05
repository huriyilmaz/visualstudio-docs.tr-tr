---
description: Bağlamını açıklayan CONTEXT_INFO yapısını alır.
title: 'IDebugMemoryContext2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2dfcd6063988f188b307b03febaeca988c8fb025
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165052"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
Bağlamını açıklayan [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) yapısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetInfo( 
   CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO*       pInfo
);
```

```csharp
int GetInfo(
   enum_CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO[]           pinfo
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
'ndaki [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) numaralandırmadaki, [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) yapısının hangi alanlarının doldurulacağını belirten bayrakların bir birleşimi.

`pInfo`\
[in, out] `CONTEXT_INFO` Doldurulmuş yapı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
