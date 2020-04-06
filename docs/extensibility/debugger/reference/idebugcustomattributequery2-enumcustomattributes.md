---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b00ead2236a36c2fa12e1ad154b9f853aa2224d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732592"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Bu alana bağlı tüm özel öznitelikler için bir sayısallaştırıcı alır.

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
[çıkış] Özel öznitelikler listesini temsil eden bir [IEnumDebugCustomÖzler](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) nesnesi döndürür; aksi takdirde, özel öznitelikleri yoksa null bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, bu alanda özel öznitelikleri yoksa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür;

## <a name="remarks"></a>Açıklamalar
 Bir alanın birden çok özel özniteliği olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
