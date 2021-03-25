---
description: Bu alana eklenen tüm özel öznitelikler için bir Numaralandırıcı alır.
title: 'IDebugCustomAttributeQuery2:: EnumCustomAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bcd11f3058de191a3b0a77f0316afb6140769fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077648"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Bu alana eklenen tüm özel öznitelikler için bir Numaralandırıcı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı Özel özniteliklerin listesini temsil eden bir [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) nesnesi döndürür; Aksi takdirde, özel öznitelik yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, bu alanda özel öznitelik yoksa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür;

## <a name="remarks"></a>Açıklamalar
 Bir alan birden çok özel özniteliğe sahip olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
