---
description: Bir numaralandırma dizisinde belirtilen sayıda özel öznitelik alır.
title: 'IEnumDebugCustomAttributes:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79c8b6cf86413f1642d22d79e9c072794353499b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226884"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
Bir numaralandırma dizisinde belirtilen sayıda özel öznitelik alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next ( 
   ULONG      celt,
   CODE_PATH* rgelt,
   ULONG*     pceltFetched
);
```

```csharp
int Next(
   uint                        celt,
   out IDebugCustomAttribute[] rgelt,
   ref uint                    pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
'ndaki Alınacak öğe sayısı. Ayrıca, dizinin en büyük boyutunu belirtir `rgelt` .

`rgelt`\
dışı Doldurulacak bir [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) nesneleri dizisi.

`pceltFetched`\
dışı İçinde gerçekten döndürülen öğelerin sayısını döndürür `rgelt` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`İstenen sayıda öğeden daha az döndürülüp döndürülmeyeceğini döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
