---
description: Dizinin bir öğesini alır.
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bc91b0576e98b5c27659ca9ae90ef37001e790c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627567"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Dizinin bir öğesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Parametreler
`dwIndex`\
[in] Öğe dizini.

`ppElement`\
[out] öğesini [temsil eden bir IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, dizi nesnesi çok boyutlu olsa bile bir dizi nesnesinin tüm öğelerini tek boyutlu bir dizi olarak görür. Örneğin, dizi ve 20 parametresine göre, bu yöntem öğesinden öğesini döndürür ve `myarray[3][2][6]` `dwIndex` 21 parametresi `myarray[1][1][2]` `dwIndex` öğesinden `myarray[1][1][3]` döndürür. Dizide toplam öğe sayısını belirlemek için [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
