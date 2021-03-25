---
description: Belirtilen uzunluğa sahip bir dize nesnesi oluşturur.
title: 'IDebugFunctionObject2:: CreateStringObjectWithLength | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5314bf6d06f291ce7128b3b6ccebd520ef2eafca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072838"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Belirtilen uzunluğa sahip bir dize nesnesi oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`pcstrString`\
'ndaki Dize nesnesi için dize değeri.

`uiLength`\
'ndaki Dizenin bayt cinsinden uzunluğu.

`ppObject`\
dışı Yeni oluşturulan dize nesnesini temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
