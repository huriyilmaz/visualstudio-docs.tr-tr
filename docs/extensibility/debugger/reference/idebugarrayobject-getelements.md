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
ms.openlocfilehash: 919a6a1ea6486cedec6ede700c9db0038a41d032a606bd5f80f13af8045a1f61
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403110"
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
