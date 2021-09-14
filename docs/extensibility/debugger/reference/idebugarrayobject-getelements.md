---
description: Dizinin tüm öğelerinin bir Numaralandırıcı alır.
title: 'Ihata ayıklama Garrayobject:: GetElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72f3ec74ccb8eae959f3a12b9233bb329c0f72c3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627566"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Dizinin tüm öğelerinin bir Numaralandırıcı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı Tüm öğeler üzerinde numaralandırma yapılmasına izin veren bir [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Alternatif olarak, öğeleri içinde yinelemek için [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) ve [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) yöntemlerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
