---
title: 'Ihata ayıklama Garrayobject:: GetElement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 61085ee3e8323b2aa297473cffeebb998fc5c11b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870187"
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
'ndaki Öğe dizini.

`ppElement`\
dışı Öğesini temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, dizi nesnesi çok boyutlu olsa bile, dizi nesnesinin tüm öğelerini tek boyutlu bir dizi olarak görür. Örneğin, array `myarray[3][2][6]` ve `dwIndex` 20 parametresi verildiğinde, bu yöntem öğesinden öğesini döndürür `myarray[1][1][2]` ve bir `dwIndex` 21 parametresi öğesinden öğesini döndürür `myarray[1][1][3]` . Dizideki toplam öğe sayısını öğrenmek için [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metodunu kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
