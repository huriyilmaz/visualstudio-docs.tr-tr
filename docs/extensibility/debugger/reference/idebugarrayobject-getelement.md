---
description: Dizinin bir öğesini alır.
title: 'Ihata ayıklama Garrayobject:: GetElement | Microsoft Docs'
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
ms.openlocfilehash: 95d910d6ab039a544715a77b68d2f09b4a1478545ef64dd962db8cd5b372f707
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121323878"
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
