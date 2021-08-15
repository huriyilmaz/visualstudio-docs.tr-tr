---
description: Bu yöntem, işlev parametreleri oluşturmak için kullanılan bir IDebugFunctionObject nesnesi alır.
title: 'Idebugciltçi:: GetFunctionObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5fbd978bf415565c4fab016d08bbe50729124fb2683141acdcba611659bd07a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342602"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Bu yöntem, işlev parametreleri oluşturmak için kullanılan bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Parametreler
`ppFunction`\
dışı İşlev parametreleri oluşturmak için kullanılan [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
