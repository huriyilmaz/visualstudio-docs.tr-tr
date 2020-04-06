---
title: IDebugEvent2::GetAttributes | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffc3fc1b7988401611190fdf09e8041bf0dc5b1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729949"
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
[çıkış] [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) numaralandırmagelen bayrakların birleşimi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi tüm olaylariçin ortaktır. Bu yöntem, olay türünü açıklar; örneğin, olay senkron veya asynchronous ve bir durdurma olayıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
