---
description: Bu hata ayıklama olayının özniteliklerini alır.
title: 'IDebugEvent2:: GetAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b41e3f50b73c16c9acb28a809b8c33b535370c47
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065859"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Bu hata ayıklama olayının özniteliklerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>Parametreler
`pdwAttrib`\
dışı [EventAttributes](../../../extensibility/debugger/reference/eventattributes.md) numaralandırmasındaki bayrakların birleşimi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi tüm olaylar için ortaktır. Bu yöntem, olay türünü açıklar; Örneğin, olay zaman uyumlu veya zaman uyumsuz olur ve bu bir durdurma olayıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
