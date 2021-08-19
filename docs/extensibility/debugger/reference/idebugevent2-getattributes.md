---
description: Bu hata ayıklama olayı için öznitelikleri alır.
title: IDebugEvent2::GetAttributes | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba1b39a74497633e7a6cd1a2655b83550ae3a51c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111066"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Bu hata ayıklama olayı için öznitelikleri alır.

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
[out] [EVENTATTRIBUTES numaralamalarından gelen bayrakların](../../../extensibility/debugger/reference/eventattributes.md) birleşimi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugEvent2 arabirimi](../../../extensibility/debugger/reference/idebugevent2.md) tüm olaylar için ortaktır. Bu yöntem olay türünü açıklar; Örneğin, olay zaman uyumlu veya zaman uyumsuz ve bir durdurma olayıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
